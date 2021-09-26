<template>
  <v-app id="inspire">
    <v-navigation-drawer v-model="drawer" app temporary>
      <v-list>
        <v-list-item-group>
          <v-list-item v-for="(link, i) in links" :key="i" :to="link.url">
            <v-list-item-icon>
              <v-icon v-text="link.icon"></v-icon>
            </v-list-item-icon>
            <v-list-item-content>
              <v-list-item-title v-text="link.title"></v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list-item-group>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar app color="blue darken-4" dark>
      <v-app-bar-nav-icon
        @click="drawer = !drawer"
        class="hidden-md-and-up"
      ></v-app-bar-nav-icon>
      <v-toolbar-title>AdvertApp</v-toolbar-title>
      <v-spacer></v-spacer>
      <v-toolbar-items class="hidden-sm-and-down">
        <v-btn text v-for="(link, i) in links" :key="i" :to="link.url">
          <v-icon left v-text="link.icon"></v-icon>
          {{ link.title }}
        </v-btn>
      </v-toolbar-items>
    </v-app-bar>
    <v-main>
      <router-view></router-view>
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: "App",

  components: {},

  data: () => ({
    drawer: null,
    links: [
      { title: "Login", icon: "mdi-lock", url: "/login" },
      { title: "Registration", icon: "mdi-face", url: "/register" },
      { title: "Orders", icon: "mdi-bookmark-outline", url: "/orders" },
      { title: "New advert", icon: "mdi-note-plus", url: "/new" },
      { title: "My adverts", icon: "mdi-format-list-bulleted", url: "/list" },
    ],
  }),
};
</script>
