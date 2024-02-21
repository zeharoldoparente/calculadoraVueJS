<!-- App.vue -->
<template>
   <div id="app">
      <h1>Calculadora VueJS</h1>
      <div class="calculator">
         <input
            type="number"
            v-model.number="numero1"
            placeholder="Digite o primeiro número"
         />
         <select v-model="operacao" @change="calcular">
            <option value="soma">+</option>
            <option value="subtracao">-</option>
            <option value="multiplicacao">*</option>
            <option value="divisao">/</option>
         </select>
         <input
            type="number"
            v-model.number="numero2"
            placeholder="Digite o segundo número"
         />
      </div>
      <div v-if="resultado !== null" class="resultado">
         <p>O resultado da operação é: {{ resultado }}</p>
      </div>
   </div>
</template>

<script>
export default {
   name: "App",
   data() {
      return {
         numero1: 0,
         numero2: 0,
         operacao: "soma",
         resultado: null,
      };
   },
   methods: {
      calcular() {
         switch (this.operacao) {
            case "soma":
               this.resultado = this.numero1 + this.numero2;
               break;
            case "subtracao":
               this.resultado = this.numero1 - this.numero2;
               break;
            case "multiplicacao":
               this.resultado = this.numero1 * this.numero2;
               break;
            case "divisao":
               this.resultado =
                  this.numero2 !== 0
                     ? this.numero1 / this.numero2
                     : "Indefinido";
               break;
            default:
               this.resultado = null;
         }
      },
   },
};
</script>

<style>
#app {
   font-family: Arial, sans-serif;
   text-align: center;
}

.calculator {
   margin-bottom: 20px;
}

input[type="number"],
select {
   padding: 8px;
   margin: 5px;
   border-radius: 5px;
   border: 1px solid #ccc;
}

button {
   padding: 10px 20px;
   border: none;
   border-radius: 5px;
   background-color: #007bff;
   color: #fff;
   cursor: pointer;
}

button:hover {
   background-color: #0056b3;
}

.resultado {
   font-size: 20px;
   margin-top: 20px;
}
</style>
