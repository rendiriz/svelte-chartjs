<svelte:options tag="rendikit-chartjs-bar" />

<script lang="typescript">
  import { onMount } from 'svelte'

  import cssVars from 'svelte-css-vars'
  import { Color } from 'rendikit-theme'

  import Chart from 'chart.js/auto'

  $: styleMain = {
    white: Color.Normal('white')
  }

  let canvas: any

  onMount(() => {
    const ctx = canvas.getContext('2d')
    var myChart = new Chart(ctx, {
      type: 'bar',
      data: {
        labels: ['Red', 'Blue', 'Yellow', 'Green', 'Purple', 'Pink'],
        datasets: [
          {
            label: '# of Votes',
            data: [12, 19, 3, 5, 2, 3],
            backgroundColor: [
              Color.Normal('R400'),
              Color.Normal('B400'),
              Color.Normal('Y400'),
              Color.Normal('G400'),
              Color.Normal('P400'),
              Color.Normal('PK400')
            ],
            borderWidth: 1
          }
        ]
      },
      options: {
        aspectRatio: 2,
        responsive: true,
        maintainAspectRatio: true,
        scales: {
          y: {
            beginAtZero: true
          }
        }
      }
    })
  })
</script>

<div use:cssVars={styleMain}>
  <canvas bind:this={canvas} />
</div>

<style lang="scss">
  @import 'tailwindcss/base';
  @import 'tailwindcss/components';
  @import 'tailwindcss/utilities';

  div {
    @apply relative p-1;

    canvas {
      @apply w-screen;
      height: 350px;
    }
  }
</style>
