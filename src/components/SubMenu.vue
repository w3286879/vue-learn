<template functional>
  <a-sub-menu :key="props.menuInfo.key">
    <span slot="title">
      <a-icon type="mail" /><span>{{ props.menuInfo.title }}</span>
    </span>
    <template v-for="item in props.menuInfo.children">
      <a-menu-item v-if="!item.children" :key="item.key">
        <a-icon type="pie-chart" />
        <span>{{ item.title }}</span>
      </a-menu-item>
      <sub-menu v-else :key="item.key" :menu-info="item" />
    </template>
  </a-sub-menu>
</template>
<script>
// import Vue from "vue"
import { Menu, Icon } from "ant-design-vue";
// Vue.use(Menu)
export default {
  props: ['menuInfo'],
  components: {
    AIcon: Icon,
    ASubMenu: Menu.SubMenu,
    AMenuItem: Menu.Item
  },
};
</script>