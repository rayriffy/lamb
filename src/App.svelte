<script lang="ts">
	import { Github } from '@svicons/boxicons-logos'

	let mainElement: HTMLElement
	let lambElement: HTMLAudioElement
	let sauceElement: HTMLAudioElement

	let timeoutId: number

	const onMouseDown = () => {
		lambElement.currentTime = 0

		if (timeoutId) clearTimeout(timeoutId)

		if (!sauceElement.paused) sauceElement.pause()

		mainElement.setAttribute('class', 'lamb')

		lambElement.play()
	}

	const onMouseUp = () => {
		sauceElement.currentTime = 0

		if (!lambElement.paused) lambElement.pause()

		mainElement.setAttribute('class', 'sauce')

		sauceElement.play()

		timeoutId = setTimeout(() => {
			mainElement.removeAttribute('class')
		}, 1000)
	}
</script>

<main
	bind:this={mainElement}
	on:mousedown={onMouseDown}
	on:mouseup={onMouseUp}
/>

<audio bind:this={lambElement} src="/av/lamb.mp3" />
<audio bind:this={sauceElement} src="/av/sauce.mp3" />

<a class="source" href="https://github.com/rayriffy/lamb">
	<Github />
</a>
