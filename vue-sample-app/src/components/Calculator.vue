<template>
  <div class="calculator">
    <div class = display>{{ current || '0'}}</div>
    <div @click ="clear" class = "button">C</div>
    <div @click ="sign" class = "button">+/-</div>
    <div @click ="percent" class = "button">%</div>
    <div class = "button operator-confings">/</div>
    <div @click ="append('7')"class = "button">7</div>
    <div  @click ="append('8')" class = "button">8</div>
    <div  @click ="append('9')"class = "button">9</div>
    <div class = "button operator-confings">x</div>
    <div  @click ="append('4')"class = "button">4</div>
    <div  @click ="append('5')"class = "button">5</div>
    <div  @click ="append('6')" class = "button">6</div>
    <div class = "button operator-confings">-</div>
    <div  @click ="append('1')"class = "button">1</div>
    <div  @click ="append('2')"class = "button">2</div>
    <div  @click ="append('3')"class = "button">3</div>
    <div class = "button operator-confings">+</div>
    <div @click ="append('0')" class = "button zero">0</div>
    <div @click ="dot" class = "button">.</div>
    <div class = "button operator-confings">=</div>
   </div>
</template>

<script>
  export default {
    data() {
      return {
        current: '1234'
      };
    },
    methods: {
      clear() {
        this.current = '';
      },
      sign() {
      this.current = this.current.charAt(0) === '-' ?
      this.current.slice(1) : `-${this.current}`;
    },
    percent(){
      this.current = `${parseFloat(this.current) / 100}`;
    },
    append(number){
      this.current = `${this.current}${number}`;
  },
  dot(){
    if(this.current.indexOf('.') === '-1'){
      this.append('.');
    }
  }
}    
};
</script>


<style scoped>

.calculator{

  margin: 0 auto;
  width: 400px;
  display: grid;

  /*for defining columns */
  grid-template-columns: repeat(4, 1fr) ;

  /*for defining rows */
  grid-auto-rows: minmax(50px, auto);

}

.display{
  grid-column: 1/5 ;
  background-color: #eee;
  color: black;
  font-weight: bold;

}

.zero{
  grid-column: 1/3;
}

.button{
  background-color: #eee;
  border: 1px solid #333;
}

.operator-confings{
  background-color: orange;
  color: white;
}
</style>
