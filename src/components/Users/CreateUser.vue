<template>
  <div>
    <h1>Create Users</h1>
    <form v-on:submit.prevent="createUser">
      <p>title: <input type="text" v-model="user.title" /></p>
      <p>author: <input type="text" v-model="user.author" /></p>
      <p>total_page: <input type="text" v-model="user.total_page" /></p>
      <p>publisher: <input type="text" v-model="user.publisher" /></p>
      <p>category: <input type="text" v-model="user.category" /></p>
      <p>price: <input type="text" v-model="user.price" /></p>
      <p><button type="submit">create user</button></p>
    </form>
    <hr />
    <div>
      <p>name: {{ user.name }}</p>
      <p>lastname: {{ user.lastname }}</p>
      <p>email: {{ user.email }}</p>
      <p>password: {{ user.password }}</p>
    </div>
  </div>
</template>
<script>
import UsersService from "@/services/UserService";

export default {
  data() {
    return {
      user: {
        name: "",
        lastname: "",
        email: "",
        password: "",
        status: "active"
      }
    };
  },
  methods: {
    async createUser() {
      try {
        await UsersService.post(this.user);
        this.$router.push({
          name: "users"
        });
      } catch (err) {
        console.log(err);
      }
    }
  }
};
</script>
<style scoped></style>
