<template>
  <div class="home" ref="home" @mouseenter="mouseEnter" @mouseleave="mouseLeave">
    <div class="content" ref="view">
      <p v-for="(item, index) in arr" :key="index" ref="content">{{ item }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "Home",
  data() {
    return {
      arr: [
        "如果有遗憾，那也是遗憾没有再爱你多一点。",
        "从爱生忧患，从爱生怖畏；离爱无忧患，何处有怖畏？是故莫爱着，爱别离为苦。若无爱与憎，彼即无羁缚。我只惦记着离爱可以无羁缚，可恨呢？那是否是更大的羁缚？遗憾呢？那是否会让心日夜不得宁静？",
        "我想将对你的思念，寄予散落的星辰；但愿星光照进你的窗前，伴你好眠。",
        "一个人在戏里戏外肯定是不一样的，这一点不可怕，最可怕的是，你分不清自己到底是在戏里，还是戏外。",
        "喜欢一个人是种感觉，不喜欢一个人却是事实。事实容易解释，感觉却难以言喻。我们每一天努力地忙碌，用力地生活，却总在不知不觉间遗失了什么。有时候，我们需要的，只是一颗静下来的心。",
        "缘来则聚，缘去则散，缘起则生，缘落则灭。",
        "发号施令爱情中是行不通的",
        "很多时的争吵，都是与亲近的人，更甚是与自己。伤害最深不过还是在乎之人，还伤了自己。与其和自己过不去，倒不如学会暂缓当下，寻觅方向。遇窄路，心宽走，遇险时，慢慢行。",
      ],
      time: null,
      length: null,
    };
  },
  methods: {
    scrollInterval() {
      this.$refs.home.scrollTop += 1;
      if (this.$refs.home.scrollTop > 0 && this.arr.length === this.length) {
        this.arr.push(this.arr[0]);
      } else if (
        this.$refs.home.scrollTop >= this.$refs.content[0].clientHeight + 5
      ) {
        this.$refs.home.scrollTop = 0;
        this.arr.splice(0, 1);
      }
    },
    mouseEnter(){
      clearInterval(this.time)
    },
    mouseLeave(){
      this.time = setInterval(this.scrollInterval,50)
    }
  },
  mounted() {
    this.length = this.arr.length;
    let viewHeight = this.$refs.view.clientHeight;
    let homeHeight = this.$refs.home.clientHeight;
    if (viewHeight > homeHeight) {
      this.time = setInterval(this.scrollInterval, 50);
    }
    // this.time = setInterval(()=>{
    //   this.$refs.home.scrollTop += 1
    // },100)
  },
};
</script>

<style lang="scss" scoped>
.home {
  width: 400px;
  height: 200px;
  border: 1px solid #000;
  overflow: hidden;
  p {
    margin: 0 0 5px 0;
    font-family: Georgia, serif;
    font-size: 12px;
    // font-style: oblique;
  }
}
</style>
