---
sidebarDepth: 0
---

# Contributing

This project is powered by [VuePress](https://vuepress.vuejs.org/guide/), therefore contributing couldn't be any easier. The idea of this project is to cement my learning by _attempting_ to provide explanations of several topics encompassing the JavaScript language.

Contribution is always appreciated, as this project could later help someone else who is going through the process of Bootcamp, or self-study.

## Local Development

Clone the repo into your desired folder and `cd` into it, then install the dependencies.

```bash
git clone https://github.com/sanctumlysis/bootcamp-notes.git
cd bootcamp-notes
npm ci
```

Once npm has finished installing all of the dependencies, navigate your way through into the `/docs/notes` directory, where you will find several folders, each folder will have multiple `.md` files within, these are the individual note pages which [VuePress](https://vuepress.vuejs.org/miscellaneous/design-concepts.html) compiles into HTML.

To start-up the development server, you can type the following command into your terminal:

```bash
npm run dev
```

This will compile the `.md` files into HTML and open up a local version of the site at [http://localhost:8080](http://localhost:8080) for you to navigate as you develop your pages.

## Adding Pages

To add a new page, create a `page-name.md` file in the folder of your choosing. For example, if you wanted to create a page which details how to use promises, your directory should look something like `/notes/async/promises.md`. This allows [VuePress](https://vuepress.vuejs.org/theme/default-theme-config.html#sidebar) to pick up on it and set up the routing, however, you will still need to add the directory to the `sidebar.js` located within the `/docs/.vuepress/` directory.

For the promises example, the corresponding code for `sidebar.js` should look like the code below.

```js{8-13}
{
    title: "Notes",
    collapsable: false,
    path: "/notes/",
    sidebarDepth: 8,
    children: [
      {
          title: "Async",
          collapsable: true,
          path: "/notes/async/",
          children: [
              "/notes/async/promises.md"
          ]
      }
}
```

## Formatting

VuePress comes with a lot of handy [extensions](https://vuepress.vuejs.org/guide/markdown.html) which you can use to prettify your markdown-driven web-pages, while also supporting the standard markdown syntax which you're probably used to. Code-snippets and containers can be used to provide the reader with context.

### Tips, warnings, and danger messages

Likewise, if you have a tip to share with the reader, you can format them in a specific way so that it is more noticeable and appealing – the same applies to warnings and 'danger' messages.

**Example code:**

```
In this section, we will be doing something!

::: tip <label or name>
This is useful for the reader.
:::

::: warning Encapsulation!
Make sure you're correctly encapsulating these with the ':' markers
:::

::: danger Markers!
If you do not, they may not work and will make your webpage look messy.
:::
```

**Output:**
::: tip
This is useful for the reader.
:::

::: warning Encapsulation!
Make sure you're correctly encapsulating these with the ':' markers
:::

::: danger Markers!
If you do not, they may not work and will make your webpage look messy.
:::

## Linting

Prior to committing, please lint your code, it makes all of our lives easier if we all follow one linting structure, to make things easier, you can just run the following command in your CLI prior to pushing any changes.

```bash
npm run lint
```

The linter set up for this is prettier and it will lint every file which has been altered when that command is run.

## Deploying

Once you're finished with all of your changes, follow the normal `git commit` process and then open a [pull request](https://github.com/sanctumlysis/bootcamp-notes/pulls) detailing what you have added. The rest will be handled by the GitHub workflow, which will automatically compile and push changes to the `gh-pages` branch when the merge is successful.
