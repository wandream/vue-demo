<template>
    <div class="posts-tab">
      <ul class="posts-sidebar">
        <li
        v-for="post in posts"
        v-bind:key="post.id"
        v-bind:class="{ selected: post === selectedPost }"
        v-on:click="selectedPost = post"
        >
          {{ post.title }}
        </li>
      </ul>
      <div class="selected-post-container">
        <div
        v-if="selectedPost"
        class="selected-post"
        >
          <h3>{{ selectedPost.title }}</h3>
          <div v-html="selectedPost.content"></div>
        </div>
        <strong v-else>
          Click on a blog title to the left to view it.
        </strong>
      </div>
    </div>
</template>

<script>
export default {
  data () {
    return {
      posts: [
        {
          id: 1,
          title: 'cat Ipsum',
          content: '<p>one</p>'
        },
        {
          id: 2,
          title: 'one Ipsum',
          content: '<p>two</p>'
        },
        {
          id: 3,
          title: 'two Ipsum',
          content: '<p>two</p>'
        }
      ]
    }
  }
}
</script>

<style scoped>
.posts-tab {
  display: flex;
}
.posts-sidebar {
  max-width: 40vw;
  margin: 0;
  padding: 0 10px 0 0;
  list-style-type: none;
  border-right: 1px solid #ccc;
}
.posts-sidebar li {
  white-space: nowrap;
  text-overflow: ellipsis;
  overflow: hidden;
  cursor: pointer;
}
.posts-sidebar li:hover {
  background: #eee;
}
.posts-sidebar li.selected {
  background: lightblue;
}
.selected-post-container {
  padding-left: 10px;
}
.selected-post > :first-child {
  margin-top: 0;
  padding-top: 0;
}
</style>
