<template>
  <div>
    <h2> Tous les utilisateurs </h2>
    <ul>
      <li v-for="user in users" :key="user.firstname">
        {{ user.firstname }} {{ user.lastname }}
      </li>

    </ul>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data () {
    return {
      users: [],
    }
  },
  methods: {
    async fetchData () {
      const token = localStorage.getItem('vuejs_token')
      const res = axios.get('http://localhost:3000/users', {
        headers: {
          Authorization: `Bearer ${token}`
        }
      })
      this.users = res.data
    }
  },
  mounted () {
    this.fetchData()
  }
}
</script>
