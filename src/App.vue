<template>
  <div>
    <p>{{state.a}}</p>
    <p>{{state.gf.b}}</p>
    <p>{{state.gf.f.c}}</p>
    <p>{{state.gf.f.s.d}}</p>
    <button @click="myfn">按钮</button>
  </div>
</template>

<script>
import {shallowRef,triggerRef} from 'vue';
export default {
  name: 'App',
  setup() {
    let state = shallowRef({
      a: 'a',
      gf: {
        b: 'b',
        f: {
          c: 'c',
          s: {
            d: 'd'
          }
        }
      }
    });
    function myfn(){
      // state.a='1';
      // state.gf.b='2';
      // state.gf.f.c='3',
      state.value.gf.f.s.d='4';
      triggerRef(state);

      console.log(state);
      console.log(state.value);
      console.log(state.value.gf);
      console.log(state.value.gf.f);
      console.log(state.value.gf.f.s);
   }
   return{state, myfn}
   }  
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
