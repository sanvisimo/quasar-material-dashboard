<template>
  <q-header class="text-primary bg-white">
    <q-toolbar>
      <q-btn
        flat
        dense
        round
        aria-label="Menu"
        @click="SET_DRAWER(!drawer)"
      >
        <q-icon v-if="value" name="mdi-view-quilt" />

        <q-icon v-else name="mdi-dots-vertical" />
      </q-btn>

      <q-toolbar-title>
        {{ $route.name }}
      </q-toolbar-title>

      <q-input
        :label="$t('search')"
        color="secondary"
        hide-details
        dense
        style="max-width: 165px;"
      >
        <template
          v-slot:after
        >
          <q-btn
            class="q-mt-xs"
            fab-mini
            dense
            icon="mdi-magnify"
          />
        </template>
      </q-input>

      <div class="q-mx-md" />

      <q-btn
        class="q-ml-sm"
        min-width="0"
        icon="mdi-view-dashboard"
        to="/"
        flat
      />

      <q-btn
        class="ml-2"
        min-width="0"
        flat
        icon="mdi-account"
        to="/user"
      />

      <div>Quasar v{{ $q.version }}</div>
    </q-toolbar>
  </q-header>
</template>

<script>
import { createNamespacedHelpers } from "vuex";

const { mapState, mapMutations } = createNamespacedHelpers("layout");

export default {
  name: "Appbar",
  props: {
    value: {
      type: Boolean,
      default: false
    }
  },
  computed: {
    // look up in `some/nested/module`
    ...mapState({
      drawer: state => state.drawer
    })
  },
  methods: {
    // look up in `some/nested/module`
    ...mapMutations(["SET_DRAWER"])
  }
};
</script>

<style scoped></style>
