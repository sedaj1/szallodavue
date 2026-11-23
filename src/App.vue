<script setup>

</script>

<NavBar />

  <main class="container py-4">
    <div v-if="uzenet.szoveg" :class="`alert alert-${uzenet.tipus}`">
      {{ uzenet.szoveg }}
    </div>

    <section id="szobak" class="mb-5">
      <h2 class="h4 mb-3">Szobák</h2>
      <RoomFilter v-model="szobaSzuro" class="mb-3" />
      <RoomList :szobak="szobaAllapotok" />
    </section>

    <section id="foglalasok" class="mb-5">
      <div class="row g-4">
        <div class="col-lg-5">
          <h2 class="h4 mb-3">{{ szerkesztett ? 'Foglalás módosítása' : 'Új foglalás' }}</h2>
          <BookingForm
            :kezdeti="szerkesztett"
            @mentes="mentes"
            @megse="szerkesztett = null"
          />
        </div>

        <div class="col-lg-7">
          <h2 class="h4 mb-3">Foglalások</h2>
          <BookingList
            v-model:keres="keresettNev"
            :foglalasok="szurtFoglalasok"
            @szerkesztes="szerkesztett = $event"
            @torles="torles"
          />
        </div>
      </div>
    </section>
  </main>

<style scoped>

</style>