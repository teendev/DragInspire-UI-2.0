<template>
  <v-toolbar fixed class="light-blue darken-4" dark>
    <v-toolbar-title class="mr-4">
      <span class="home" @click="navigateTo({name: 'root'})">
        DragInspire
      </span>
    </v-toolbar-title>
    <v-toolbar-items>
      <v-btn v-if="$store.state.isUserLoggedIn" flat dark @click="navigateTo({name: 'projects'})">
        Projects
      </v-btn>
      <v-btn v-if="$store.state.isUserLoggedIn" flat dark @click="navigateTo({name: 'profile'})">
        Update Your Profile
      </v-btn>
    </v-toolbar-items>
    <v-spacer></v-spacer>
    <v-toolbar-items>
      <v-btn v-if="!$store.state.isUserLoggedIn" flat dark @click="navigateTo({name: 'register'})">
        Sign Up
      </v-btn>
      <v-btn v-if="!$store.state.isUserLoggedIn" flat dark @click="navigateTo({name: 'login'})">
        Login
      </v-btn>
      <!--This will only be an option when user is logged in thus no !-->
      <v-btn v-if="$store.state.isUserLoggedIn" flat dark @click="logout">
        Logout
      </v-btn>
    </v-toolbar-items>
  </v-toolbar>
</template>

<script>
export default {
  methods: {
    navigateTo (route) {
      this.$router.push(route)
    },
    logout () {
      this.$store.dispatch('setToken', null)
      this.$store.dispatch('setUser', null)
      // redirect to homepage
      this.$router.push({
        name: 'root'
      })
    }
  }
}
</script>

<style>
.home {
  cursor: pointer;
}
.home:hover {
  color: #FDD835
}
</style>
