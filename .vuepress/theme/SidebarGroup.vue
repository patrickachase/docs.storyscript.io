<template>
  <div
    class="sidebar-group"
    :class="{ first, collapsable }"
  >
    <p
      class="sidebar-heading"
      :class="{ open }"
      @click="$emit('toggle')"
    >
      <span>{{ item.title }}</span>
      <span
        class="arrow"
        v-if="collapsable"
        :class="open ? 'down' : 'right'"
      ></span>
    </p>
    <ul
      class="sidebar-group-items"
      ref="items"
      v-if="open || !collapsable"
    >
      <li
        v-for="child in item.children"
        class="sub-link"
      >
        <SidebarLink :item="child" />
      </li>
    </ul>
  </div>
</template>

<script>
import SidebarLink from './SidebarLink.vue'

export default {
  name: 'SidebarGroup',
  props: ['item', 'first', 'open', 'collapsable'],
  components: { SidebarLink }
}
</script>
