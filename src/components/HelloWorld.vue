<template>
  <div>
    <table>
      <tr>
        <td>Nombres</td>
      </tr>
      <tr
        v-for='(character, index) in characters'
        :key='index'
      >
        <td>{{ character.name }}</td>
      </tr>
    </table>
  </div>
</template>

<script>

export default {
  name: 'HelloWorld',
  data () {
    return {
      characters: []
    }
  },
  mounted () {
    this.getCharacters()
  },
  methods: {
    async getCharacters () {
      const url = 'https://rickandmortyapi.com/api/character'
      const { data } = await this.axios.get(url)
      this.characters = data.results
    }
  }
}
</script>

<style scoped>
table, th, td {
  border: 1px solid black;
  border-collapse: collapse;
}

table tr:first-child {
  background: #eaeaea;
}

td {
  padding: 10px;
  min-width: 200px;
}
</style>
