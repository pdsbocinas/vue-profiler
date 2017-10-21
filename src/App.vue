<template>
  <div class="app">
    <ul>
      <li v-for="item of data">
        <div class="">
          <p>{{ item.title }}</p>
          <p>{{ item.description }}</p>
        </div>
        <div class="">
          <a href="#">{{ item.option.one }}</a>
          <a href="#">{{ item.option.two }}</a>
          <a href="#">{{ item.option.three }}</a>
          <a href="#">{{ item.option.four }}</a>
          <a href="#">{{ item.option.five }}</a>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: 'app',
  data() {
    return {
      errors: [],
      data: []
    }
  },
  created () {
    axios.get(`../json/data.json`)
    .then(response => {
      this.data = response.data
    })
    .catch(e => {
      this.errors.push(e)
    })
  }
}
</script>

<style lang="scss" scoped>
.app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

h1,
h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: flex;
}

a {
  color: #42b983;
}
</style>
