<template>
  <form v-on:submit.prevent="submitForm">
    <div>
      <label for="username">id: </label>
      <input id="username" type="text" v-model="username"/>
    </div>
    <div>
      <label for="pwd">pw: </label>
      <input id="pwd" type="password" v-model="pwd"/>
    </div>
    <button type="submit">login</button>
  </form>
</template>

<script>
import axios from 'axios';

export default {

  data: function() {
    return {
      username: '',
      pwd: ''
    }
  },
  methods: {
    submitForm: function() {
      console.log(this.username, this.pwd);

      var url = "https://jsonplaceholder.typicode.com/users";
      var data = {
        username: this.username,
        password: this.pwd
      }

      axios.post(url, data)
        .then(function(response) {
          console.log(response);
        })
        .catch(function(error) {
          console.log(error);
        });
    }
  }
}
</script>

<style>

</style>