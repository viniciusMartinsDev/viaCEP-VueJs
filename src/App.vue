<template>
  <div id="app">
    <article class="container">
      <header>Consumindo API: ViaCEP</header>
      <input type="text" placeholder="Digite o CEP..." v-model="cep" @keydown.enter="buscarCEP"/>
      <p>Logradouro: {{info.logradouro == "" ? "Não está disponível" : info.logradouro}}</p>
      <p>Complemento: {{info.complemento == "" ? "Não está disponível" : info.complemento}}</p>
      <p>Bairro: {{info.bairro == "" ? "Não está disponível" : info.bairro}}</p>
      <p>Localidade: {{info.localidade == "" ? "Não está disponível" : info.localidade}}</p>
      <p>Uf: {{info.uf == "" ? "Não está disponível" : info.uf}}</p>
      <p>IBGE: {{info.ibge == "" ? "Não está disponível" : info.ibge}}</p>
      <p>GIA: {{info.gia == "" ? "Não está disponível" : info.gia}}</p>
      <p>DDD: {{info.ddd == "" ? "Não está disponível" : info.ddd}}</p>
      <p>Siafi: {{info.siafi == "" ? "Não está disponível" : info.siafi}}</p>
    </article>


  </div>
</template>

<script>
export default {
  name: 'App',
  data(){
    return{
      info: Object,
      cep: null

    }
  },
  async mounted(){
    // const cep = '86430000'

  },
  methods:{
    async buscarCEP(){
      const res = await this.$http.get(`/${this.cep}/json`)
      // console.log(res.data)
      this.info = res.data
    }
  }
}

</script>

<style>
*{
  margin: 0;
  padding: 0;
  border: 0;
  box-sizing: border-box;

  font-family: 'Roboto Mono', monospace;
}

#app{
  background: #E0E0E0;
  width: 100vw;
  height: 100vh;

  display: flex;
  justify-content: center;
  align-items: center;
}
.container{
  background: #FFFFFF;
  padding: 40px;

  border-radius: 8px;
  box-shadow: 8px 3px 2px #C0C0C0;
}
.container header{
  font-size: 25px;
  font-weight: 400;

  background: #E8E8E8;
  padding: 10px;
  border-radius: 8px;
  box-shadow: 2px 1px 5px #C0C0C0 ;

  margin-bottom: 25px;
}
.container input{
  font-size: 16px;
  font-weight: 300;
  width: 100%;

  background: #E8E8E8;
  padding: 10px;
  border-radius: 8px;
  box-shadow: 2px 1px 5px #C0C0C0 ;
  
  margin-bottom: 8px;
}
.container p {
  font-size: 16px;
  font-weight: 300;

  background: #E8E8E8;
  padding: 10px;
  border-radius: 8px;
  box-shadow: 2px 1px 5px #C0C0C0 ;

  margin-bottom: 8px;
}
</style>
