<template>
  <div id="app">
    <Header />
    <AddTodo v-on:add-todo="addTodo" />
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>
import Todos from "./components/Todos.vue";
import Header from "./components/layout/Header.vue";
import AddTodo from "./components/AddTodo.vue";

export default {
  name: "app",
  components: {
    Header,
    AddTodo,
    Todos
  },
  data() {
    return {
      todos: [
        { id: 1, title: "Todo one", completed: false },
        { id: 2, title: "Todo two", completed: false },
        { id: 3, title: "Todo three", completed: false },
        { id: 4, title: "Todo four", completed: false }
      ]
    };
  },
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id);
    },
    addTodo(newTodo) {
      this.todos.push(newTodo);
    }
  }
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}
.btn {
  background: #555;
  border: none;
  color: #ffffff;
}
</style>
