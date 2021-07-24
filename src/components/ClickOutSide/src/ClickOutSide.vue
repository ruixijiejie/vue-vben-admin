<template>
  <div ref="target">
    <slot></slot>
  </div>
</template>
<script lang="ts">
  import { defineComponent, ref, onMounted } from 'vue';
  import { onClickOutside } from '@vueuse/core';
  export default defineComponent({
    name: 'ClickOutSide',
    emits: ['mounted', 'clickOutside'],
    setup(_, { emit }) {
      const target = ref<ElRef>(null);

      onClickOutside(target, () => {
        emit('clickOutside');
      });

      onMounted(() => {
        emit('mounted');
      });

      return { target };
    },
  });
</script>
