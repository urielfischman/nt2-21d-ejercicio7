<template>

  <section class="src-components-usuarios">
    <div class="container-fluid mt-3">
      <div v-if="usuarios.length" class="table-responsive">
        <table class="table table-dark">
          <tr>
            <th>Nombre</th>
            <th>Edad</th>
            <th>Email</th>
          </tr>
          <tr v-for="(usuario,index) in usuarios" :key="index">
            <td>{{ usuario.nombre }}</td>
            <td>{{ usuario.edad }}</td>
            <td>{{ usuario.email }}</td>
          </tr>
        </table>
      </div>
      <h4 v-else class="alert alert-danger text-center">No hay usuarios disponibles</h4>
    </div>
  </section>

</template>

<script lang="js">

  export default  {
    name: 'src-components-usuarios',
    props: [],
    mounted () {
      this.axios(this.url)
      .then(({ data:respuesta }) => {
        this.usuarios = respuesta
      })
      .catch( error => console.error('Error en Axios:', error))
    },
    data () {
      return {
        url: 'https://627da4d7dd8aafd4fa80f897.mockapi.io/users',
        usuarios: []
      }
    },
    methods: {

    },
    computed: {

    }
}


</script>

<style scoped lang="css">
  .src-components-usuarios {

  }
</style>
