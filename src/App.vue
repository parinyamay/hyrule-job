<template>
  <div class="app">
    <header>
      <div class="title">
        <i class="fa-regular fa-heart" style="margin-right: 16px"></i>
        <h1>Hryule Jobs</h1>
        <i class="fa-regular fa-heart" style="margin-left: 16px"></i>
      </div>
      <div class="order">
        <button @click="handleClick('title')">order by title</button>
        <button @click="handleClick('salary')">order by salary</button>
        <button @click="handleClick('location')">order by location</button>
      </div>
    </header>
    <JobList :jobs="jobs" :order="order" />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue'
import JobList from './components/JobsList.vue'
import Job from './types/Job'
import OrderTerm from './types/OrderTerm'

export default defineComponent({
  name: 'App',
  components: { JobList },
  setup() {
    const jobs = ref<Job[]>([
      { title: 'fram worker', location: 'lon lon ranch', salary: 30000, id: '1' },
      { title: 'quarryman', location: 'death mountain', salary: 40000, id: '2' },
      { title: 'flute player', location: 'the lost woods', salary: 35000, id: '3' },
      { title: 'fisherman', location: 'lake hylia', salary: 21000, id: '4' },
      { title: 'prison guard', location: 'gerudo valley', salary: 32000, id: '5' },
    ])

    const order = ref<OrderTerm>('title')

    const handleClick = (term: OrderTerm) => {
      order.value = term
    }

    return { jobs, handleClick, order }
  },
})
</script>

<style>
header {
  text-align: center;
}

header .order {
  margin-top: 20px;
}

header .title {
  display: flex;
  align-items: center;
  justify-content: center;
}

header .title i {
  font-size: 48px;
}

button {
  margin: 0 10px;
  color: #1195c9;
  border: 3px solid #1195c9;
  background: #d5f0ff;
  padding: 8px 18px;
  border-radius: 4px;
  cursor: pointer;
  font-weight: bold;
}
</style>
