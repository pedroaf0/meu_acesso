<template>
  <div
    class="lg:mx-20 sm:mx-20 md:mx-20 sm:px-0 sm:my-0 md:px-0 md:my-0 xl:mx-96 lg:px-42 lg:my-10 lg:shadow-2xl"
  >
    <div>
      <cabecalho titulo="Recuperar Senha" />

      <!-- <form @submit.prevent="Redefinir()" method="POST"> -->
      <div class="flex justify-center">
      
        <div
          class="grid grid-rows-2 flex justify-center mt-52 sm:mt-64 md:mt-72 lg:mt-60"
        >
          <h2 class="text-lg text-gray-500">Matricula</h2>
          <input
            v-model="data.username"
            class="p-1 border border-solid border-blue-500 rounded-md"
            placeholder="sua matricula"
            type="text"
          />

          <h2 class="text-lg mt-2 text-gray-500">Senha Atual</h2>
          <input
            v-model="data.oldPassword"
            class="p-1 border border-solid border-blue-500 rounded-md"
            placeholder="senha atual"
            type="password"
            name=""
            id=""
          />

          <h2 class="text-lg mt-2 text-purple-700">Nova Senha</h2>
          <input
            v-model="data.newPassword"
            class="p-1 border border-solid border-blue-500 rounded-md"
            placeholder="nova senha"
            type="password"
            name=""
            id=""
          />
          <!-- 
      <h2 class="text-lg mt-2 text-purple-700">Confirme sua Senha</h2>
      <input v-model="ConfirmaSenha" id='confirma' class="p-1 border border-solid border-blue-500 rounded-md" placeholder="nova senha" type="password" name=""  /> -->
        </div>
      </div>

      <router-link :to="{ name: 'recuperaremail' }">
        <div class="flex justify-center flex-grow-0 m-1">
          <a class="text-lg text-indigo-700 underline">Redefinir por Email ?</a>
        </div>
      </router-link>

      <div
        v-show="modal"
        class="fixed inset-0 w-full h-screen flex items-center justify-center bg-semi-75 p-8">

        <div
          class="relative  max-w-2xl bg-white shadow-2xl rounded-lg p-8 border border-solid border-purple-800">
           <h2 class="text-lg mt-2 text-purple-700 ">{{ message }}</h2>
              <div class="flex justify-center flex-grow-0 m-1">
                <botao rotulo="Entrar" tipo="submit" v-on:click="closeModal"/>              
              </div>
        </div>
      </div>

      <div class="flex justify-center flex-grow-0">
        <botao :rotulo="textBotao" tipo="submit" @click="Redefinir()" />

      </div>
      <img-ifrs />
    </div>
  </div>
</template>

<script>
import Requests from "../services/requests";

import Botao from "./Botao.vue";
import Cabecalho from "./Cabecalho.vue";
import ImagemIFRS from "./ImagemIFRS.vue";


export default {
  data() {
    return {
      data: {
        username: {
          type: Number,
          required: true,
        },
        newPassword: {
          type: String,
          required: true,
        },
        oldPassword: {
          type: String,
          required: true,
        },
      },
      modal: false,
      message: "",
      textBotao: 'Redefinir Senha'
    };
  },
  components: {
    botao: Botao,
    cabecalho: Cabecalho,
    "img-ifrs": ImagemIFRS,
  },

  mounted() {

  },

  computed: () => {

    //  reversedMessage: function () {
    //   // `this` points to the vm instance
    //   return this.message.split('').reverse().join('')
    // }


  },

  updated(){
  },

  methods: {

    Redefinir() {
      this.textBotao = 'Aguarde ....'
      alert(this.data)
      // Requests.recuperar(this.data)
      //   .then((res) => {
      //     if(res.status == 200){
      //     this.modal = true;
      //     this.message = res.data.message;
      //     this.$router.push({ name: 'aluno' })
      //     }
      //   })
      //   .catch((err) => {
      //     console.error(err.message);
      //       this.message = `Não foi possivel trocar a senha do usuário ${this.data.username}`;
      //       this.modal = true;
      //       this.$router.push({ name: 'recuperarsenha' })
      //   })
    },
    closeModal() {
      this.modal = false;
      this.$forceUpdate();
    },
  },
};
</script>
