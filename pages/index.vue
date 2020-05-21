<template>
  <div>
    <img-slot />
    <input id="start" type="button" value="Start" @click="startSlot" />
    <input id="stop" type="button" value="Stop" @click="stopSlot" />
  </div>
</template>

<script>
import ImgSlot from '~/components/ImgSlot.vue'

export default {
  components: {
    ImgSlot
  },
  data() {
    return {
      imgList: [
        'https://www.pakutaso.com/shared/img/thumb/017AME5031_TP_V.jpg',
        'https://www.pakutaso.com/shared/img/thumb/PP_englishrose_TP_V.jpg',
        'https://www.pakutaso.com/shared/img/thumb/AME832_teibanmomiji_TP_V.jpg'
      ],
      slotId: 1
    }
  },
  methods: {
    setImg(id) {
      const selectImg = Math.floor(Math.random() * this.imgList.length)
      document.getElementById(`${id}`).src = this.imgList[selectImg]
    },
    startSlot() {
      const self = this
      this.slotId = setInterval(function() {
        self.setImg('img1')
        self.setImg('img2')
        self.setImg('img3')
      }, 50)
    },
    stopSlot() {
      clearInterval(this.slotId)
    }
  }
}
</script>
