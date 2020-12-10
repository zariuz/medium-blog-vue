<template>
  <nav class="navbar navbar-light">
    <div class="container">
      <router-link class="navbar-brand" :to="{ name: 'home' }">
        MediumClone
      </router-link>
      <ul class="nav navbar-nav pull-xs-right">
        <li class="nav-item">
          <router-link class="nav-link" :to="{ name: 'home' }" active-class="activ" exact
            >Home</router-link
          >
        </li>
        <template v-if="isLoggedIn">
          <li class="nav-item">
            <router-link
              class="nav-link"
              :to="{ name: 'createArticle' }"
              active-class="activ"
            >
              <i class="ion-compose" />
              &nbsp; New Article
            </router-link>
          </li>

          <li class="nav-item">
            <router-link class="nav-link" :to="{ name: 'settings' }" active-class="activ">
              <i class="ion-gear-a" />
              &nbsp; Settings
            </router-link>
          </li>

          <li class="nav-item">
            <router-link
              class="nav-link"
              :to="{ name: 'userProfile', params: { slug: currentUser.username } }"
            >
              <img class="user-pic" :src="currentUser.image" />
              &nbsp;
              {{ currentUser.username }}
            </router-link>
          </li>
        </template>
        <template v-if="isAnonymous">
          <li class="nav-item">
            <router-link class="nav-link" :to="{ name: 'login' }" active-class="activ">
              Sign in
            </router-link>
          </li>
          <li class="nav-item">
            <router-link class="nav-link" :to="{ name: 'register' }" active-class="activ">
              Sign up
            </router-link>
          </li>
        </template>
      </ul>
    </div>
  </nav>
</template>

<script>
import { mapGetters } from 'vuex';
import { getterTypes } from '@/store/modules/auth';

export default {
  name: 'McvTopbar',

  computed: {
    ...mapGetters({
      currentUser: getterTypes.currentUser,
      isLoggedIn: getterTypes.isLoggedIn,
      isAnonymous: getterTypes.isAnonymous,
    }),
  },
};
</script>
