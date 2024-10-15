<script lang="ts">
  import { Button } from "$lib/components/ui/button";
  import "swiper/css";
  import "swiper/css/navigation";
  import "swiper/css/pagination";
  import "swiper/css/scrollbar";
  import Swiper from "swiper";
  import { Navigation, Pagination, Scrollbar } from "swiper/modules";
  import type { ButtonEventHandler } from "bits-ui";

  // swiper element
  let swiper: Swiper | null = null;

  const spaceBetween = 10;
  const onProgress = (e: any) => {
    console.log("progress", e);
    const [swiper, progress] = e.detail;
    console.log(progress);
  };
  const onSlideChange = (e: any) => {
    console.log("slide changed", e);
  };

  const onClick = (e: ButtonEventHandler<MouseEvent>) => {
    console.log("clicked", swiper);
  };

  function mountSwiper(swiperEl: HTMLDivElement) {
    swiper = new Swiper(swiperEl, {
      modules: [Navigation, Pagination, Scrollbar],
      navigation: {
        nextEl: ".swiper-button-next",
        prevEl: ".swiper-button-prev",
      },
      pagination: true,
      scrollbar: true,
      autoplay: {
        delay: 2500,
        disableOnInteraction: false,
      },
      slidesPerView: 1,
      spaceBetween: 10,
      loop: true,
    });
  }
</script>

<h1>Welcome to SvelteKit</h1>
<p>
  Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation
</p>
<Button on:click={onClick} size="sm">Click me</Button>

<!-- Slider main container -->
<div class="swiper w-[500px] h-[400px]" use:mountSwiper>
  <!-- Additional required wrapper -->
  <div class="swiper-wrapper">
    <!-- Slides -->
    <div class="swiper-slide bg-slate-400">Slide 1</div>
    <div class="swiper-slide bg-slate-400">Slide 2</div>
    <div class="swiper-slide bg-slate-400">Slide 3</div>
    <div class="swiper-slide bg-slate-400">Slide 4</div>
    <div class="swiper-slide bg-slate-400">Slide 5</div>
    <div class="swiper-slide bg-slate-400">Slide 6</div>
    <div class="swiper-slide bg-slate-400">Slide 7</div>
    <div class="swiper-slide bg-slate-400">Slide 8</div>
    <div class="swiper-slide bg-slate-400">Slide 9</div>
  </div>

  <div
    class="swiper-button-next absolute top-1/2 left-0 w-4 h-4 z-10 bg-slate-200"
  ></div>
  <div
    class="swiper-button-prev absolute top-1/2 right-0 w-4 h-4 z-10 bg-slate-200"
  ></div>
</div>
<!-- If we need pagination -->
<div class="swiper-pagination bg-gray-600 w-[100px] h-[30px]"></div>

<!-- If we need scrollbar -->
<div class="swiper-scrollbar w-[200px] h-[40px]"></div>
