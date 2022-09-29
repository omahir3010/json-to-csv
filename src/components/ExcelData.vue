
<template>
  <div class="result-table">
    <table class="table table-bordered">
      <thead>
        <tr>
          <th scope="col">ID</th>
          <th scope="col">Age</th>
          <th scope="col">First-Name</th>
          <th scope="col">Last-Name</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="i in items" :key="i.id" scope="row">
          <td>{{ i.id }}</td>
          <td>{{ i.age }}</td>
          <td>{{ i.first_name }}</td>
          <td>{{ i.last_name }}</td>
        </tr>
      </tbody>
    </table>

    <button type="button" class="btn btn-success" @click="downloadFile()">
      Download
    </button>
  </div>
</template>

<script>

import exportFromJSON from "export-from-json";

export default {
  data() {
    return {
      items: [
        { id: 1, age: 21, first_name: "Om", last_name: "Ahir" },
        { id: 2, age: 11, first_name: "Yash", last_name: "Patil" },
        { id: 3, age: 40, first_name: "Krishna", last_name: "Patel" },
        { id: 4, age: 21, first_name: "Yash", last_name: "Shaw" },
        { id: 5, age: 89, first_name: "King", last_name: "Yusuf" },
        { id: 6, age: 38, first_name: "Patil", last_name: "Umer" },
      ],
    };
  },

  methods: {


    downloadFile() {
      const data = this.items;
      const fileName = "myData";
      const exportType = exportFromJSON.types.csv;

      if (data) exportFromJSON({ data, fileName, exportType });
    },
  },
};
</script>

<style scoped>
.result-table {
    margin-top: 40px;
  /* width: 50%; */
  text-align: center;
}
</style>