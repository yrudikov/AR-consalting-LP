<script>
	import { page } from '$app/stores';
	import content from '$lib/content.json';

	export let title = content.site.title; // "AR Consulting"
	export let description = content.site.description;
	export let keywords =
		'consulting, doradztwo biznesowe, optymalizacja, AI, IT, logistyka, transport, sprzedaż, pricing, tworzenie stron www';
	export let image = '/img/logo-consulting.png';
	export let type = 'website';
	export let canonical = $page.url.href;

	const structuredData = {
		"@context": "https://schema.org",
		"@type": "ProfessionalService",
		"name": title,
		"description": description,
		"image": canonical + image,
		"url": canonical,
		"telephone": content.contact.content[1].text,
		"address": {
			"@type": "PostalAddress",
			"addressLocality": content.contact.content[0].text
		},
		"email": content.contact.content[2].text,
		"priceRange": "$$"
	};
</script>

<svelte:head>
	<title>{title} – Twój niezawodny partner w świecie biznesu i konsultingu</title>
	<meta name="description" content={description} />
	<meta name="keywords" content={keywords} />
	<link rel="canonical" href={canonical} />

	<!-- Open Graph -->
	<meta property="og:type" content={type} />
	<meta property="og:url" content={canonical} />
	<meta property="og:title" content={title} />
	<meta property="og:description" content={description} />
	<meta property="og:image" content={image} />

	<!-- Twitter -->
	<meta property="twitter:card" content="summary_large_image" />
	<meta property="twitter:url" content={canonical} />
	<meta property="twitter:title" content={title} />
	<meta property="twitter:description" content={description} />
	<meta property="twitter:image" content={image} />

	<!-- JSON-LD -->
	<script type="application/ld+json">
		{JSON.stringify(structuredData)}
	</script>
</svelte:head>
