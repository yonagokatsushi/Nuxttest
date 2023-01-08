<template>
  <div class="">


    <div class="">
      <h1>テストブログ</h1>
      <p>てすてすてすと</p>
      <ul>
        <li v-for="singleData in data" :key="singleData.id">
          <article>
            <h2>{{ singleData.title }}</h2>
            <p>{{ singleData.excerpt }}</p>
            <date>投稿日時：({{ singleData.date }})</date>
            <NuxtLink :to="singleData._path">続きを読む</NuxtLink>
          </article>
          <div class="image">
            <img :src="singleData.image" :alt="singleData.excerpt">
          </div>
        </li>
      </ul>
    </div>
  </div>

</template>

<script setup>


  const { data } = await useAsyncData("blogQuery", () =>
    queryContent("/blog").sort({ id: -1 }).find()
  )
</script>
