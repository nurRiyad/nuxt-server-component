<script lang="ts" setup>

const { data } = useFetch<Array<Record<string,string>>>('https://jsonplaceholder.typicode.com/posts');
const searchText = ref('')

const filterEdData = computed(() => {
  if (!searchText.value) return data.value
  return data.value?.filter((item: any) => item.title.includes(searchText.value))
})

</script>

<template>
  <div>
    <h1>Normal Component(Search work)</h1>
    <input type="text" v-model="searchText" placeholder="Search Title" />
    <pre>{{ filterEdData }}</pre>
  </div>
</template>
