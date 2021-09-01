<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <div>{{ message }}</div>
    <div>
      <button @click="invokeApi">Invoke API</button>
    </div>
    <div>
      <a href="/login">Login</a>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref, computed } from 'vue';
import axios from 'axios';

export default defineComponent({
  name: 'Home',
  setup: () => {
    const name = ref('');
    const message = computed(() => name.value ? `こんにちは ${name.value} さん` : 'ログインしてボタンを押してください。');

    return {
      name,
      message,
    };
  },
  methods: {
    async invokeApi() {
      try {
        this.name = await axios.get('/api/Function1');
      } catch (e) {
        this.name = '';
        alert('エラー');
      }
    }
  }
});
</script>
