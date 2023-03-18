<script setup>
import { ref, computed } from "vue";

const name = "Orlando";

const counter = ref(0);
const listNumber = ref([]);

const increment = () => {
  counter.value++;
};

const decrement = () => {
  counter.value--;
};

const reset = () => {
  counter.value = 0;
};

const add = () => {
  listNumber.value.push(counter.value);
};

const classCounter = computed(() => {
  if (counter.value === 0) {
    return "neutral";
  }
  if (counter.value > 0) {
    return "green";
  }
  if (counter.value < 0) {
    return "red";
  }
});

const isDisabledAdd = computed(() => {
  const numSearch = listNumber.value.find((num) => num === counter.value);
  return numSearch || numSearch === 0;
});
</script>

<template>
  <div class="container text-center mt-3">
    <h1>Hola {{ name }}!</h1>
    <h1>Counter</h1>
    <h2 :class="classCounter">{{ counter }}</h2>
    <div class="btn-group">
      <button @click="increment" class="btn btn-success">Increment</button>
      <button @click="decrement" class="btn btn-danger">Decrement</button>
      <button @click="reset" class="btn btn-secondary">Reset</button>
      <button @click="add" :disabled="isDisabledAdd" class="btn btn-primary">Add</button>
    </div>
    <ul class="list-group mt-4">
      <li class="list-group-item" v-for="(item, index) in listNumber" :key="index">{{ item }}</li>
    </ul>
  </div>
</template>

<style>
.green {
  color: green;
}
.red {
  color: red;
}
.neutral {
  color: blue;
}
p {
  text-align: center;
}
</style>

<!--    <li v-for="(value, prop, index) in objFrutas" :key="index">
      {{ index }} - {{ prop }} : {{ value }}
    </li> -->
