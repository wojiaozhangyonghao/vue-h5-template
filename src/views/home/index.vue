<!--
 * @Author: zyh
 * @Date: 2021-03-04 09:10:49
 * @LastEditors: zyh
 * @LastEditTime: 2021-04-01 17:58:35
 * @Description: file content
-->
<!-- home -->
<template>
  <div class="app-container">
    <div class="warpper">
      <div class="demo-img">
        <img src="../../assets/logo1.jpg" />
      </div>
      <!-- <h1 class="demo-home__title">
        </h1> -->
      <!-- <h2 class="demo-home__desc">
        A vue h5 template with Vant UI
      </h2>  -->
    </div>
    <div  :class="fixed2 ? 'monitor' : 'grey'">
        <van-search
          v-model="value" 
          shape="round"
          background="#4fc08d"
          placeholder="请输入搜索关键词"
        />
        <!-- {{fixed}} -->
    </div>
    <van-cell icon="success" v-for="item in list" :key="item" :title="item" />
    <van-tabbar fixed v-model="active" @change="onChange">
      <van-tabbar-item icon="home-o">首页</van-tabbar-item>
      <van-tabbar-item icon="good-job-o">我的</van-tabbar-item>
    </van-tabbar>
  </div>
</template>

<script>

// window.addEventListener('scroll',function(){
//     var scrollTop = document.documentElement.scrollTop || document.body.scrollTop;
//   console.log(scrollTop,'scrollTop')
//   if (scrollTop>300){
//     this.fixed = true
//   }
// })
// 请求接口
import { getUserInfo } from '@/api/user.js'
export default {
  components: {},

  data() {
    return {
      fixed2:false,
      value:'',
      active: 0,
      list: [
        'Vue-cli4',
        'VantUI组件按需加载',
        'Sass',
        'Webpack 4',
        'Vue-router',
        'Vuex',
        'Axios封装',
        'rem适配方案',
        '多环境配置',
        '生产环境cdn优化首屏加速',
        'babel低版本浏览器兼容',
        'Eslint+Pettier统一开发规范46',
        'Eslint+Pettier统一开发规范8',
          'Eslint+Pettier统一开发规范5',
        'Eslint+Pettier统一开发规范6',
        'Eslint+Pettier统一开发规范4',
      ]
    }
  },

  computed: {},

  mounted() {
     window.addEventListener('scroll', this.handleScroll)
    this.initData()
  },

  methods: {
     handleScroll () {
      // let scrollY = document.documentElement.scrollTop
      var scrollTop = window.pageYOffset || document.documentElement.scrollTop || document.body.scrollTop;
       console.log(scrollTop,'scrollTop')
      if (scrollTop > 300) {
        this.fixed2 = true
           }
        else {
       this.fixed2 = false
    }
  },
    // 请求数据案例
    initData() {
      // 请求接口数据，仅作为展示，需要配置src->config下环境文件
      const params = {user:'sunnie'}
      getUserInfo()
        .then(() => { })
        .catch(() => { })
    },
    onChange(index) {
      if (index === 1){
        console.log('ppp')
      } 
      // window.location.href = 'https://github.com/sunnie1992/vue-h5-template'
    }
  }
}
</script>
<style lang="scss" scoped>
.app-container {
  .monitor{
    width: 100%;
    position: fixed;
    top: 0px;
    z-index: 999999;
  }
  .grey{
    width: 100%;
  }
  .warpper {
    .demo-img{
      width: 100%;
      height:300px;
      img{
        width: 100%;
        height: 100%;
      }
    }
    padding: 12px;
    .demo-home__title {
      margin: 0 0 6px;
      font-size: 32px;
      .demo-home__title img,
      .demo-home__title span {
        display: inline-block;
        vertical-align: middle;
      }
      img {
        width: 32px;
      }
      span {
        margin-left: 16px;
        font-weight: 500;
      }
    }
    .demo-home__desc {
      margin: 0 0 20px;
      color: rgba(69, 90, 100, 0.6);
      font-size: 14px;
    }
  }
}
</style>
