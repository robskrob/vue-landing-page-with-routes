<template>
    <nav class="nav-wrapper">
                
        <div class="logo">
            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24"><path d="M24 10.935v2.131l-8 3.947v-2.23l5.64-2.783-5.64-2.79v-2.223l8 3.948zm-16 3.848l-5.64-2.783 5.64-2.79v-2.223l-8 3.948v2.131l8 3.947v-2.23zm7.047-10.783h-2.078l-4.011 16h2.073l4.016-16z"/></svg>
            <div class="ml-2">WebDevs</div>
        </div>
        <div class="flex">
          <template v-for="(item, parentIndex) in nav">
            <router-link :to="item.link" class="link-item" :key="parentIndex"
                :class="[ (item.subLinkModal) ? 'link-active' : '' ]"
                @click="toggleSubModal(item)">{{ item.title }}</router-link>

            <template v-if="item.subLinks && item.subLinkModal">
              <div class="sublinks" :key="parentIndex + 4">
                <template v-for="(subLink, subIndex) in item.subLinks" >
                  <a :href="subLink.link" :key="subIndex" class="link-item">{{ subLink.title }}</a>
                </template>
              </div>
            </template>
          </template>
        </div>
        
    </nav>
</template>

<script>
export default {
  data: function () {
    return {
      nav: [
        { title: 'Home', link: '/' },
        { title: 'About', link: '/about', subLinks: [
          { title: 'History', link: '#history' },
          { title: 'Our Team', link: '#team' },
        ], subLinkModal: false },
        { title: 'Services', link: '#services', subLinks: [
          { title: 'Audio', link: '#audio' },
          { title: 'Video', link: '#video' },
          { title: 'Web', link: '#web' },
        ], subLinkModal: false },
      ]
    }
  },

  methods: {
    toggleSubModal: function (item) {
      if (item.subLinks) {
        item.subLinkModal = ! item.subLinkModal;
      }
    }
  }
}
</script>
