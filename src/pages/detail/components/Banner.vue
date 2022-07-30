<template>
  <div>
    <div class="banner">
      <img class="banner-img"  @click="handleBannerClick" v-show="!showGallery" :src="bannerImg" />
      <div class="banner-info">
        <div class="banner-title">{{this.sightName}}</div>
        <div class="banner-number">
          <span class="iconfont">&#xe645;</span>
          {{this.bannerImgs.length}}
          </div>
      </div>
    </div>
    <fade-animation>
      <common-gallary
        :imgs="bannerImgs"
        v-show="showGallery"
        @close="handleGalleryClose">
      </common-gallary>
    </fade-animation>
  </div>
</template>
<script>
import CommonGallary from 'common/gallary/Gallary.vue'
import FadeAnimation from 'common/fade/FadeAnimation.vue'
export default {
  name: 'DetailBanner',
  props: {
    sightName: String,
    bannerImg: String,
    bannerImgs: Array
  },
  data () {
    return {
      showGallery: false
    }
  },
  methods: {
    handleBannerClick () {
      this.showGallery = true
    },
    handleGalleryClose () {
      this.showGallery = false
    }
  },
  components: {
    CommonGallary,
    FadeAnimation
  }
}
</script>
<style lang="stylus" scoped>
  .banner
    position: relative
    overflow: hidden
    height: 0
    width: 100%
    padding-bottom: 55%
    .banner-img
      width: 100%
    .banner-info
      position: absolute
      color: #ffffff
      left: 0
      right: 0
      bottom: 0
      line-height: .6rem
      background-image: linear-gradient(top,rgba(0,0,0,0),rgba(0,0,0,0.8))
      display: flex
      .banner-title
        font-size: .32rem
        padding: 0 .2rem
        flex: 1
      .banner-number
        margin: .14rem
        padding: 0 .3rem
        line-height: .4rem
        height: .32rem
        font-size: .24rem
        border-radius: .2rem
        background: rgba(0, 0, 0, 8)
        .iconfont
          font-size: .24rem
          padding: .02rem
</style>
