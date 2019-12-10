<template>
  <div>
    <div v-for="(post, index) in directory" :key="index">
      <router-link tag="h2" :to="post.path" class="title">{{ post.frontmatter.title }}</router-link>
      <p>{{ post.frontmatter.description }}</p>
    </div>
  </div>
</template>

<script>
  export default {
    computed: {
      directory() {
        return this.$site.pages
          .filter(x => x.path.startsWith('/directory/') && !x.frontmatter.directory_index)
      }
    }
  }
</script>