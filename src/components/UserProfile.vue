<template>

  <div class = "user-profile">
    <div class = "user-profile__user-panel">
      <h1 class = "user-profile__username">
        @{{user.username}}
      </h1>
      <div class="user-profile__follower-count">
        <strong>Followers: </strong> {{followers }}
      </div>
    </div>
  </div>


  <!-- <div id="app">
    @{{user.username}} - {{ fullName }}
    <br>
    <strong>Followers: </strong> {{followers }}
    <br>


    <button v-on:click="followUser()">Follow</button>
    <br>
    <button v-on:click="reSet()">Reset</button>
    <br>
    <button v-on:click="unFollowUser()">UnFollow</button>
    <br>
    <strong>Disclaimer: </strong> {{dat}}
  </div> -->

</template>

<script>


export default {
  name: 'App',
  data() {

    // data 
    return{
      followers : 0,
      dat: '',
      user: { 
        id: 1,
        username: '_bhunte',
        first_name : 'Bhunte',
        last_name : 'Dahal',
        email : 'bhunte_stud@gmail.com',
        isAdmin : true, 
      }
    }
  },
  // watch the changes: in this case, watch the changes made in followers data
  watch: {
    followers(newFollowerCount, oldFollowerCount){

      if (newFollowerCount > oldFollowerCount){ 
        this.dat =  this.gainFollower();
       
        } else { 
          this.dat = this.loseFollower(); 
          }
    }
  },

  computed: {
    fullName() {
      return `${this.user.first_name} ${this.user.last_name}`;
    }
  },
  methods : {
    followUser() {
      this.followers ++;
    },

    unFollowUser(){
      this.followers --;
    },

    reSet(){
      this.followers = 0;
    },

    gainFollower(){
      return (`${this.user.username} has gained a follower!`);
    },

    loseFollower(){
      return (`${this.user.username} has lost a follower!`);
    }

  },

  // mounted: a hook that is run for the first time the component is run
  mounted(){
    // this.followUser();
  }
}
</script>

<style>

.user-profile{
  display: grid;
  grid-template-columns: 1fr 3fr;
  width: 100%;
  padding: 50px 5%;
}

.user-profile__user-panel{
  display: flex;
  flex-direction: column;
  margin-right: 50px;
  padding: 20px;
  background-color: white;
  border-radius: 5px;
  border: 1px solid #DFE3E8;
}

h1 {
  margin: 0;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  flex-direction: column;
  text-align: center;
}

</style>
