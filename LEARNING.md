# Learning Guide: Introduction to Websites

This guide walks you through the practical exercises for the workshop.
By the end, you will have built and published your first website — a
documentation site made with Material for MkDocs and deployed to
GitHub Pages, with no web hosting to set up and nothing to pay for.

Along the way you will practise writing **Markdown**, the simple text
format used for the README you are reading now, for every page of your
site, and across most of GitHub.

## Step 1: Create your repository

1. Go to https://github.com/ImperialCollegeLondon/RCDS-Intro-to-Websites
2. Click the green **Use this template** button, then **Create a new repository**
3. Give it a name (e.g. `my-first-site`) and set it to **Public**
4. Click **Create repository**

You now have your own copy of the template, including a sample MkDocs
site and a pre-configured GitHub Action to publish it.

## Step 2: Give GitHub Actions permission to publish

Before anything can be deployed, GitHub Actions needs permission to
write to your repository.

1. On your new repository page, click **Settings** (the tab along the top)
2. In the left sidebar, expand **Actions** and click **General**
3. Scroll down to **Workflow permissions**
4. Select **Read and write permissions**
5. Click **Save**

## Step 3: Enable GitHub Pages

Still in your repository settings:

1. In the left sidebar, click **Pages**
2. Under **Build and deployment**, set **Source** to **GitHub Actions**

That's it — the workflow included in the template (`.github/workflows/publish.yml`)
will build your site and deploy it whenever you push to `main`.

## Step 4: Make your first change

Let's change the name of the site.

1. In your repository, click on `mkdocs.yml`
2. Click the pencil icon (**Edit this file**)
3. Change the `site_name:` value from `My Docs` to something of your own
4. Click **Commit changes...**, then **Commit changes** again

Committing to `main` triggers the publish workflow.

### Watch it deploy

1. Click the **Actions** tab at the top of your repository
2. You should see your workflow running — wait for it to finish
   (this usually takes a minute or two)
3. Once it completes with a green tick, go back to **Settings > Pages**
4. You will see a link to your live site, something like:
   `https://your-username.github.io/my-first-site/`

Click the link — your website is now live on the internet. Every time
you push a change to `main`, the site rebuilds and redeploys automatically.

## EXERCISE: Practise Markdown in the README

Edit `README.md` just under the file listing in your repository.
It is full of comments marked with `<!-- ... -->`. These are
invisible in the rendered page but visible in
the editor, and each one suggests a small Markdown improvement to make.

You can edit the file directly on GitHub (the pencil icon) and use the
**Preview** tab to see your changes rendered as you go.

Work through the comments at your own pace. They cover the essentials:

### Emphasis

Surround words with symbols to style them:

```markdown
*italic*  or  _italic_
**bold**
`inline code`
```

### Headings

Prefix a line with hashtags. More hashtags means a deeper level:

```markdown
# Level 1 heading
## Level 2 heading
### Level 3 heading
```

### Ordered lists

Prefix each line with a number and a full stop:

```markdown
1. First step
2. Second step
3. Third step
```

### Unordered lists

Prefix each line with `-` (you can also use `+` or `*`):

```markdown
- An item
- Another item
```

### Task lists

Prefix each line with a hyphen and square brackets (mind the spaces):

```markdown
- [ ] Something to do
- [x] Something already done
```

### Code blocks

Wrap a block in three backticks. You can name the language after the
opening backticks for syntax highlighting:

````markdown
```python
pip install mkdocs-material
```
````

### Links

Square brackets for the text, round brackets for the URL:

```markdown
[Markdown basics](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)
```

### Images

Like a link, but with a leading exclamation point. The square brackets
hold the *alt text* (a description shown if the image can't load):

```markdown
![ECRI banner](docs/assets/ecri-banner.png)
```

When you are happy, commit your changes and check the rendered README
on your repository's front page.

## EXERCISE: Add content to your site

Your site's pages live in the `docs/` folder. The home page is
`docs/index.md`. Everything you practised in the README works here too.

1. Open `docs/index.md` and replace the placeholder text with something
   of your own — a heading, a paragraph, a list.
2. Add a brand-new page by creating another file in `docs/`, for example
   `docs/about.md`. Give it a heading and some content.
3. Commit your changes and watch the Actions tab rebuild the site.
4. Visit your live site to see the new page.

By default, MkDocs builds the navigation automatically from the files in
`docs/`. If you want to control the order and labels yourself, you can add
a `nav:` section to `mkdocs.yml`:

```yaml
nav:
  - Home: index.md
  - About: about.md
```

## Step 5: Work in a Codespace

Everything above can be done in the browser. If you would like to edit
your site with a full editor and a live preview, you can open a
**Codespace** — a development environment that runs in the cloud.

1. On your repository page, click the green **Code** button
2. Switch to the **Codespaces** tab
3. Click **Create codespace on main**

Wait for it to build. The template's devcontainer automatically runs
`pip install mkdocs-material` for you.

Then, in the Codespace terminal, start the live preview server:

```bash
mkdocs serve
```

A notification should offer to open the preview in your browser. As you
edit and save files, the preview reloads automatically. When you are
happy, commit and sync your changes using the Source Control panel in the
left sidebar — and your live site will update.

## Step 6: Have a go with Jekyll

MkDocs is not the only **Static Site Generator** (SSG) — a tool that turns
Markdown into a finished HTML/CSS/JavaScript website. **Jekyll** is another
popular choice, and it works especially well for personal sites and blogs.
The workflow is almost identical to what you have just done with MkDocs, so
it's a great way to see what changes between generators and what stays the same.

We'll use a Jekyll template built around the **Minimal Mistakes** theme.

1. Go to the Jekyll template repository:
   https://github.com/ImperialCollegeLondon/RCDS-jekyll-template
2. Click **Use this template**, then **Create a new repository**
3. Give it a name and set it to **Public**, then **Create repository**

### Configure Pages and Actions

This is exactly the same as for your MkDocs site:

- **Settings > Actions > General > Workflow permissions** → select
  **Read and write permissions** and **Save** (see Step 2)
- **Settings > Pages > Build and deployment** → set **Source** to
  **GitHub Actions** (see Step 3)

### Set your site details

Jekyll's configuration lives in a file called `_config.yml` (the equivalent
of MkDocs' `mkdocs.yml`).

1. Open `_config.yml` in your repository
2. Fill in the `repository:` value with your `username/repository-name`,
   for example `repository: your-username/your-repo-name`
3. While you are there, set `title:` and `email:` to your own details
4. Commit your change — the included GitHub Action will build and publish
   the site, just like before

### Preview it in a Codespace

If you open a Codespace for the Jekyll repository (Step 5), the preview
command is different. Jekyll is a Ruby tool, so in the terminal run:

```bash
bundle exec jekyll serve
```

The Jekyll template's devcontainer runs `bundle install` for you
automatically (where the MkDocs one ran `pip install mkdocs-material`).

To go further, follow the
[Minimal Mistakes theme documentation](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/).

## Step 7: Keep exploring

You have published two real websites, with two different Static Site
Generators. From here you could:

- Keep adding pages and Markdown content to your sites
- Learn more GitHub Flavoured Markdown from
  [GitHub's guide](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)
- Customise the look of your sites by editing `mkdocs.yml` or `_config.yml`
- Move on to the **Further Websites** workshop, which goes deeper into
  Material for MkDocs features: themes, admonitions, diagrams, automatic
  API documentation, and more

This material was developed by the RCDS team at ECRI.

