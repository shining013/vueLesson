<template>
  <div class="container">
    <h2 class="mb-10">HOT & NEW</h2>
    <div class="cardWrap">
      <div class="card" v-for="(item, i) in data" :key="i">
        <div class="imgWrap">
          <img v-bind:src="`./images/${item.img}`" :alt="`${item.img}`" />
          <div class="hot" v-if="item.hoticon">HOT</div>
        </div>
        <div class="cardBody">
          <h4>{{ item.title }}</h4>
          <p>🍿 {{ item.num }}</p>
          <p>대여: {{ item.won }} ⓒ</p>
          <p>
            👍 {{ item.like }}
            <button v-on:click="increaseLike(i)">클릭</button>
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import mdata from "./assets/mdata";

export default {
  name: "appView",
  data() {
    return {
      data: mdata,
      title: "test",
    };
  },
  methods: {
    increaseLike(i) {
      this.data[i].like += 1;
      this.title = "no";
    },
  },
};
</script>

<style lang="scss" scoped>
$radius: 5px;
.container {
  width: 1000px;
  margin: 0 auto;

  @media screen and (max-width: 790px) {
    width: 100%; /* 컨트롤바 없음 */
    padding: 0 16px;
  }
  img {
    display: block;
  }
}

.cardWrap {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  .card {
    width: calc((100% - 40px) / 5);
    @media screen and (max-width: 790px) {
      width: calc((100% - 20px) / 2);
    }

    @media screen and (max-width: 560px) {
      width: 100%;
    }

    .imgWrap {
      width: 100%;
      position: relative;
      overflow: hidden;
      cursor: pointer;
      border-radius: $radius;
      img {
        width: 100%;
        transition: 0.3s;
      }
      &:hover img {
        transform: scale(1.1);
      }
      .hot {
        position: absolute;
        top: 10px;
        left: 10px;
        background-color: skyblue;
        padding: 2px 10px;
        border-radius: 5px;
        font-weight: bold;
        color: white;
      }
    }
  }
}
.mb10 {
  margin-bottom: 10px !important;
}
</style>
