<template>
  <div
    class="flex flex-col relative h-screen w-full py-[60px] bg-gray-200 items-center"
  >
    <h1 class="mb-[20px] text-5xl font-bold">TO-DO LIST</h1>
    <div class="flex flex-row relative">
      <div>
        <input
          v-model="inputField"
          type="text"
          placeholder="enter tasks"
          class="border border-2xl w-[400px] h-[60px] px-[10px] rounded-[10px] placeholder: font-normal placeholder: text-sm outline-0 text-gray-600"
        />
      </div>
      <button
        @click="addTask()"
        class="bg-black text-white absolute left-[300px] w-[100px] h-[60px] rounded-[10px]"
      >
        add
      </button>
    </div>
    <div class="flex flex-row">
      <div class="flex flex-col justify-center">
        <div
          v-for="toDo in toDos"
          class="mt-[20px] flex justify-between border rounded-[10px] h-[50px] w-[400px] bg-white"
        >
          <p
            class="text-black font-mono text-xl flex items-center text-center justify-center ml-[20px]"
          >
            {{ toDo }}
          </p>

          <button
            @click="removeTask()"
            class="h-[50px] w-[100px] bg-red-700 rounded-[10px] text-white"
          >
            delete
          </button>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "Test",
  created() {},
  data() {
    return {
      inputField: "",
      toDos: [],
    };
  },
  props: {},
  methods: {
    addTask() {
      // function to add a task using push method to add what is being typed in the inputField as tasks
      if (this.inputField !== "") {
        this.toDos.push(this.inputField);
        this.inputField = "";
      }
    },
    removeTask() {
      // function to delete a task using splice method
      this.toDos.splice(0, 1);
    },
    saveTask() {
      // converting the todos to a string and saving the todos in localstorage
      localStorage.setItem("data", JSON.stringify(this.toDos));
    },
  },
};
</script>

<style lang="scss" scoped></style>
