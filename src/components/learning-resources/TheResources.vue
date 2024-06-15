<template>
  <base-card>
    <base-button @click="setSelectedTab('stored-resources')"
    :mode="storedResBtnMode"
      >Stored Resources</base-button
    >
    <base-button @click="setSelectedTab('add-resource')"
    :mode="addResBtnMode"
      >Add Resource</base-button
    >
  </base-card>
  <component :is="selectedTab"></component>
</template>

<script>
import StoredResources from "./StoredResources.vue";
import AddResource from "./AddResource.vue";

export default {
  components: {
    StoredResources,
    AddResource,
  },
  data() {
    return {
      selectedTab: "stored-resources",
      storedResources: [
        {
          id: "official-guide",
          title: "Vue Official Guide",
          description: "The official Vue.js documentation.",
          link: "https://vuejs.org",
        },
        {
          id: "google",
          title: "Google",
          description: "Everybody knows Google.",
          link: "https://www.google.pl",
        },
      ],
    };
  },
  computed: {
    storedResBtnMode() {
        return this.selectedTab === 'stored-resources' ? null : 'flat';
    },
    addResBtnMode() {
        return this.selectedTab === 'add-resource' ? null : 'flat';
    }
  },
  provide() {
    return {
        resources: this.storedResources
    }
  },
  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab;
    },
  },
};
</script>
