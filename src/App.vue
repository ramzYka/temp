<template>
  <div id="app">
    <input type="text" v-model="name" placeholder="Name">
    <input type="password" v-model="passwrd" placeholder="Password">
    <input type="email" v-model="email" placeholder="Email">
    <p className="error">{{ error }}</p>
    
    <button @click="sendData()">To send</button>

    <div v-if="users.length == 0">Нет зареганых пользователей</div>
    
    <div v-for="el,index in users" :key="index">
      {{ el.name }}
      {{ el.password }}
      {{ el.mail }}
    </div>

  </div>
</template>

<script>

  import User from "./components/"

  export default {
    data() {
      return {
        name: '',
        passwrd: '',
        email: '',
        error: '',
        users: []
      }
    },

    methods: {
      sendData() {

        if(this.name == '') {
          this.error = "Вы ничего не ввели"
          return;
        } else if(this.passwrd == '') {
          this.error = "Вы ничего не ввели"
          return;
        } else if(this.email == '') {
          this.error = "Вы ничего не ввели"
          return
        }

        this.error = ''

        this.users.push({
          name: this.name,
          password: this.passwrd,
          mail: this.email,
        })
      }
    }
  }

</script>

<style scoped>

  h3 {
    font-weight: lighter;
  }

  p {
    color: red
  }
</style>
