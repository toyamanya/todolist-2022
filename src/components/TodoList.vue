<script setup>
import { ref } from "vue";

const todos = ref([
  { name: "早く起きる", done: true },
  { name: "プログラミング", done: false },
]);
const newTodoName = ref("");
const newTodoChecked = ref(false);

const addTodo = () => {
  todos.value.push({ name: newTodoName.value, done: newTodoChecked.value });
};
</script>

<template>
  <div>
    <div>TodoList</div>
    <div>まだ終わってないタスク</div>
    <div v-for="todo in todos" :key="todo.name">
      <label v-if="!todo.done">
        <input v-model="todo.done" type="checkbox" />
        {{ todo.name }}
      </label>
    </div>
    <div>終わったタスク</div>
    <div v-for="todo in todos" :key="todo.name">
      <label v-if="todo.done">
        <input v-model="todo.done" type="checkbox" />
        {{ todo.name }}
      </label>
    </div>
  </div>
  <div>
    <label>
      タスク
      <input v-model="newTodoName" type="text" />
    </label>
  </div>
  <button @click="addTodo">add</button>
</template>
