<script setup>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup
import Item from './components/Item.vue'
import Footer from './components/Footer.vue'
</script>

<script>
// import Dados from './Dados/Services.json';

export default {
  data(){
    return{
      servicos: null
    }
  },
  mounted(){
    fetch("https://raw.githubusercontent.com/yurimarcon/link-services/main/src/Dados/Services.json")
      .then(res => res.json())
      .then(res => this.servicos = res)
      .catch(e => console.log(e))
  }
}
</script>

<template>
  <img alt="Vue logo" style="width:70px" src="./assets/logo.png" />
  <h1>Seja bem vindo(a)!</h1>
  <hr/>
  <div class="items">
    <Item 
    v-for="servico, index in servicos"
    :key="index"
    :item="servico"
    />

  </div>

  <Footer />
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
html{
  background: url("https://cdn.pixabay.com/photo/2017/01/24/03/53/plant-2004483_960_720.jpg");
  background-repeat: no-repeat;
  background-size: cover;
  min-height: 100%;
}
.items{
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
</style>
