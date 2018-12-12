<template lang="pug">
  <div id="app" class="grid">
    .grid__vertical-spacer
    .grid__button-section
      button.button.button--primairy Listen to latest
      br
      div
        span(style="margin: 0 15px;")
          b More
        button.button.button--icon ▼
    .grid__banner.main-banner
      h1.main-banner__title 51 % CORRECT
    .grid__ctas
      button.button listen now
      button.button download latest
    .grid__about.about-section
      h2.about-section__title About
      p.about-section__body Techtopia is a show that zooms in on the interaction of the digital and the analog. In a more concrete manner this means that we take a look at something and the influence technology has on it.
    .grid__userdata.user-data-section
      h2.user-data-section__title USERDATA:
      ul.user-data-section__body
        li > {{userData[0]}}
        li > {{userData[1]}}
        li > {{userData[2]}}
        li > {{userData[3]}}
        li > _
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'app',
  components: {
    HelloWorld
  },
  computed: {
    userData () {
      return [
        window.navigator.appCodeName,
        window.navigator.oscpu,
        window.navigator.language,
        `notrack: ${window.navigator.doNotTrack}`
      ]
    }
  }
}
</script>

<style lang="scss">
// VARS //
$sm-break: 600px;

// GENERAL EL CSS //
html {
  font-size: 14px;
}
h1, h2, h3, h4, h5, h6 {
  margin: 0;
  font-stretch: condensed;
}

ul {
  list-style: none;
  padding-left: 5px;
}

* {
  box-sizing: border-box;
}

#app {
  font-family: 'Helvetica Neue', -apple-system, BlinkMacSystemFont, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
}

.grid {
  display: grid;
  grid-template-columns: 90px repeat(9, 1fr) 90px;
  grid-template-rows: 70px 180px 140px 60px 170px 80px;
  grid-column-gap: 20px;
  grid-template-areas:
    ".              .             .             .             header-middle header-middle .             .             .             .             .             "
    ".              header-left   header-left   .             header-middle header-middle .             .             header-right  header-right  .             "
    "main-center    main-center   main-center   main-center   main-center   main-center   main-center   main-center   main-center   main-center   main-center   "
    ".              .             .             .             .             .             .             .             .             .             .             "
    ".              sub-cta       sub-cta       .             sub-about     sub-about     .             .             sub-userdata  sub-userdata  .             ";

  @media (max-width: $sm-break) {
    grid-template-columns: 20px repeat(1, 1fr) 20px;
    grid-template-rows: 70px 180px 140px 60px 170px 140px;
    grid-column-gap: 20px;
    grid-template-areas:
      ".              header-middle .             "
      ".              header-right  .             "
      "main-center    main-center   main-center   "
      ".              .             .             "
      ".              sub-cta       .             "
      ".              sub-about      .             "
      ".              sub-userdata   .             ";
  }

  &__button-section {
    grid-area: header-right;
    justify-self: end; // pull to right
    text-align: right;
  }

  &__vertical-spacer {
    grid-area: header-middle;
    border-left: 3px solid black;
    height: 170px;
  }
  &__banner {
    grid-area: main-center;
    align-self: end; // pull to bottom
  }
  &__ctas {
    grid-area: sub-cta;
  }
  &__about {
    grid-area: sub-about;
  }
  &__userdata {
    grid-area: sub-userdata;
  }

  & > * {
    padding: 10px;
  }
}

// SECTION STYLING //

.main-banner {
  display: inline-block;
  width: 100%;
  color: white;
  background-color: black;
  padding: 0;
  overflow-x: hidden;

  &__title {
    margin: 0;
    font-size: 8rem;
    font-stretch: normal;

    @media (max-width: $sm-break) {
      animation-name: marquee;
      animation-duration: 12s;
      animation-timing-function: linear;
      animation-direction: normal;
      animation-iteration-count: infinite;

      @keyframes marquee {
        0% {
          transform: translateX(calc(100% + 20px))
        }
        100% {
          transform: translateX(calc(-100% - 100vw - 20px))
        }
      }
    }
  }
}

.about-section {
  &__title {

  }
  &__body {
    font-size: 0.8rem;
    line-height: 1.8em;
    opacity: 0.6;
  }
}

.user-data-section {
  &__title {

  }
  &__body {
    font-family: "Cousine", sans-serif; // need to include font
    font-size: 0.8rem;
    line-height: 1.5em;
    opacity: 0.6;
  }
}

// GENRAL CSS CLASSES //

.button {
  padding: 10px 40px 10px 10px;
  margin: 5px 0;
  border: 4px solid black;
  background-color: transparent;
  font-weight: bold;
  text-transform: uppercase;
  text-align: left;
  cursor: pointer;

  &--primairy {
    color: white;
    background-color: black;
  }

  &--icon {
    padding: 10px 12px;
  }

  &:hover {
    background-color:dodgerblue;
  }
}

</style>
