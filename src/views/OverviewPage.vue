<template>
  <div class="flex h-full flex-col gap-2 overflow-x-hidden overflow-y-auto p-2">
    <ChartsCard />
    <NetworkCard v-if="showIPAndConnectionInfo" />
    <div
      class="card"
      v-if="displayProxiesRelationship"
    >
      <div class="card-title absolute px-4 pt-4">
        {{ $t('proxiesRelationship') }}
      </div>
      <ProxiesCharts />
    </div>
    <ConnectionHistory />
    <div class="flex-1"></div>
    <div class="card items-center justify-center gap-2 p-2 sm:flex-row">
      {{ getLabelFromBackend(activeBackend!) }} :
      <BackendVersion />
    </div>
  </div>
</template>

<script setup lang="ts">
import BackendVersion from '@/components/common/BackendVersion.vue'
import ChartsCard from '@/components/overview/ChartsCard.vue'
import ConnectionHistory from '@/components/overview/ConnectionHistory.vue'
import NetworkCard from '@/components/overview/NetworkCard.vue'
import ProxiesCharts from '@/components/overview/ProxiesCharts.vue'
import { getLabelFromBackend } from '@/helper/utils'
import { displayProxiesRelationship, showIPAndConnectionInfo } from '@/store/settings'
import { activeBackend } from '@/store/setup'
</script>
