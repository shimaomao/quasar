<template>
  <q-btn
    round
    small
    @click="click"
    :outline="outline"
    :push="push"
    :flat="flat"
    :color="color"
    :glossy="glossy"
    :icon="icon"
  >
    <slot></slot>
  </q-btn>
</template>

<script>
import { QBtn } from '../btn'
import FabMixin from './fab-mixin'

export default {
  name: 'q-fab-action',
  mixins: [FabMixin],
  components: {
    QBtn
  },
  inject: {
    __qFabClose: {
      default () {
        console.error('QFabAction needs to be child of QFab')
      }
    }
  },
  props: {
    icon: {
      type: String,
      required: true
    }
  },
  methods: {
    click (e) {
      this.__qFabClose(() => {
        this.$emit('click', e)
      })
    }
  }
}
</script>
