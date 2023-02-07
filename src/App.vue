<script setup>
import { ref } from "vue"
import AppHeader from "./components/AppHeader.vue"
import TodoList from "./components/TodoList.vue"

const newTodo = ref("")
const todos = ref([])

const addTodo = () => {
  todos.value.push(newTodo.value)
  newTodo.value = ""
}

const removeTodo = (index) => {
  todos.value.splice(index, 1)
}
</script>

<template>
  <AppHeader color="blue">My Todos</AppHeader>
  <div>
    <input type="text" size="30" v-model="newTodo" />
  </div>
  <div>
    <button @click="addTodo()">追加</button>
  </div>
  <div>
    <TodoList :todos="todos" @removeTodo="removeTodo" />
  </div>
</template>
