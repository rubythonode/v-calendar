<template>
<section id='setup' class='section'>
  <div class='container'>
    <b-message type='is-warning'>
      <a href='https://vuejs.org' target='_blank'>Vue.js</a> version <strong>2.4.2+</strong> is required.
    </b-message>
    <article class='media'>
      <div class='media-left'>
        <p class='title is-5'>1</p>
      </div>
      <div class='media-content'>
        <p class='title is-5'>Select method</p>
      </div>
    </article>
    <b-tabs type='is-toggle' class='offset'>
      <b-tab-item label='Use NPM'>
        <article class='media'>
          <div class='media-left'>
            <p class='title is-5'>2</p>
          </div>
          <div class='media-content'>
            <p class='title is-5'>Install</p>
          </div>
        </article>
        <code-block lang='javascript' code='npm install v-calendar' offset></code-block>
        <article class='media'>
          <div class='media-left'>
            <p class='title is-5'>3</p>
          </div>
          <div class='media-content'>
            <p class='title is-5'>Import into your project</p>
          </div>
        </article>
        <code-block lang='javascript' :code='importCode | pre' offset></code-block>
        <article class='media'>
          <div class='media-left'>
            <p class='title is-5'>4</p>
          </div>
          <div class='media-content'>
            <p class='title is-5'>Reference in your component templates</p>
          </div>
        </article>
        <code-block :code='componentCode | pre' offset></code-block>
      </b-tab-item>
      <b-tab-item label='Use CDN'>
        <article class='media'>
          <div class="media-left">
            <p class="title is-5">2</p>
          </div>
          <div class="media-content">
            <p class="title is-5">Load external resources</p>
          </div>
        </article>
        <code-block :code='cdnHtml | pre' offset></code-block>
      </b-tab-item>
    </b-tabs>
  </div>
</section>
</template>

<script>
import cdnHtml from '!!raw-loader!../index-cdn.html';

export default {
  data() {
    return {
      setupOption: 'npm',
      importCode: `
        import Vue from 'vue';
        import VCalendar from 'v-calendar';
        import 'v-calendar/lib/v-calendar.min.css';

        // Access v-calendar, v-date-packer and v-popover components
        Vue.use(VCalendar);`,
      componentCode: `
        <template>
          <v-calendar
            is-double-paned>
          </v-calendar>
          <v-date-picker
            mode='single'
            v-model='mySelection'>
          </v-date-picker>
        </template>`,
      cdnHtml,
    };
  },
  computed: {
    npmSelected() {
      return this.setupOption === 'npm';
    },
    cdnSelected() {
      return this.setupOption === 'cdn';
    },
  },
};
</script>

<style lang='sass' scoped>

.offset
  margin-top: 20px

.b-tabs
  .tabs
    margin-left: 20px

</style>
