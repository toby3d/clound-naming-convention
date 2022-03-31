<script lang="ts">
	let prefix: string = "";
	let project: string = "";
	let env: string = "";
	let resource: string = "";
	let location: string = "";
	let description: string = "";
	let suffix: string = "";
</script>

<h1>Cloud Naming Convention</h1>

<label>
	Fixed prefix
	<input
		type="text"
		name="prefix"
		bind:value={prefix}
		minlength="3"
		maxlength="3"
		placeholder="ste"
		required
	/>
</label>

<label>
	Project name
	<input
		type="text"
		name="project"
		bind:value={project}
		minlength="4"
		maxlength="10"
		pattern="a-z0-9"
		placeholder="blog"
		required
	/>
</label>

<label>
	Environment
	<select name="env" bind:value={env}>
		<option value="d">development</option>
		<option value="s">staging</option>
		<option value="p">production</option>
	</select>
</label>

<label>
	Resource type
	<input
		type="text"
		name="resource"
		bind:value={resource}
		size="3"
		pattern="a-z"
		placeholder="kcl"
		required
	/>
</label>

<label>
	Resource location
	<input
		type="text"
		name="location"
		bind:value={location}
		minlength="1"
		maxlength="6"
		pattern="a-z0-9"
		placeholder="euwe1a"
	/>
</label>

<label>
	Additional description
	<input
		type="text"
		name="description"
		bind:value={description}
		minlength="1"
		maxlength="20"
		pattern="a-z0-9"
		placeholder="backend"
	/>
</label>

<label>
	Random suffix
	<input
		type="text"
		name="suffix"
		bind:value={suffix}
		size="4"
		pattern="a-z0-9"
		placeholder="a49f"
	/>
</label>

<h2>Global Naming Pattern</h2>
<input
	type="text"
	value="{prefix}-{project}-{env}-{resource}-{location}-{description}-{suffix}"
	size="64"
	readonly
/>

<h2>GCP Projects</h2>
<input
	type="text"
	value="{prefix}-{project}-{env}-{suffix}"
	size="64"
	readonly
/>

<h2>Exceptions</h2>
<h3>Service Accounts</h3>
<input
	type="text"
	value="{resource}-{description}@{prefix}-{project}-{env}-{suffix}.iam.gserviceaccount.com"
	size="64"
	readonly
/>

<h2>DNS</h2>
<input
	type="text"
	value="{resource}-{location}-{description}-{suffix}.{project}-{env}.example.com"
	size="64"
	readonly
/>
