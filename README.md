# netlify-cli [beta]
[![npm version][npm-img]][npm] [![build status][travis-img]][travis] [![windows build status][av-img]][av]
[![coverage][coverage-img]][coverage] [![dependencies][david-img]][david] [![downloads][dl-img]][dl]

Welcome to the Netlify CLI! The new 2.0 version (now in beta) was rebuilt from the ground up to help improve the site building experience.

## Table of Contents

<!-- AUTO-GENERATED-CONTENT:START (TOC:collapse=true&collapseText=Click to expand) -->
<details>
<summary>Click to expand</summary>

- [Install & Setup](#install--setup)
- [Usage](#usage)
- [Getting Started](#getting-started)
  * [Link to an existing site](#link-to-an-existing-site)
  * [Create a new site](#create-a-new-site)
  * [Deploying a site](#deploying-a-site)
  * [Production Deploys](#production-deploys)
- [Full Command Reference](#full-command-reference)
  * [deploy](#deploy)
  * [init](#init)
  * [link](#link)
  * [login](#login)
  * [logout](#logout)
  * [open](#open)
  * [sites](#sites)
  * [status](#status)
  * [unlink](#unlink)
  * [watch](#watch)
  * [telemetry](#telemetry)
- [Local Development](#local-development)

</details>
<!-- AUTO-GENERATED-CONTENT:END -->

## Install & Setup

**Prerequisites**

- [Node.js](https://nodejs.org/en/download/) 8+.
- [Netlify User Account](http://app.netlify.com/)

To install the Netlify CLI, run the following command in your terminal window:

```sh-session
npm install netlify-cli@next -g
```

After installing the CLI globally, connect the CLI to your Netlify account with the following command:

```sh-session
netlify login
```

This will open a browser window, asking you to log in with Netlify and grant access to **Netlify CLI**. This will store your Netlify access token in your home folder, under `~/.netlify/config.json`.

## Usage

```sh-session
netlify [command]

# Run `help` for detailed information about CLI commands
netlify [command] help
```

## Getting Started

[Netlify's continuous deployment](https://www.netlify.com/docs/continuous-deployment) will automatically deploy new versions of your site when you push commits to your connected Git repository.

To setup continuous deployment with the CLI, run:

```sh-session
netlify init
```

In order to connect your repository for continuous deployment, Netlify CLI will need access to create a deploy key and a webhook on the github repository. When you run the command above, you'll be prompted to log in to your GitHub account, which will create an account-level access token.

The access token will be stored in your home folder, under `.netlify/config.json`. Your login password will never be stored. You can revoke the access token at any time from your GitHub account settings.


### Link to an existing site

Linking to a site tells Netlify CLI which site the current directory should deploy to. To do this, run the following command from the base of your project directory:

```sh-session
netlify link
```

This will add a `siteId` field to a new file inside your project folder, at `.netlify/state.json`. To unlink your folder from the site, you can remove this field, or you can run the following command from inside the project folder:

```sh-session
netlify unlink
```


### Create a new site

To create a new Netlify site with the CLI, run the `netlify init` command in your site folder.

```sh-session
netlify init
```

Then Choose "Create & configure a new site in Netlify"

Proceed through the prompts to finish configuring your site.

### Deploying a site

It's also possible to deploy a site manually, without continuous deployment. This method uploads files directly from your local project directory to your site on Netlify.

A common use case for this command is when you're using a separate Continuous Integration (CI) tool, deploying prebuilt files to Netlify at the end of the CI tool tasks.

**To do a manual deployment with the CLI run:**

```sh-session
netlify deploy

# Optionally pass in the build directory
netlify deploy --dir your-build-directory

# Deploying to production with --prod flag
netlify deploy --dir your-build-directory --prod
```

This `deploy` command needs to know which folder to publish, and if your project includes functions, a functions folder to deploy. It will look for this information in three places, in the following order:

* in flags specified in the command itself
* in a [netlify.toml file](https://www.netlify.com/docs/netlify-toml-reference) stored at the base of your project directory.
* in your site settings in the Netlify UI.


### Production Deploys

By default, all `deploys` are set to a draft preview URL.

To do a manual deploy to production, use the `--prod` flag:

```sh-session
# Deploy build folder to production
netlify deploy --prod

# Shorthand -p
netlify deploy -p
```

Deploying to production will publish the build directory at the live URL of your Netlify site.

## Full Command Reference

<!-- AUTO-GENERATED-CONTENT:START (GENERATE_COMMANDS_LIST) -->
### [deploy](/docs/commands/deploy.md)

Create a new deploy from the contents of a folder

### [init](/docs/commands/init.md)

Configure continuous deployment for a new or existing site

### [link](/docs/commands/link.md)

Link a local repo or project folder to an existing site on Netlify

### [login](/docs/commands/login.md)

Login to your Netlify account

### [logout](/docs/commands/logout.md)

Logout of your Netlify account

### [open](/docs/commands/open.md)

Open settings for the site linked to the current folder

| Subcommand | description  |
|:--------------------------- |:-----|
| [`open:admin`](/docs/commands/open.md#openadmin) | Opens current site admin UI in Netlify  |
| [`open:site`](/docs/commands/open.md#opensite) | Opens current site url in browser  |


### [sites](/docs/commands/sites.md)

Handle various site operations

| Subcommand | description  |
|:--------------------------- |:-----|
| [`sites:create`](/docs/commands/sites.md#sitescreate) | Create an empty site (advanced)  |
| [`sites:list`](/docs/commands/sites.md#siteslist) | List all sites you have access too  |


### [status](/docs/commands/status.md)

Print status information

| Subcommand | description  |
|:--------------------------- |:-----|
| [`status:hooks`](/docs/commands/status.md#statushooks) | Print hook information of the linked site  |


### [unlink](/docs/commands/unlink.md)

Unlink a local folder from a Netlify site

### [watch](/docs/commands/watch.md)

Watch for site deploy to finish


<!-- AUTO-GENERATED-CONTENT:END -->

### telemetry

By default, the CLI collects usage stats from logged in Netlify users. This is to constantly improve the developer experience of the tool and bake in better features.

If you'd like to opt out of sending telemetry data, you can do so with the `--telemetry-disable` flag

```sh-session
# opt out of telemetry
netlify --telemetry-disable

# turn on telemetry
netlify --telemetry-enable
```

Or edit the `telemetryDisabled` property of the `~/.netlify/config.json` file in your computers root directory.


# Local Development

1. Clone down the repo

```sh-session
$ git clone git@github.com:netlify/cli.git
```

2. Install dependencies

```sh-session
$ npm install
```

3. Run CLI locally during development

```sh-session
$ ./bin/run [command]
```

When developing, you can use watch mode which will automatically run ava tests:

```sh-session
$ npm run watch
```
[npm-img]: https://img.shields.io/npm/v/netlify-cli.svg
[npm]: https://npmjs.org/package/netlify-cli
[travis-img]: https://img.shields.io/travis/netlify/cli/master.svg
[travis]: https://travis-ci.org/netlify/cli
[av-img]: https://ci.appveyor.com/api/projects/status/imk2qjc34ly7x11b/branch/master?svg=true
[av]: https://ci.appveyor.com/project/netlify/cli
[dl-img]: https://img.shields.io/npm/dm/netlify-cli.svg
[dl]: https://npmjs.org/package/netlify-cli
[coverage-img]: https://img.shields.io/coveralls/netlify/cli/master.svg
[coverage]: https://coveralls.io/github/netlify/cli
[david-img]: https://david-dm.org/netlify/cli/status.svg
[david]: https://david-dm.org/netlify/cli
