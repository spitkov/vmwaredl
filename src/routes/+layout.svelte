<script>
	import '../app.css';
	import { page } from '$app/stores';
	import { onMount } from 'svelte';
	let { children } = $props();
	
	const name = "spitkov";
	const description = "home";
	const email = "bence@spitkov.hu";
	const github = "spitkov";
	
	const pageTitle = $derived(
		$page.url.pathname === '/' 
			? name + ' | ' + description 
			: name + ' | ' + $page.url.pathname.substring(1)
	);
	
	function scrollToTop() {
		window.scrollTo({ top: 0, behavior: 'auto' });
	}
	
</script>

<svelte:head>
	<title>{pageTitle}</title>
	<meta name="description" content="{description}" />
</svelte:head>

<div class="min-h-screen bg-transparent text-[#ffffff] font-mono p-4 flex flex-col content-container">
	<div class="max-w-2xl mx-auto w-full flex flex-col flex-grow items-center">
		
		<main class="pb-8 flex-grow">
			{@render children()}
		</main>
		
		<footer class="mt-auto pt-6 w-full">
			<div class="border-t border-[#333333] w-full mb-6"></div>
			<div class="flex justify-between items-center text-xs text-[#777777] pb-4">
				<button 
					on:click={() => window.location.href = 'https://github.com/spitkov/vmwaredl'} 
					class="text-[#71A5B9] cursor-pointer hover:cursor-pointer"
				>
					github.com/spitkov/vmwaredl
				</button>
			</div>
		</footer>
	</div>
</div>
