<template>
  <div class="col-sm-4" @click="switchChar">
    <div class="item-card">
      <div class="card-block">
        <h4 class="card-title">{{item.name}}</h4>
        <div v-for="(value, key, index) in item">
          <div class v-if="index < 5">
            <strong>{{key}}</strong>
            : {{value}}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["passedItem", "type"],

  // created() {
  //   console.log();

  // },

  data() {
    return {
      item: {}
    };
  },

  methods: {
    switchChar() {
      const random_num = Math.floor(Math.floor(Math.random() * 63) + 1);
      fetch(`https://swapi.co/api/${this.type}/${random_num}`, {
        method: "GET"
      })
        .then(response => response.json())
        .then(json => (this.item = json));
    }
  },
  created() {
    this.item = this.passedItem;
  }
};
</script>
