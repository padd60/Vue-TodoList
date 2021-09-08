<template>
  <div id="app">
    <TodoHeader></TodoHeader>
    <!-- v-on:하위 컴포넌트 이벤트명 = '상위 컴포넌트 이벤트명' -->
    <TodoInput v-on:addTodo="addTodo"></TodoInput>
    <!-- v-bind:propsdata='부모 data 변수명' -->
    <TodoList
      v-bind:propsdata="todoItems"
      v-on:removeTodo="removeTodo"
    ></TodoList>
    <TodoFooter v-on:clearTodo="clearTodo"></TodoFooter>
  </div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue';
import TodoInput from './components/TodoInput.vue';
import TodoList from './components/TodoList.vue';
import TodoFooter from './components/TodoFooter.vue';

export default {
  name: 'App',
  data() {
    return {
      todoItems: [],
    };
  },
  components: {
    TodoHeader: TodoHeader,
    TodoInput: TodoInput,
    TodoList: TodoList,
    TodoFooter: TodoFooter,
  },
  methods: {
    addTodo: function(value) {
      this.todoItems.push(value);
      console.log(this.todoItems);
    },
    removeTodo: function(idx) {
      this.todoItems.splice(idx, 1);
    },
    clearTodo: function() {
      this.todoItems = [];
    },
  },
};
</script>

<style>
body {
  text-align: center;
  background-color: #f6f6f8;
}

input {
  border-style: groove;
  width: 200px;
}

button {
  border-style: groove;
}

.shadow {
  box-shadow: 5px 10px 10px rgba(0, 0, 0, 0.03);
}
</style>
