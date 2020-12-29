<template>
  <div>
    <v-container>
      <v-flex xs12 pb5>
        <h2>News</h2>
      </v-flex>

      <v-flex v-for="(article, index) in articles" :key="index" pb-3>
        <!-- News -->
        <v-card class="mx-auto" max-width="600">
          <v-img
            class="white--text align-end"
            height="200px"
            :src="article.urlToImage"
          />
          <v-card-title>{{ article.title }}</v-card-title>

          <v-card-subtitle class="pb-0"> {{ article.author }} </v-card-subtitle>

          <v-card-text class="text--primary">
            <div>{{ article.content }}</div>
          </v-card-text>

          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn :href="article.url" target="_blank" color="orange" text
              >Open</v-btn
            >
          </v-card-actions>
        </v-card>
      </v-flex>
    </v-container>
  </div>
</template>

<script>
export default {
  async asyncData({ app }) {
    const { articles } = await app.$axios.$get(
      'https://newsapi.org/v2/top-headlines?country=us&category=business&apiKey=3575ca4502914139af45c385d5ebc20b'
    )
    return { articles }
  },
}
</script>
