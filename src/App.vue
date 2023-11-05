<template>
  <div class="todo-container">
    <div class="todo-wrap">
      <Header />
      <List :todos="todos" />
      <Footer />
    </div>
  </div>
</template>

<script lang="ts">
  import { defineComponent, reactive, toRefs } from 'vue'
  import Header from './components/Header.vue'
  import List from './components/List.vue'
  import Footer from './components/Footer.vue'

  import { Todo } from './types/todo'


  export default defineComponent ({
    name: 'App',
    components: {
      Header,
      List,
      Footer
    },

    setup() {
    const state = reactive<{todos: Todo []}>({
      todos: [
        { id: 1, title: "吃飯", isCompleted: false },
        { id: 2, title: "散步", isCompleted: true },
        { id: 3, title: "看電影", isCompleted: false },
      ]
    })
    return {
      ...toRefs(state)
    }
  }

  })
</script>

<style>
  /*app*/
  .todo-container {
    width: 600px;
    margin: 0 auto;
  }
  .todo-container .todo-wrap {
    padding: 10px;
    border: 1px solid #ddd;
    border-radius: 5px;
  }
</style>

