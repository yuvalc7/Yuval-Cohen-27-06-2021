<template>

  <div class="container-app" id="app" :style="[ themeLight ?  {'background-color' : '#9086862e'} : {'background-color' : 'rgb(1 4 25 / 93%)'}  ]">
    <div class="header">
    <NavigationHeader @selected-screen="setSelectedScreen"/>
    </div>
    <div class="body container">
    <router-view></router-view>
    </div>
    <div class="footer">
      <Footer></Footer>
    </div>
  </div>
</template>

<script>

import NavigationHeader from "./components/header/NavigationHeader";
import Footer from "./components/Footer/Footer"
import {mapState} from "vuex";

export default {
  name: 'App',
  components: {
    NavigationHeader,
    Footer
  },

  computed:{
    ...mapState(["themeLight"])
  },

  data(){
    return{
       showHomeScreen: true
    }
  },

  methods:{
    setSelectedScreen(isHomeScreen){
      this.showHomeScreen = isHomeScreen;
    }

  }
}
</script>

<style>

.container-app{
  display: flex;
  flex-direction: column;
  min-height: 100vh;
  padding-bottom: 60px;
  justify-content: space-between;
}

.header{
  margin-bottom: 3%;
}

.body{
  margin-bottom: 3%;
}

.footer{
  border-top: 1px solid rgba(54, 53, 53, 0.32);
  position: fixed;
  right: 0;
  left: 0;
  bottom: 0;
  z-index: 1;
  background-color: white;
}
</style>
