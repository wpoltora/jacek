<template>
  <StylishHeader title="JACEK STYRCZULA" subtitle="portfolio"/>
  <SideNav :active="activeSection" />
  <div id="about-me" class="section">
    <AboutMe />
  </div>
  <div id="photography" class="section">
    <h2 class="projects-heading">{{$t('strings.navPhotography')}}</h2>
    <CustomCarousel class="custom-carousel photo-carousel" photoList='portfolio'/> 
  </div>
  <div id="films" class="section">
    <h2 class="projects-heading">{{$t('strings.navFilm')}}</h2>
    <iframe width="100%" src="https://www.youtube.com/embed/HIhFx3KNW40?si=S0DoOFSQYR9489e-" 
    title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" 
    referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
    <iframe width="100%" src="https://www.youtube.com/embed/Uumkgz4jC-0?si=L_5wdJaRjIh8qpvg" 
    title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" 
    referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
    <iframe width="100%" src="https://www.youtube.com/embed/ldbSTaw5RpY?si=aVByPz-g0GmvKAdJ" 
    title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" 
    referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
  </div>
  <div id="music" class="section">
    <h2 class="projects-heading">{{$t('strings.navMusic')}}</h2>
    <iframe width="100%" src="https://www.youtube.com/embed/9rHHa61gWSw?si=JzSkWIWWWKIQSqeG" 
    title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" 
    referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
  </div>
  <div id="contact-me" class="section">
    <ContactMe />
  </div>
</template>


<script>
import StylishHeader from './components/StylishHeader.vue'
import AboutMe from './components/AboutMe.vue'
import SideNav from './components/SideNav.vue';
import ContactMe from './components/ContactMe.vue';
import CustomCarousel from './components/CustomCarousel.vue'

export default {
  name: 'App',
  components: {
    StylishHeader,
    AboutMe,
    SideNav,
    ContactMe,
    CustomCarousel,
  },
  data() {
    return {
      activeSection: '',
    };
  },
  mounted() {
    window.addEventListener('scroll', this.onScroll);
    this.onScroll(); // Ensure correct section is active on load
  },
  beforeUnmount() {
    window.removeEventListener('scroll', this.onScroll);
  },
  methods: {
    onScroll() {
      const sections = document.querySelectorAll('.section');
      let scrollPosition = window.scrollY + window.innerHeight / 2; // Middle of the viewport

      sections.forEach((section) => {
        const rect = section.getBoundingClientRect();
        const sectionTop = window.scrollY + rect.top;
        const sectionBottom = sectionTop + section.offsetHeight;

        if (scrollPosition >= sectionTop && scrollPosition <= sectionBottom) {
          this.activeSection = section.id;
        }
      });
    },
  },
}
</script>

<style>
html{
  scroll-padding-top: 30vh;
}

#app {
  font-family: 'Roboto', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: white;
  margin-top: 60px;
}

body{
  background-color:black;
}

a {
  color: inherit;
  text-decoration: none;
  outline: none;
}

.project-dp{
  margin-top: 4em;
}

#projects, #photography{
  max-width: 1000px;
  justify-self: center;
  margin-top: 2em;
}

#films, #music{
  max-width: 1000px;
  justify-self: center;
  width:100%;
}

#films iframe, #music iframe{
  aspect-ratio: 16 / 9; 
  width: 100%;
  margin-bottom: 6em;
}



.projects-heading{
        width: fit-content;
        text-align: start;
        box-shadow: 10px 10px var(--primary);
        margin-bottom: 3em;
        margin-top: 3em;
        padding-right: 7px;
        font-size: 2em;
}

.section{
  margin-top: 6em;
}

.stylish-header{
  transition: 0.5s;
}

.photo-carousel .carousel__track{
  height: 800px;
}

@media screen and (max-width: 1400px) {
      .stylish-header{
        margin-top: 7em;
        transition: 0.5s;
      }
}

@media screen and (max-width: 820px) {
      .stylish-header .line{
        display: none;
      }
}


@media screen and (max-width: 1000px) {
  body{
    margin-left: 20px;
    margin-right: 20px;
  }
}

@media screen and (max-width: 768px) {
  body{
    font-size: 0.8em;
  }
}
</style>
