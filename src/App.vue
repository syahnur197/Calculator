<template>
  <div id="app">
    <div class="jumbotron">
      <h1>
        <span class="fa fa-calculator"></span>
        Calculator
      </h1>
    </div>
    <div class="container">
      <h4>Hello! Welcome to Calculator. Use this website to calculate your volume!</h4>
      <p>Note that the lot calculated is a rough estimate, it should be accurate for all XXXUSD pairs!</p>
      <label>Select Your Account</label>
      <br>
      <input type="radio" name="standard" value="0" id="" v-model="account"> Standard (100,000 unit per lot) <br>
      <input type="radio" name="micro" id="" value="1" v-model="account"> Mini (10,000 unit per lot) <br>
      <input type="radio" name="micro" id="" value="2" v-model="account"> Micro (1,000 unit per lot)

      <br>
      <label for="">Dollar Risk: </label>
      <input type="number" name="dollar" id="dollar" v-model="dollar" class="form-control">

      <br>
      <label for="">Pips Risk: </label>
      <input type="number" name="pips" id="pips" v-model="pips" class="form-control">

      <br>
      <label for="">Volume: {{volume}}</label>

    </div>
    <footer class="footer bg-secondary py-4 fixed-bottom">
      <div class="container">
        <span class="text-light">Syahnur Nizam &copy;
          {{yearNow}}
        </span>
      </div>
    </footer>
  </div>
</template>

<script>
export default {
  data() {
    return {
      dollar: 5,
      pips: 50,
      account: "0"
    }
  },

  computed: {
    volume() {
      if(this.account === "0") {
        return (this.dollar/(10*this.pips)).toFixed(2)
      } else if (this.account === "1") {
        return (this.dollar/(this.pips)).toFixed(2)
      } else {
        return (this.dollar/(0.1*this.pips)).toFixed(2)
      }
    },

    yearNow() {
      return (new Date()).getFullYear();
    }
  },

  methods: {
    activate(index) {
      this.buttons[0] = false;
      this.buttons[1] = false;
      this.buttons[index] = true;
      // console.log(this.buttons[index])
    }
  }
}
</script>


<style lang="scss">
</style>
