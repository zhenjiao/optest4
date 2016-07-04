# Markdown, Extensions, and HTML code

## <a id="Top"> </a>1. Markdown flavor
Docfx supports "Docfx Flavored Markdown," (DFM). It is 100% compatiable with Github Flavored Markdown, and adds some additional functionality, including cross reference and file inclusion.

## 2. Getting started with Markdown

Here are two great tutorials for Markdown and GitHub Flavored Markdown:

- [Introduction to Markdown by John Gruber](http://daringfireball.net/projects/markdown/syntax)
- [GitHub Flavored Markdown](https://help.github.com/articles/github-flavored-markdown/)

## 3. Markdown editor
You can use any Markdown editor you would like to edit Markdown. Some suggestions: [MarkdownPad](http://markdownpad.com/), [Visual Studio Code](https://www.visualstudio.com/en-us/products/code-vs.aspx), [Markdown Mode](https://visualstudiogallery.msdn.microsoft.com/0855e23e-4c4c-4c82-8b39-24ab5c5a7f79). 

Most of them provide live preview functionality so that you can get a simple preview when writing the topic.

## 4. Markdown extensions supported by Open Publishing
The following contains the list of supported extensions in Open Publishing. 

### 4.1 File Include
You can include other file into the current file; the included file will also be configured in DFM syntax. 

#### NOTE
> [!NOTE]
> YAML header is **NOT** supported when the file is an inclusion.

There are three types of file inclusion: inline, block, and image.

#### 4.1.1 Inline
Inline file inclusion is in the following syntax, in which `<title>` stands for the title of the included file, and `<filepath>` stands for the file path of the included file; the file path can be either an absolute file path or a relative file path.`<filepath>` can be wrapped by `'` or `"`. Note that for inline file inclusion, the file included will be considered as containing only inline tags, e.g. `###header` inside the file will not be transformed because `<h3>` is a block tag, while `[a](b)` will be transformed to `<a href='b'>a</a>` because `<a>` is an inline tag.
```
...Other inline content... [!include[<title>](<filepath>)]
```

#### 4.1.2 Block
Block file inclusion must be in a single line and with no prefix characters before the start `[`. Content inside the included file will be transformed using DFM syntax.

```md
[!include[<title>](<filepath>)]
```
#### 4.1.3 Images
The syntax to include an image is `![[name]]({folderPath})` Example: `![Introduction](..\images\Introduction.png)`

### 4.2 Notes: Note, Warning, Tip, Important, Caution
Use specific syntax inside a block quote to indicate that the content following is a Note.

```
> [!NOTE]
> This is a NOTE

> [!WARNING]
> This is a WARNING

> [!TIP]
> This is a TIP

> [!IMPORTANT]
> This is IMPORTANT

```

And it will render like:

> [!NOTE]
> This is a NOTE

> [!WARNING]
> This is a WARNING

> [!TIP]
> This is a TIP

> [!IMPORTANT]
> This is IMPORTANT

### 4.3 Anchor links
Anchor links allow you to go to a section of a specific topic. 

Use the following syntax for the header you would like to link to:

`## <a id="AnchorText"> </a> Header text`

And the following for the link to it:

`Go to [text](#AnchorText)`

Example:
Go to [top](#Top)

### 4.4 Section definition
A user may need to define a section. This is mostly used for code tables.
See the following example.

````
> [!div class="tabbedCodeSnippets" data-resources="OutlookServices.Calendar"]
> ```cs
> <cs code text>
> ```
> ```javascript
> <js code text>
> ```
````

The preceding blockquote markdown text will render as:
> [!div class="tabbedCodeSnippets" data-resources="OutlookServices.Calendar"]
> ```cs
> <cs code text>
> ```
> ```javascript
> <js code text>
> ```

### 4.5 Code snippets
See [Code snippets page](codesnippets.md).

### 4.6 Metadata
See [Metadata page](metadata.md).

### 4.7 Selector
Selector can be used when partner would like to connect different pages for the same topic and allow user to switch between those topics. 
> [!NOTE]
> This extension works different between docs.microsoft.com and MSDN 

#### 4.7.1 Single Selector
```
> [!div class="op_single_selector"]
- [Universal Windows](../articles/notification-hubs-windows-store-dotnet-get-started/)
- [Windows Phone](../articles/notification-hubs-windows-phone-get-started/)
- [iOS](../articles/notification-hubs-ios-get-started/)
- [Android](../articles/notification-hubs-android-get-started/)
- [Kindle](../articles/notification-hubs-kindle-get-started/)
- [Baidu](../articles/notification-hubs-baidu-get-started/)
- [Xamarin.iOS](../articles/partner-xamarin-notification-hubs-ios-get-started/)
- [Xamarin.Android](../articles/partner-xamarin-notification-hubs-android-get-started/)
```
And it will render like
> [!div class="op_single_selector"]
- [Universal Windows](../index.md)
- [Windows Phone](../index.md)
- [iOS](../index.md)
- [Android](../index.md)
- [Kindle](../index.md)
- [Baidu](../index.md)
- [Xamarin.iOS](../index.md)
- [Xamarin.Android](../index.md)

### 4.7.2 Multi Selector
```
> [!div class="op_multi_selector" title1="Platform" title2="Backend"]
- [(iOS | .NET)](./mobile-services-dotnet-backend-ios-get-started-push.md)
- [(iOS | JavaScript)](./mobile-services-javascript-backend-ios-get-started-push.md)
- [(Windows universal C# | .NET)](./mobile-services-dotnet-backend-windows-universal-dotnet-get-started-push.md)
- [(Windows universal C# | Javascript)](./mobile-services-javascript-backend-windows-universal-dotnet-get-started-push.md)
- [(Windows Phone | .NET)](./mobile-services-dotnet-backend-windows-phone-get-started-push.md)
- [(Windows Phone | Javascript)](./mobile-services-javascript-backend-windows-phone-get-started-push.md)
- [(Android | .NET)](./mobile-services-dotnet-backend-android-get-started-push.md)
- [(Android | Javascript)](./mobile-services-javascript-backend-android-get-started-push.md)
- [(Xamarin iOS | Javascript)](./partner-xamarin-mobile-services-ios-get-started-push.md)
- [(Xamarin Android | Javascript)](./partner-xamarin-mobile-services-android-get-started-push.md)
```
And it will render like 
> [!div class="op_multi_selector" title1="Platform" title2="Backend"]
- [(iOS | .NET)](../index.md)
- [(iOS | JavaScript)](../index.md)
- [(Windows universal C# | .NET)](../index.md)
- [(Windows universal C# | Javascript)](../index.md)
- [(Windows Phone | .NET)](../index.md)
- [(Windows Phone | Javascript)](../index.md)
- [(Android | .NET)](../index.md)
- [(Android | Javascript)](../index.md)
- [(Xamarin iOS | Javascript)](../index.md)
- [(Xamarin Android | Javascript)](../index.md)

## 5. Resolve file path

 1. Relative path (path like foo/bar.md) is the path relative to the file where this path is written, which means in file include case, it’s relative to the included file. For example, we have A.md includes B.md, B.md has a relative path in it. Then that path is relative to B.md instead A.md.
 2. Relative path will be resolved during build (remove .md extension), and generate build warning if target file doesn’t exist.
 3. You can use “../” to link to file in parent folder, but that file has to be in the same docset. You cannot use “../” to link to a file in another docset folder.
 4. We also support a special form of relative path which starts with ~ (for example, ~/foo/bar.md), which means a file relative to the root folder of a docset. This kind of path will also be validated and resolved during build.
 5. Besides markdown link and image, you can also use relative path in html link (<a>) and image (<img>).
 6. Absolute path (path starts with /) means a path in the output website. We don’t process absolute path and leave it as-is in output html. This means if you use absolute path, you need to add the base url and remove the .md extension by yourself.

## 6. HTML whitelist

You can embed HTML code into your content, as long as it is within the GitHub WhiteLlist. **We also enable iframe element for video embedding even though it is not in the GFM whitelist**. HTML rendered by the various markup language processors gets passed through an [HTML sanitization filter](https://github.com/jch/html-pipeline/blob/master/lib/html/pipeline/sanitization_filter.rb) for security reasons. HTML elements not in the whitelist are removed. HTML attributes not in the whitelist are removed from the preserved elements.

The following HTML elements, organized by category, are whitelisted:

Type  |Elements  
---------|---------
Headings     |  h1, h2, h3, h4, h5, h6    
Prose     |  p, div, blockquote       
Formatted     |   pre      
Inline     |     b, i, strong, em, tt, code, ins, del, sup, sub, kbd, samp, q, var    
Lists     |   ol, ul, li, dl, dt, dd      
Tables     | table, thead, tbody, tfoot, tr, td, th        
Breaks     |   br, hr      
Ruby (East Asian)     |   ruby, rt, rp      
Video (not in GFM whitelist)    |  iframe
Comments | Comments

The following attributes, organized by element, are whitelisted:

Element  |Attributes  
---------|---------
a     |      href (http://, https://, mailto://, github-windows://, and github-mac:// URI schemes and relative paths only)   
iframe |  src, allowFullScreen, frameBorder, scrolling
img     |     src (http:// and https:// URI schemes and relative paths only)    
div     |     itemscope, itemtype    
All     |     abbr, accept, accept-charset, accesskey, action, align, alt, axis, border, cellpadding, cellspacing, char, charoff, charset, checked, cite, clear, cols, colspan, color, compact, coords, datetime, dir, disabled, enctype, for, frame, headers, height, hreflang, hspace, ismap, label, lang, longdesc, maxlength, media, method, multiple, name, nohref, noshade, nowrap, prompt, readonly, rel, rev, rows, rowspan, rules, scope, selected, shape, size, span, start, summary, tabindex, target, title, type, usemap, valign, value, vspace, width, itemprop    

Note that the id attribute is not whitelisted.

