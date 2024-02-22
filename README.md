# Vardhaman College of Engineering -- IPR Cell Website

- [Table of Contents](#vardhaman-college-of-engineering----ipr-cell-website)
   * [Local Development and Usage Guidelines](#local-development-and-usage-guidelines)
      + [Pre Requistes](#pre-requistes)
      + [Setting up a local instance for improving this theme](#setting-up-a-local-instance-for-improving-this-theme)
      + [Config files](#config-files)
      + [Custom front matter](#custom-front-matter)
               + [Hide the page title / article header](#hide-the-page-title--article-header)
      + [Custom shortcodes ](#custom-shortcodes)
         - [Button](#button)
         - [Cards](#cards)
         - [Columns](#columns)
         - [Current Year](#current-year)
         - [iFrame](#iframe)
         - [Img](#img)
         - [Linebreak](#linebreak)
         - [Responsive Table](#responsive-table)
         - [Spacer](#spacer)
         - [Table of Contents (TOC)](#table-of-contents-toc)
         - [YouTube Enhanced](#youtube-enhanced)

## Local Development and Usage Guidelines

### Pre Requistes

- [Node.js](https://nodejs.org/en/download)
- [Hugo Framework](https://gohugo.io/getting-started/quick-start/)
- [Git](https://git-scm.com/)
- [Github Account](github.com) to commit changes
- [Visual Studio Code](https://code.visualstudio.com/) or your favourite IDE

### Setting up a local instance for improving this theme

To run in your local system follow below commands

```zsh
git clone https://github.com/vce-cse-dept/ipr-cell
cd ipr-cell
npm install
npm run start
```

### Config files

See /exampleSite/config/ for example configuration files.

You should copy these across or merge them with your existing config.

### Custom front matter

We have created custom front matter to use in your markdown files:

###### Hide the page title / article header

```
showHeader: false
```

### Custom shortcodes 

You can use our custom shortcodes to quickly style your website in markdown. Due to the way Hugo deals with nested content, particularly nested shortcodes, you may find that shortcodes that are children of other shortcodes do not render as they should. If this happens to your site, this can often be resolved by allowing Hugo to [render "unsafe" HTML](https://gohugo.io/getting-started/configuration-markup/#goldmark). Add the following to your config YAML file:

```yaml
markup:
  goldmark:
    renderer:
      unsafe: true
```

#### Button

There is a button ready to be inserted in to markdown files:

```md
{{< button link="/path/to/page" text="Default Button" >}}
```
```md
{{< button link="/path/to/page" style="secondary" text="Secondary Button" >}}
```
```md
{{< button link="/path/to/page" style="tertiary" text="Tertiary Button" >}}
```

Options:
- link # (required) the button link
- text # (required) the button text
- style # (optional) secondary, tertiary

#### Cards

An outlined box that is useful for highlighting information or using to wrap list elements.

```
{{< cards count=2 >}}
{{< card >}}
### Special Feature 1
Lorem ipsum dolor sit amet consectetuer adipiscing elit aenean commodo
{{< spacer >}}
[Download](#)
{{< /card >}}
{{< card >}}
### Special Feature 2
Lorem ipsum dolor sit amet consectetuer adipiscing elit aenean commodo
{{< spacer >}}
[About us](#)
{{< /card >}}
{{< /cards >}}
```

Options:
- count # (optional) number of columns on desktop; 2,3,4. Default: 3.

#### Columns

A responsive column structure.

```
{{< columns >}}
{{< column >}}
Column 1
{{< /column >}}
{{< column >}}
Column 2
{{< /column >}}
{{< /columns >}}
```

Options:
- count # (optional) number of columns on desktop; 2,3,4. Default: 3.

#### Current Year

Insert the current year easily with this shortcode:

```
{{< current_year >}}
```

Useful for copyright notices and evergreen blog content.

#### iFrame

Insert an iFrame with your desired content.

```
{{< iframe title="My slides" src="https://www.slideshare.net/slideshow/embed_code/key/vTNvkwIXN4pmr8" >}}
```

Options:
- src # (required) the page to display
- width # (optional)
- height # (optional)
- title # (optional) the title of the iframe for accessibility
- loading # (optional) defaults to lazy

#### Img

Inserts an image in a more advanced format than standard Hugo syntax.

```
{{< img src="/img/blog/image-name.png" >}}
```

Options: 
- src # (required) the image link
- alt # (optional) describing the image, defaults to filename
- width # (optional) recommended 
- height # (optional) recommended
- caption # (optional) markdown is accepted
- loading # (optional) defaults to lazy, use eager above the fold

#### Linebreak

Sometimes markdown can bunch paragraphs together. You can force a line return using the linebreak shortcode.

```
{{< br >}}
```

#### Responsive Table

Wrap your large tables with this shortcode so they overflow on mobile:

```
{{< responsive_table >}}
| Option | Option | Description |
| ------ | ------ | ----------- |
| one    | data   | path to data files to supply the data that will be passed into templates. |
| two    | engine | engine to be used for processing templates. Handlebars is the default. |
| three  | ext    | extension to be used for dest files. |
{{< /responsive_table >}}
```

#### Spacer

A spacer is useful for spacing out content on your page. By default our spacer inserts a 50px height space. Our spacer is responsive, so on mobile devices the value is reduced by 50% (i.e. 50px space becomes 25px space).

```
{{< spacer >}}
```
```
{{< spacer 100 >}}
```

#### Table of Contents (TOC)

Insert a Table of Contents automatically in to your page. Picks up on all H2 elements on the page.

```
{{< toc >}}
```

#### YouTube Enhanced

A privacy friendly and fast YouTube embed.

```
{{< youtube_enhanced id="9oVr7rrNZVI" >}}
```

For embedding playlists, a singular video id must be mentioned as playlists do not have a thumbnail.

```
{{< youtube_enhanced id="xPSXtoJNGLs" title="Play Videos from Kubecon" playlistid="PLj6h78yzYM2PyrvCoOii4rAopBswfz1p7" >}}
```

Options:
- id # (required)
- title # (optional) defaults to Play Video
- playlistid # (optional) your playlist ID
- autoload # (optional) defaults to false
- start # (optional) the start time in seconds, default 0