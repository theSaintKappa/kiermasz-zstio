<script lang="ts">
    import { blur } from 'svelte/transition';
    import Footer from './lib/Footer.svelte';
    import Header from './lib/Header.svelte';
    import DasboardPanels from './lib/admin/DasboardPanels.svelte';
    import Landing from './lib/customer/Landing.svelte';
    import { user, writingDisabled } from './stores';
</script>

<Header />
<main>
    {#if $user}
        <DasboardPanels />
    {:else}
        <Landing />
    {/if}
</main>
<Footer />
{#if $writingDisabled && $user}
    <div>Wprowadzanie zmian zostało wyłączone</div>
{/if}

<style>
    main {
        width: 100%;
        display: flex;
        justify-content: center;
    }

    div {
        position: fixed;
        bottom: 0.5rem;
        font-size: clamp(1rem, 4vw, 2.25rem);
        font-weight: 700;
        opacity: 0.45;
        color: var(--warning-color);
        pointer-events: none;
    }
</style>
