<template>
  <div class="banner-warp">
    <!-- <swiper :options="swiperOption">
      <swiper-slide v-for="(item) in banners" :key="item.goods">
        <router-link
          :to="'/app/home/productDetail/' + item.goods"
          target="_blank"
        >
          <img src="../../assets/banner/banner1.jpg" alt=""
        /></router-link>
      </swiper-slide>
      <div class="swiper-pagination" slot="pagination"></div>
    </swiper> -->
    <img src="../../assets/banner/banner1.jpg" alt="" />
  </div>
</template>

<script>
import { swiper, swiperSlide } from 'vue-awesome-swiper';

import { bannerGoods } from '../../api/api';

export default {
  name: 'banner',
  components: {
    swiper,
    swiperSlide,
  },
  data() {
    return {
      swiperOption: {
        initialSlide: 1,
        loop: true,
        pagination: '.swiper-pagination',
        paginationClickable: true,
        autoplay: 5000,
        autoplayDisableOnInteraction: true,
      },
      banners: [],
    };
  },
  methods: {
    getBanner() {
      bannerGoods()
        .then((response) => {
          console.log(response);
          //跳转到首页页response.body面
          this.banners = response.data;
        })
        .catch(function (error) {
          console.log(error);
        });
    },
  },
  created() {
    this.getBanner();
  },
  mounted() {},
};
</script>

<style>
.banner-warp {
  height: 300px;
}
</style>
