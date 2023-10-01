<script setup lang="ts">

  import { ref, reactive, computed } from 'vue';

  let product = reactive({
    image: true
  })
  // Ref cria uma var que guarda em value a string
  const icon = ref<string>('/icon360.svg');
  // Função que muda o icone e imagem
  function changeState(): void{
    product.image = !product.image;
    icon.value = icon.value == '/icon360.svg' ? '/iconClose.svg' : '/icon360.svg';
  }

  const productImage = computed<string>(() =>{
    return product.image ? '/sofa.svg' : '/sofa.gif';
  })

</script>

<template>
  <section id="products-page">
    <div id="left-side">
      <div class="image">
        <img :src="productImage" alt="Icone de sofá">
        <img :src="icon" alt="Icone 360" @click="changeState">
      </div>
    </div>
    <div id="right-side">
      <div class="content">
        <p>CÓDIGO: 42484</p>
        <h1>Sofá Margot II - Rosé</h1>
        <p>R$ 4.000</p>
        <button>ADICIONAR À CESTA</button>
      </div>
    </div>
  </section>
</template>

<style scoped>

  #products-page{
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    height: 100vh;
    background-color: #D9CDF7;
    color: #271A45;
  }

  #left-side{
    display: flex;
    place-items: center;
    justify-content: flex-end;
  }

  .image{
    position: relative;
  }

  .image img:first-child{
    width: 441px;
  }

  .image img:last-child{
    cursor: pointer;
    position: absolute;
    right: 60px;
    top: 0;
  }

  #right-side{
    display: flex;
    place-items: center;
    justify-content: flex-start;
  }

  .content h1{
    margin: 12px 0;
    font-weight: 600;
    font-size: 32px;
  }

  .content p:first-child{
    font-size: 10px;
    font-weight: 300;
  }

  .content p:last-child{
    font-size: 16px;
    font-weight: 400;
  }

  .content button{
    border-radius: 999px;
    border: 0.5px solid #271A45;
    padding: 8px 16px;
    background-color: transparent;
    cursor: pointer;
    margin-top: 20px;
  }

</style>
