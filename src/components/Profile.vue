<template>
  <div class="app theme colourway-leaf">
    <section class="main">
      <div class="container app-container">
        <div class="user-area">
          <div class="text-xs-center">
            <span class="img-circle">
              <img
                class="user-img"
                :src="profile.icon"
              >
            </span>
            <h3>
              <a class="user-name btn">@{{ profile.name }}</a>
            </h3> 
            <p
              v-if="profile.description"
              class="user-desc"
            >
              {{ profile.description }}
            </p>
          </div>
        </div>
        <div
          v-for="(link, index) in profile.links"
          :key="index"
          class="links"
        >
          <div class="link">
            <a
              :href="link.url"
              class="btn btn-link"
              :style="style"
            >{{ link.title }}</a>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import axios from "axios";
import data from "../assets/profiles.js"

export default {
  name: 'Profile',
  data () {
    return {
     window: null,
     profile: data[0],
     loading: false,
	 error: null,
	 textColor: "red"
    }
  },
	computed: {
	  style() {
		  return {
			"--color-border": `2px solid ${this.profile.color ? this.profile.color : "#206694"}`,
			"--bg-color": this.profile.color ? this.profile.color : "#206694"
		  }
	  }
  },
  async created() {
	if (window.location.pathname == "/") window.location.href = "/default";
    this.window = window.location;
    const name = window.location.pathname.split("@")[1];
    for (let i = 0; i < data.length; i++) {
      if (data[i].name == name) {
        this.profile = data[i];
      }
    }
    console.log(this.window)
    // this.loading = true;
    // try {
    //   const res = await axios.get("https://jsonplaceholder.typicode.com/users");
    //   this.users = res.data;
    //   console.log(this.data);
    //   this.loading = false;
    // } catch (err) {
    //   this.loading = false;
    //   this.error = "Something went wrong";
    // }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

@import url("https://fonts.googleapis.com/css?family=Source+Code+Pro:400,700");
*,
*:before,
*:after {
	box-sizing: border-box
}

body {
	margin: 0;
	font-family: 'Source Code Pro', monospace;
	font-size: 100%;
	line-height: 1.8
}

a {
	color: #757575
}

a:hover {
	text-decoration: none
}

.inner {
	max-width: 1240px;
	margin: 0 auto;
	padding: 0 20px;
	position: relative
}

@media screen and (max-width: 768px) {
	.inner {
		max-width: initial
	}
}

.marker {
	display: inline-block;
	background: #000;
	color: #fff;
	padding: 0 4px
}

._black .marker {
	background: #fff;
	color: #000
}

hr {
	height: 0;
	border: 0;
	margin: 56px 0;
	box-sizing: content-box;
	overflow: visible;
	border-top: 1px solid #eee
}

._center {
	text-align: center
}

._black {
	background: #000;
	color: #fff
}

.header {
	padding: 80px 0
}

.header p {
	margin: 32px 0 0
}

.header-logo {
	display: inline-block;
	margin: 0;
	padding: 0 8px;
	font-size: 2rem;
	line-height: 1;
	background: #000;
	color: #fff
}

.footer {
	padding: 80px 0
}

.footer .inner {
	display: flex;
	align-items: center
}

.footer .sns {
	display: flex
}

.footer .sns a {
	display: block;
	margin-left: 1em
}

.menu {
	padding: 24px 0;
	background: #000;
	line-height: 1
}

@media screen and (max-width: 768px) {
	.menu {
		padding: 0
	}
}

.menu .inner {
	display: flex
}

@media screen and (max-width: 768px) {
	.menu .inner {
		padding: 0 10px;
		overflow-x: scroll;
		-webkit-overflow-scrolling: touch
	}
}

._center .menu .inner {
	justify-content: center
}

.menu a {
	display: block;
	color: #fff
}

@media screen and (max-width: 768px) {
	.menu a {
		padding: 24px 10px
	}
}

.menu a+a {
	margin: 0 0 0 32px
}

@media screen and (max-width: 768px) {
	.menu a+a {
		margin: 0
	}
}

.section {
	padding: 112px 0
}

@media screen and (max-width: 768px) {
	.section {
		padding: 72px 0
	}
}

.section:nth-child(2n) {
	background: #f5f5f5
}

.section .inner>*:first-child {
	margin: 0
}

.section *+h1,
.section *+h2,
.section *+h3,
.section *+h4,
.section *+h5,
.section *+h6 {
	margin: calc(56px - (((1rem * 1.8) - 1rem) / 2)) auto 0
}

figure {
	max-width: 800px;
	text-align: center;
	margin: calc(56px - (((1rem * 1.8) - 1rem) / 2)) auto 0
}

figure+* {
	margin: calc(56px - (((1rem * 1.8) - 1rem) / 2)) auto 0
}

figure img {
	max-width: 100%;
	max-height: 800px;
	-webkit-filter: grayscale(100%);
	filter: grayscale(100%);
	vertical-align: bottom
}

figure figcaption {
	color: #757575;
	padding-left: 16px;
	border-left: 4px solid #f5f5f5;
	margin-top: 1em;
	text-align: left
}

pre {
	background: #000;
	overflow-x: scroll;
	margin: calc(56px - (((1rem * 1.8) - 1rem) / 2)) auto 0
}

pre+* {
	margin: calc(56px - (((1rem * 1.8) - 1rem) / 2)) auto 0
}

pre code {
	display: block;
	color: #fff;
	font-family: monospace;
	padding: 1em 1.5em
}

.section ul {
	margin: calc(56px - (((1rem * 1.8) - 1rem) / 2)) auto 0
}

blockquote {
	color: #757575;
	padding-left: 16px;
	border-left: 4px solid #f5f5f5;
	margin: calc(56px - (((1rem * 1.8) - 1rem) / 2)) auto 0
}

@font-face {
  font-family: 'Karla';
  font-style: normal;
  font-weight: 400;
  font-display: swap;
  src: local('Karla'), local('Karla-Regular'), url(https://fonts.gstatic.com/s/karla/v8/qkBbXvYC6trAT7RbLtyG5Q.woff2) format('woff2');
  unicode-range: U+0100-024F, U+0259, U+1E00-1EFF, U+2020, U+20A0-20AB, U+20AD-20CF, U+2113, U+2C60-2C7F, U+A720-A7FF;
}
@font-face {
  font-family: 'Karla';
  font-style: normal;
  font-weight: 400;
  font-display: swap;
  src: local('Karla'), local('Karla-Regular'), url(https://fonts.gstatic.com/s/karla/v8/qkBbXvYC6trAT7RVLtw.woff2) format('woff2');
  unicode-range: U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA, U+02DC, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215, U+FEFF, U+FFFD;
}
@font-face {
  font-family: 'Karla';
  font-style: normal;
  font-weight: 700;
  font-display: swap;
  src: local('Karla Bold'), local('Karla-Bold'), url(https://fonts.gstatic.com/s/karla/v8/qkBWXvYC6trAT7zuC8m3xLt3mQ.woff2) format('woff2');
  unicode-range: U+0100-024F, U+0259, U+1E00-1EFF, U+2020, U+20A0-20AB, U+20AD-20CF, U+2113, U+2C60-2C7F, U+A720-A7FF;
}
@font-face {
  font-family: 'Karla';
  font-style: normal;
  font-weight: 700;
  font-display: swap;
  src: local('Karla Bold'), local('Karla-Bold'), url(https://fonts.gstatic.com/s/karla/v8/qkBWXvYC6trAT7zuC8m5xLs.woff2) format('woff2');
  unicode-range: U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA, U+02DC, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215, U+FEFF, U+FFFD;
}

html {
	padding: 0;
	margin: 0;
	-webkit-box-sizing: border-box;
	box-sizing: border-box;
	min-height: 100%
}

body,
h1,
h2,
h3,
h4,
h5,
h6 {
	font-family: Source Code Pro, Helvetica, sans-serif;
	color: #222
}

.container {
	margin-left: auto;
	margin-right: auto;
	padding-left: 10px;
	padding-right: 10px
}

.btn-link,
.btn-link:focus,
.btn-link:hover {
  text-decoration: none;
  font-weight: bold;
  border-radius: 10px;
}

.app.theme.colourway-leaf .btn-link {
	color: #fff;
	border: var(--color-border);
	background-color: var(--bg-color);
	text-align: center;
	position: relative;
	-webkit-transition: all .25s cubic-bezier(.08, .59, .29, .99);
	transition: all .25s cubic-bezier(.08, .59, .29, .99);
	z-index: 2
}

.app.theme.colourway-leaf .btn-link:hover {
	color: var(--bg-color);
	background-color: transparent;
	border-color: var(--bg-color)
}

.app.theme .user-area {
	text-align: center;
	margin-top: 20px;
	padding-top: 15px
}

.app.theme .user-area h3 {
	line-height: 1;
	margin: 0 auto 20px
}

.app.theme .app-container {
	max-width: 700px;
	width: auto
}

.app.theme .img-circle {
	position: relative;
	width: 129px;
	height: 129px;
	display: block;
	background-color: rgba(0, 0, 0, .1);
	margin: 0 auto 10px;
	border-radius: 50%;
	overflow: hidden
}

.app.theme .img-circle img {
	width: 0;
	min-width: 129px;
	min-height: 129px
}

.app.theme .user-name {
	color: #bbb;
	font-size: 1.5rem;
	font-weight: 600;
	border-color: transparent;
	line-height: 1.25;
	text-overflow: ellipsis;
	max-width: 100%;
	display: block;
	overflow: hidden
}

.user-desc {
	color: #bbb;
	font-size: 0.9rem;
	font-weight: 600;
	border-color: transparent;
	line-height: 1.25;
	text-overflow: ellipsis;
	max-width: 100%;
	display: block;
	overflow: hidden
}

.app.theme .link {
	margin-bottom: 16px;
	padding: 0;
	position: relative
}

.app.theme .link a {
	overflow-wrap: break-word;
	word-wrap: break-word;
	word-break: break-word;
	hyphens: auto;
	white-space: normal;
	padding: 15px 20px;
	display: block;
	width: 100%;
	position: relative;
}

.app.theme .link.link-disabled>a {
	border-color: #e5e5e5;
	background-color: #e5e5e5;
	padding: 15px 20px
}

.app section.app-footer {
	position: absolute;
	bottom: 8px;
	left: 0;
	width: 100%;
	padding-bottom: 15px
}

.app section.app-footer h1 {
	position: relative;
	z-index: 100;
	font-size: 0
}

.app section.app-footer h1 .logo {
	background-image: url(https://cdn.pixabay.com/photo/2015/04/23/17/41/javascript-736400_960_720.png);
	background-size: contain;
	background-position: 50%;
	background-repeat: no-repeat;
	display: block;
	width: 150px;
	height: 20px
}

.app section.app-footer a {
	display: inline-block;
	vertical-align: middle
}

.app section.app-footer .app-logo-wrap,
.app section.app-footer .site-logo-wrap {
	margin-left: -10px;
	display: block;
	text-align: center
}

</style>
