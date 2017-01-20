<template>
  <div class="text">
    <h1>{{ msg }}</h1>
    <!--<pre v-for="commit in commits">{{commit.sha.slice(0, 70)}}   {{commit.commit.author.date}}   {{commit.commit.author.email}}   {{commit.commit.author.name}}</pre>-->
    <pre v-for="commit in commits">{{commit.sha.slice(0, 7)}}   {{commit.commit.author.date}}</pre>
  </div>
</template>

<script>
  import $ from 'jquery'
  
  export default {
    name: 'hello',
    data () {
      var _this = this
      $.get('https://api.github.com/repos/yjman/vue-demo/commits')
      .done(function (data) {
        _this.commits = data
      })
      return {
        msg: 'Welcome to Your Vue.js App, commits',
        commits: {}
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  h1,
  h2 {
    font-weight: normal;
  }
</style>