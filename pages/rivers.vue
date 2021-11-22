<template>
  <div>
    <div>
      <h1>Nuxt Rivers</h1>
      <div
        v-for="river in $data.rivers"
        :key="river.title"
        class="md:flex flex-col"
      >
        <div class="max-w-lg rounded overflow-hidden shadow-lg m5">
          <img class="w-full" :src="river.image" alt="river.title" />
          <div class="px-6 py-4">
            <nuxt-link :to="river.slug">
              <div class="font-bold text-xl mb-2">{{ river.title }}</div>
            </nuxt-link>
            <p class="text-gray-700 text-base">
              {{ river.description }}
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $axios }) {
    const rivers = await $axios.$get('https://api.nuxtjs.dev/rivers')
    return { rivers }
  },
}
</script>

<style></style>
