<template>
  <div id="app">
    <div class="w-50 mx-auto">
      <h3>オリジナルトークンを作ろう</h3>
      <b-form @submit="onSubmit" @reset="onReset" v-if="show" class="mt-4">
        <b-form-group
          id="input-group-1"
          label="トークン名："
          label-for="input-1"
        >
          <b-form-input 
            id="input-1"
            v-model="form.tokenName"
            type="text"
            required
            placeholder="Bitcoin">
          </b-form-input>
        </b-form-group>
        <b-form-group
          id="input-group-2"
          label="シンボル："
          label-for="input-2"
        >
          <b-form-input 
            id="input-2"
            v-model="form.tokenSymbol"
            type="text"
            required
            placeholder="BTC">
          </b-form-input>
        </b-form-group>
        <b-form-group
          id="input-group-4"
          label="総発行料："
          label-for="input-4"
        >
          <b-form-input 
            id="input-4"
            v-model="form.supply"
            type="number"
            required
            placeholder="1000000000000000000">
          </b-form-input>
        </b-form-group>
        <b-button type="submit" variant="primary" class="mr-2">発行する</b-button>
        <b-button type="reset" variant="danger">リセットする</b-button>
      </b-form>
      <p class="mt-4">コントラクトアドレス：{{ contractAddress }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'app',
  data: () => ({
    form: {
      tokenName: '',
      tokenSymbol: '',
      supply: 0
    },
    contractAddress: '',
    show: true
  }),
  components: {
  },
  async created()  {
  },
  methods: {
    onSubmit(evt) {
      evt.preventDefault()
    },
    onReset(evt) {
      evt.preventDefault()
      this.form.tokenName = ''
      this.form.tokenSymbol = ''
      this.form.supply = null
      this.show = false
      this.$nextTick(() => {
        this.show = true
      })
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
