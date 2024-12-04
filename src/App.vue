<script>
// import HelloWorld from "./components/HelloWorld.vue";
import axios from 'axios'

export default {
  name: "app",
  data() {
    return {
      title: "Lab-Dashboard",
      lastUpdate: '',
      data: []
    };
  },
  methods: {
    getData() {
      axios.get(import.meta.env.VITE_API_KEY)
      .then((res)=> {
        if(res.data.result === "DONE"){
          console.log(res.data)
          this.data = res.data.data[0]
          this.lastUpdate = res.data.data[0].time
        }
      })
    }
  },
  beforeMount() {
    this.getData()
    setInterval(() => {
      this.getData()
    }, 60000);
   
  },
};
</script>

<template>
  <div>
    <nav class="navbar bg-body-tertiary">
      <div class="container text-center">
        <div class="row">
          <div class="col"><img src="./assets/udch.png" width="80" /></div>
        </div>
      </div>
    </nav>
    <h1 style="padding: 2em 0px 1em 0px">{{ title }}</h1>


    <div class="container text-center">
      <!-- <div class="container text-center">
      <div class="row row-cols-5">
        <div class="col">Column</div>
        <div class="col">Column</div>
        <div class="col">Column</div>
        <div class="col">Column</div>
        <div class="col">Column</div>
      </div> -->
    <!-- </div> -->

      <div class="row row-cols-5">
        <div class="col logo">
          <div class="card">
            <div class="card-body">
              <h1 class="card-title">LAB</h1>
              <p class="card-text">
                <span class="text-num"> {{ data.LAB }}</span>
              </p>
            </div>
          </div>
        </div>

        <div class="col logo">
          <div class="card">
            <div class="card-body">
              <h1 class="card-title">BLOODBANK</h1>
              <p class="card-text">
                <span class="text-num"> {{ data.BB }}</span>
              </p>
            </div>
          </div>
        </div>

        <div class="col logo">
          <div class="card" style="width: 100%">
            <div class="card-body">
              <h1 class="card-title">CYTO</h1>
              <p class="card-text">
                <span class="text-num"> {{ data.CYTO }}</span>
              </p>
            </div>
          </div>
        </div>
        <div class="col logo">
          <div class="card" style="width: 100%">
            <div class="card-body">
              <h1 class="card-title">PATHO</h1>
              <p class="card-text">
                <span class="text-num"> {{ data.PATHO }}</span>
              </p>
            </div>
          </div>
        </div>

        <div class="col logo">
          <div class="card" style="width: 100%">
            <div class="card-body">
              <h1 class="card-title">NON GYNAE</h1>
              <p class="card-text">
                <span class="text-num"> {{ data.NONGYNAE }}</span>
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>

    <p style="padding-top: 2em">last update : {{ lastUpdate }}</p>

    <!-- <a href="https://vitejs.dev" target="_blank"> -->
    <!-- <img src="/vite.svg" class="logo" alt="Vite logo" /> -->
    <!-- </a> -->
    <!-- <a href="https://vuejs.org/" target="_blank"> -->
    <!-- <img src="./assets/vue.svg" class="logo vue" alt="Vue logo" /> -->
    <!-- </a> -->
  </div>
</template>

<style scoped>
.text-num {
  font-size: 8vw;;
  font-weight: bold;
  border-radius: 10%;
}
.card-title{
  height: 100px;
  align-content: center
}
.logo {
  /* height: 6em; */
  /* padding: 1.5em; */
  will-change: filter;
  transition: filter 300ms;
  
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
