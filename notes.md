## Mobile Viewport

There are a few different options that you can use with the [`viewport` meta
tag](https://docs.google.com/present/view?id=dkx3qtm_22dxsrgcf4 "Viewport and
Media Queries - The Complete Idiot's Guide"). You can find out more in [the MDN
Web
Docs](https://developer.mozilla.org/en-US/docs/Mozilla/Mobile/Viewport_meta_tag).
HTML5 Boilerplate comes with a simple setup that strikes a good balance for
general use cases.

```html
<meta name="viewport" content="width=device-width, initial-scale=1" />
```

If you want to take advantage of edge-to-edge displays of iPhone X/XS/XR you
can do so with additional viewport parameters. [Check the WebKit
blog](https://webkit.org/blog/7929/designing-websites-for-iphone-x/) for
details.

## Open Graph Metadata

The [Open Graph Protocol](https://ogp.me/) allows you to define the way your
site is presented when referenced on third party sites and applications
(Facebook, Twitter, LinkedIn). The protocol provides a series of meta elements
that define the details of your site. The required attributes define the title,
preview image, URL, and [type](https://ogp.me/#types) (e.g., video, music,
website, article).

```html
<meta property="og:title" content="" />
<meta property="og:type" content="" />
<meta property="og:url" content="" />
<meta property="og:image" content="" />
```

In addition to these four attributes there are many more attributes you can use
to add more richness to the description of your site. This just represents the
most basic implementation.

To see a working example, the following is the open graph metadata for the HTML5
Boilerplate site. In addition to the required fields we add `og:description` to
describe the site in more detail.

```html
<meta name="og:url" content="https://html5boilerplate.com/" />
<meta name="og:title" content="HTML5 ★ BOILERPLATE" />
<meta name="og:type" content="website" />
<meta
  name="og:description"
  content="The web’s most popular front-end template which helps you build fast, robust, and adaptable web apps or sites."
/>
<meta name="og:image" content="https://html5boilerplate.com/icon.png" />
```

## Search

### Direct search spiders to your sitemap

After creating a [sitemap](https://www.sitemaps.org/protocol.html)

Submit it to search engine tool:

- [Google](https://www.google.com/webmasters/tools/sitemap-list)
- [Bing](https://www.bing.com/toolbox/webmaster)
- [Yandex](https://webmaster.yandex.com/)
- [Baidu](https://zhanzhang.baidu.com/) OR Insert the following line anywhere in
  your robots.txt file, specifying the path to your sitemap:

```
Sitemap: https://example.com/sitemap_location.xml
```

### Hide pages from search engines

According to Heather Champ, former community manager at Flickr, you should not
allow search engines to index your "Contact Us" or "Complaints" page if you
value your sanity. This is an HTML-centric way of achieving that.

```html
<meta name="robots" content="noindex" />
```

**_WARNING:_** DO NOT INCLUDE ON PAGES THAT SHOULD APPEAR IN SEARCH ENGINES.

## Miscellaneous

- Use [Microformats](http://microformats.org/wiki/Main_Page) (via
  [microdata](http://microformats.org/wiki/microdata)) for optimum search
  results
  [visibility](https://webmasters.googleblog.com/2009/05/introducing-rich-snippets.html).

- If you want to disable the translation prompt in Chrome or block Google
  Translate from translating your web page, use [`<meta name="google"
content="notranslate">`](https://support.google.com/webmasters/answer/79812).
  To disable translation for a particular section of the web page, add
  [`class="notranslate"`](https://support.google.com/translate/?hl=en#2641276).

- If you want to disable the automatic detection and formatting of possible
  phone numbers in Safari on iOS, use [`<meta name="format-detection"
content="telephone=no">`](https://developer.apple.com/library/archive/documentation/AppleApplications/Reference/SafariHTMLRef/Articles/MetaTags.html).

- Avoid development/stage websites "leaking" into SERPs (search engine results
  page) by [implementing X-Robots-tag
  headers](https://github.com/h5bp/html5-boilerplate/issues/804).

## News Feeds

## Social Networks

### Facebook Open Graph data

You can control the information that Facebook and others display when users
share your site. Below are just the most basic data points you might need. For
specific content types (including "website"), see [Facebook's built-in Open
Graph content
templates](https://developers.facebook.com/docs/sharing/opengraph/using-objects).
Take full advantage of Facebook's support for complex data and activity by
following the [Open Graph
tutorial](https://developers.facebook.com/docs/sharing/webmasters/getting-started).

For a reference of Open Graph's markup and properties, you may check [Facebook's
Open Graph Protocol reference](https://ogp.me). Finally, you can validate your
markup with the [Facebook Object
Debugger](https://developers.facebook.com/tools/debug/) (needs registration to
Facebook).

```html
<meta property="og:url" content="https://www.example.com/path/to/page.html" />
<meta property="og:type" content="website" />
<meta property="og:title" content="" />
<meta property="og:image" content="https://www.example.com/path/to/image.jpg" />
<meta property="og:description" content="" />
<meta property="og:site_name" content="" />
<meta property="article:author" content="" />
```

### Schema.org

Google also provides a snippet specification that serves a similar purpose to
Facebook's Open Graph or Twitter Cards. This metadata is a subset of
[schema.org's microdata vocabulary](https://schema.org/), which covers many
other schemas that can describe the content of your pages to search engines. For
this reason, this metadata is more generic for SEO, notably for Google's
search-engine, although this vocabulary is also used by Microsoft, Pinterest and
Yandex.

You can validate your markup with the [Structured Data Testing
Tool](https://search.google.com/structured-data/testing-tool). Also, please
note that this markup requires to add attributes to your top `html` tag.

```html
<html class="no-js" lang="" itemscope itemtype="https://schema.org/Article">
  <head>
    <link rel="author" href="" />
    <link rel="publisher" href="" />
    <meta itemprop="name" content="" />
    <meta itemprop="description" content="" />
    <meta itemprop="image" content="" />
  </head>
</html>
```

## URLs

### Canonical URL

Signal to search engines and others "Use this URL for this page!" Useful when
parameters after a `#` or `?` is used to control the display state of a page.
`https://www.example.com/cart.html?shopping-cart-open=true` can be indexed as
the cleaner, more accurate `https://www.example.com/cart.html`.

```html
<link rel="canonical" href="" />
```

### Separate mobile URLs

If you use separate URLs for desktop and mobile users, you should consider
helping search engine algorithms better understand the configuration on your web
site.

This can be done by adding the following annotations in your HTML pages:

- on the desktop page, add the `link rel="alternate"` tag pointing to the
  corresponding mobile URL, e.g.:

  `<link rel="alternate" media="only screen and (max-width: 640px)"
href="https://m.example.com/page.html" >`

- on the mobile page, add the `link rel="canonical"` tag pointing to the
  corresponding desktop URL, e.g.:

  `<link rel="canonical" href="https://www.example.com/page.html">`

For more information please see:

- https://developers.google.com/search/mobile-sites/mobile-seo/separate-urls

## Web Apps

There are a couple of meta tags that provide information about a web app when
added to the Home Screen on iOS:

- Adding `apple-mobile-web-app-capable` will make your web app chrome-less and
  provide the default iOS app view. You can control the color scheme of the
  default view by adding `apple-mobile-web-app-status-bar-style`.

```html
<meta name="apple-mobile-web-app-capable" content="yes" />
<meta name="apple-mobile-web-app-status-bar-style" content="black" />
```

- You can use `apple-mobile-web-app-title` to add a specific sites name for the
  Home Screen icon.

```html
<meta name="apple-mobile-web-app-title" content="" />
```

For further information please read the [official
documentation](https://developer.apple.com/library/archive/documentation/AppleApplications/Reference/SafariHTMLRef/Articles/MetaTags.html)
on Apple's site.

### Apple Touch Icons

Apple touch icons are used as icons when a user adds your webapp to the home
screen of an iOS devices.

Though the dimensions of the icon can vary between iOS devices and versions one
`180×180px` touch icon named `icon.png` and including the following in the
`<head>` of the page is enough:

```html
<link rel="apple-touch-icon" href="icon.png" />
```

For a more comprehensive overview, please refer to Mathias' [article on Touch
Icons](https://mathiasbynens.be/notes/touch-icons).

### Apple Touch Startup Image

Apart from that it is possible to add start-up screens for web apps on iOS. This
basically works by defining `apple-touch-startup-image` with an according link
to the image. Since iOS devices have different screen resolutions it maybe
necessary to add media queries to detect which image to load. Here is an example
for an iPhone:

```html
<link
  rel="apple-touch-startup-image"
  media="(max-device-width: 480px) and (-webkit-min-device-pixel-ratio: 2)"
  href="img/startup.png"
/>
```
