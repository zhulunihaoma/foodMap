<!-- 使用 type="home" 属性设置首页，其他页面不需要设置，默认为page；推荐使用json5，更强大，且允许注释 -->
<route lang="json5" type="home">
{
  style: {
    navigationStyle: 'custom',
    navigationBarTitleText: '首页',
  },
}
</route>
<template>
  <view>
    <view class="page-body">
      <view class="page-section page-section-gap">
        <map style="width: 100%; height: 100vh;" :latitude="mapData.latitude" :longitude="mapData.longitude" :markers="mapData.covers">
        </map>
      </view>
    </view>
  </view>
</template>

<script lang="ts" setup>
import { TestEnum } from '@/typings'
import PLATFORM from '@/utils/platform'

defineOptions({
  name: 'Home',
})

// 获取屏幕边界到安全区域距离
const { safeAreaInsets } = uni.getSystemInfoSync()
const mapData = reactive(
  {
    id: 0, // 使用 marker点  击事件 需要填写id
    title: 'map',
    latitude: 32.058300,
    longitude: 118.796000,
    covers: [{
      id:1,
      latitude: 32.058300,
      longitude: 118.796000,
      iconPath: '../../../../../static/images/dys.jpg'
    }, {
      id:2,
      latitude: 31.058300,
       longitude: 118.796000,
      iconPath: '@static/images/wll.jpg'
    }]
  }
)
// 测试 uni API 自动引入
onLoad(() => {
  console.log(TestEnum.A)
})

</script>

<style>
.main-title-color {
  color: #d14328;
}
</style>
