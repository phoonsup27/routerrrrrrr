<!-- Home.vue -->
<template>
    <div class="container text-center">
      <div class="row">
        <div
          class="col mt-5"
          v-for="(restaurant, index) in travelList"
          :key="index"
        >
          <div class="card" style="width: 18rem">
            <img
              :src="restaurant.imagesP"
              class="card-img-top"
              :width="sizeW"
              :height="sizeH"
            />
            <div class="card-body">
              <h2>คันที่ : {{ index+1 }}</h2>
              <h5 class="card-title">ชื่อรถ : {{ restaurant.name }}</h5>
              <p class="card-text">ราคาเริ่ม : {{ restaurant.price }}</p>
              <button
                class="btn btn-danger"
                data-bs-toggle="modal"
                data-bs-target="#staticBackdrop"
                @click="goToOtherComponent(restaurant.name, restaurant.imagesP,index)"
              >
                จองรถ
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  import { ref } from 'vue'; // import ref
  
  export default {
    methods: {
      goToOtherComponent(name, imagesP,index) {
        // ส่งค่าไปยังคอมโพเนนต์ OtherComponent.vue ผ่านคิวรี่พารามิเตอร์
        this.$router.push({
          name: 'other',
          query: {
            index:index,
            restaurantName: name,
            restaurantImagesP: imagesP,
          },
        });
      },
    },
    setup() {
      const travelList = ref([
        
          {
      name: " Honda CBR650R (2020)",
      price: 229000,
      imagesP:
        "https://inwfile.com/s-ga/3o6mx8.jpg"  ,
    },
    {
      name: "BMW S1000RR",
      price: 666000,
      imagesP:
        "https://mcn-images.bauersecure.com/wp-images/194976/2023_bmw_s1000rr_9.jpg",
    },
    {
      name: "HONDA CBR650F 2017",
      price: 173000,
      imagesP:
        "https://image.makewebeasy.net/makeweb/m_1920x0/GKsm2kwBS/HonCBR650F4833/DSC06833.jpg",
    },
    {
      name: "KAWASAKI ZX-6R 2020",
      price: 283000,
      imagesP:
        "https://inwfile.com/s-ga/7bcoy5.jpg",
    },
  
      ]);
  
      const sizeW = 350;
      const sizeH = 250;
  
      return { // return ตัวแปรออกมาจาก setup
        travelList,
        sizeW,
        sizeH,
      };
    },
  };
  </script>
  