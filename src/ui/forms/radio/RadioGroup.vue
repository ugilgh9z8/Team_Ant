<script setup lang="ts">
import { reactive, provide, watch, type PropType } from "vue";
import type { RadioGroupState } from "./state";

const props = defineProps({
  modelValue: {
    type: String as PropType<string | null>,
    required: true,
  },
});

const state = reactive<RadioGroupState>({
  value: props.modelValue,
});

provide("radioProvider", state);

const emit = defineEmits(["update:modelValue"]);

watch(state, () => {
  emit("update:modelValue", state.value);
});
</script>

<template>
  <div class="radio-group">
    <slot></slot>
  </div>
</template>

<style scoped>
.radio-group {
  display: flex;
}
</style>
