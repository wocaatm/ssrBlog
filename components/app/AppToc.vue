<template>
  <div v-if="toc.length" class="w-full lg:w-1/4 block relative">
    <div
      class="lg:sticky lg:top-16 overflow-y-auto h-full lg:h-auto lg:max-h-(screen-16)"
    >
      <nav class="py-4 lg:py-8 lg:px-8">
        <p
          class="mb-3 lg:mb-2 text-gray-500 uppercase tracking-wider font-bold text-base"
        >
          文章目录
        </p>
        <scrollactive
          highlight-first-item
          active-class="text-primary-500"
          :offset="0"
          tag="ul"
        >
          <li
            v-for="link of toc"
            :key="link.id"
            class="text-gray-700 dark:text-gray-300"
            :class="{
              'border-t border-dashed dark:border-gray-800 first:border-t-0':
                link.depth === 2,
            }"
          >
            <a
              :href="`#${link.id}`"
              class="block text-sm scrollactive-item transition-padding ease-in-out duration-300 hover:pl-1"
              :class="{
                'py-2': link.depth === 2,
                'ml-2 pb-2': link.depth === 3,
                'ml-3 pb-2': link.depth === 4,
                'ml-4 pb-2': link.depth === 5,
                'ml-5 pb-2': link.depth === 6,
              }"
              >{{ link.text }}</a
            >
          </li>
        </scrollactive>
      </nav>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    toc: {
      type: Array,
      default: () => [],
    },
  },
}
</script>
