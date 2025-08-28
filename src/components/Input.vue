<template>
  <div>
    <label v-if="label" class="block text-gray-700 font-medium mb-1">
      {{ label }}
    </label>
    <input
      :type="type"
      :value="modelValue"
      :placeholder="placeholder"
      @input="handleInput"
      class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring focus:ring-blue-200"
    />
    <p v-if="error" class="text-red-500 text-sm mt-1">
      {{ error }}
    </p>
  </div>
</template>

<script setup>
const props = defineProps({
  modelValue: {
    type: [String, Number],
    default: '',
  },
  label: {
    type: String,
    default: '',
  },
  type: {
    type: String,
    default: 'text',
  },
  placeholder: {
    type: String,
    default: '',
  },
  error: {
    type: String,
    default: '',
  },
});

const emit = defineEmits(['update:modelValue']);

const handleInput = (event) => {
  emit('update:modelValue', event.target.value);
};
</script>