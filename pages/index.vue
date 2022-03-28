<template>
  <div> {{ data }}</div>
</template>

<script>
import axios from 'axios';
export default {
  asyncData({app}){

    return {

    }
  },
  data() {
    return {
      data: null
    }
  },
  methods: {
    async setData() {
      this.data = await fetch();
    }
  },
  components: {
  },
  created () {
    this.setData();
  },

}

async function fetch(){
  const payLoad = {
    title :'frozen',
    type: 'movie',
    year : '2020',
    page: 1
  }
  console.log(process.client)
  const url = process.client
    ? '/api/test'
    : `${process.env.CLIENT_URL}/api/test`
  return await axios.post(url, payLoad)
}
</script>
