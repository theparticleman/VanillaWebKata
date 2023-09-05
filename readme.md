# Introduction

In web development these days, we tend to use a lot of frameworks and libraries and dependencies. But it all eventually just turns into Javascript, HTML, and CSS. 

Did you know that you can create a full web site with just HTML, CSS, and Javascript without using any frameworks or anything? This used to be a pretty bad option, but in our modern web development world it can be a surprisingly effective choice.

In this kata we will create an interactive web page using only vanilla HTML, CSS, and Javascript. We will be using the [Mega Man Quotes API](https://megamanquotes.com/api) to get data to display.

# Getting Started
Start by creating a file named `index.html`. You can use any text editor to edit the file.

Every HTML page starts with an `<html>` tag. Inside the `<html>` tag there should be a `<head>` tag and a `<body>` tag. Start by making your `index.html` file look like this:

``` html
<html>
    <head></head>
    <body></body>
</html>
```

You can open your `index.html` file in a web browser. At this point it will just be a blank page, but should open properly.

# Add Some Content

Blank pages aren't very interesting. Let's add some content. All of our content should go inside the `<body>` tag.

Let's add a title to our page. Add an `<h1>` tag with the title of our page. Something like this: `<h1>Sofware Crafting Quotes</h1>`. 

Since we're going to be using the Mega Man Quotes API, let's mention that. Add a `<p>` tag mentioning Mega Man Quotes. Something like this: `<p>Powered by Mega Man Quotes<p>`.

This really is the header for our page, so let's put it all in a `<header>` tag. This isn't strictly necessary, but it will help screen readers and other accessibility tools make sense of our page.

``` html
<header>
    <h1>Software Crafting Quotes</h1>
    <p>Powered by Mega Man Quotes</p>
</header>
```

In addition to our header, let's add the main content for our page. Let's put this content inside a `<main>` tag. Again, this isn't strictly necessary, but will help with accessibility.

For now let's just put a single button inside our `<main>` tag.

The HTML for our entire page should look something like this:

``` html
<html>
<head></head>
<body>
    <header>
        <h1>Software Crafting Quotes</h1>
        <p>Powered by Mega Man Quotes</p>
    </header>
    <main>
        <button>Find a quote</button>
    </main>
</body>

</html>
```

If you open your `index.html` file in a web browser now, some content (our heading, subheading, and button) should show up. It won't look very pretty. We'll fix that later.

# A Note On Caching

Depending on your browser and operating system, your web site files might be getting cached. If you make changes to your web site files but those changes aren't showing up in your browser, try clearing your browser cache. 

To do this in Chrome, open the developer tools, then right click on the refresh button and choose "Empty cache and hard refresh". Other browsers may have slightly different methods for clearing their cache.

# Making Things Less Ugly

We have some content on our page, but it isn't very pretty yet. Let's fix that now.

HTML is used to create content and structure for a web page. CSS is used to create styling (i.e. the looks) for a web page.

There are several options (inline, internal, and external) for how to add CSS to a web page. For this kata we will use an external file to define our CSS.

Create a new file named `site.css`. It should be in the same directory as your `index.html` file.

In order to use the CSS styles we'll define in our HTML file, we need to create a link between our HTML file and our CSS file.

To do this add a `<link>` tag inside the `<head>` tag in your HTML file. The `<link>` tag will need two attributes. The first is a `rel` attribute with the value of `stylesheet`. The second is an `href` attribute with the value of `site.css`.

After adding the `<link>` tag, your entire `index.html` file should like something like this:

``` html
<html>
<head>
    <link rel="stylesheet" href="site.css">
</head>
<body>
    <header>
        <h1>Software Crafting Quotes</h1>
        <p>Powered by Mega Man Quotes</p>
    </header>
    <main>
        <button>Find a quote</button>
    </main>
</body>

</html>
```

# CSS And Selectors And Styles! Oh, My!

CSS files have styles which determine what different HTML elements look like. They also have selectors that determine which elements different styles should get applied to.

Let's start by adding a style that applies to the `<body>` tag. Add the following selector and style to your `site.css` file:

``` css
body {
    display: flex;
    flex-direction: column;
    align-items: center;
    background-color: black;
    color: white;
}
```

The selector (`body`) says that this style applies to any `<body>` tag in our HTML (we only have one). The style then specifies that the `<body>` tag is in flexbox column mode. 

If you're not familiar with how flexbox works, [Flexbox Froggy](https://flexboxfroggy.com/) is a great introduction.

The `align-items` property in the style specifies that everything inside the `<body>` tag should be centered horizontally. I picked a `background-color` of `black` and a `color` (which changes the text color) of `white`. Feel free to choose your own colors.

Let's add one more style. Add the following block to your `site.css` file:

``` css
header {
    display: flex;
    flex-direction: column;
    align-items: center;
}
```

This style sets our `<header>` tag to also be in flexbox column mode and have its contents centered horizontally.

Our entire `site.css` file should now look something like this:

``` css
body {
    display: flex;
    flex-direction: column;
    align-items: center;
    background-color: black;
    color: white;
}

header {
    display: flex;
    flex-direction: column;
    align-items: center;
}
```

# Adding Some Behavior

Now let's add some behavior to our web page. We'll do this using Javascript. Like with CSS, there are several options for how to add Javascript to our web page. For this kata we'll use a `<script>` tag in our HTML file.

In your `index.html` file, at the bottom of the `<body>` tag (right after the `<main>` tag) add a `<script>` tag. Inside the `<script>` tag add a definition for a new function named `buttonClick`. For now, inside the `buttonClick` function, just add a `console.log("button clicked")` line.

To make this code get called when the user actually clicks on the button, add an `onclick` attribute to the `<button>` tag up in the `<main>` section. Give the attribute a value of `buttonClick()`.

The entire `index.html` file should look something like this:

``` html
<html>
<head>
    <link rel="stylesheet" href="site.css">
</head>
<body>
    <header>
        <h1>Software Crafting Quotes</h1>
        <p>Powered by Mega Man Quotes</p>
    </header>
    <main>
        <button onclick="buttonClick()">Find a quote</button>
    </main>
    <script>
        function buttonClick() {
            console.log("button clicked")
        }
    </script>
</body>
</html>
```

Try out these changes to make sure some text gets printed out when you click the button. You'll need to have the developer tools open and the console visible to see the output.

# Calling An API

Printing to the console is great for debugging, but we want to do something more interesting. Let's call an API to get some data to show on our page.

As previously mentioned, we'll be calling the [Mega Man Quotes API](https://megamanquotes.com/api) to get our data. Specifically, we'll be calling the `random-quote` endpoint to get a random quote to display.

In our `buttonClicked` function, delete the `console.log` line. Replace it with a call to `fetch`. The version of the  `fetch` function we're going to use takes one argument, a URL. For our URL use `https://api.megamanquotes.com/random-quote`.

The `fetch` function is promise-based. Let's add an `await` when we call it. We will also need to make the `buttonClick` function `async` for this to work.

Store the result of the call to `fetch` in a variable named `response`. On a subsequent line, call `response.json()` and assign the result to a new variable named `quote`. The call to `.json()` is also promise-based, so this call will need an `await` as well.

On a third line, let's print out the quote that we got. The whole `buttonClick` function should look something like this.

``` javascript
async function buttonClick() {
    const response = await fetch("https://api.megamanquotes.com/random-quote")
    const quote = await response.json()
    console.log("quote: ", quote)
}
```

Test this new functionality in your browser. A quote and some information about it should get printed out to the console every time you click the button.

# Putting Content On The Page

Now, rather than printing out information to the console, let's actually put it on our page. Go ahead and delete the `console.log` line in the `buttonClick` function.

First, we need somewhere to put our content. Let's add a `<div>` tag to our `<main>` tag before our `<button>`. Give the `<div>` an id of `quote`.

In the `buttonClick` function, after getting the quote from the response, add a line to find the quote `<div>`. Call `document.getElementById("quote")` and store the result in a variable called `quoteDiv`.

To make sure that we only show one quote at a time, start by removing any existing content our quote `<div>` may have. To do this, add a subsequent line, `quoteDiv.innerHTML = ""`.

Now let's add a new `<div>` tag to show the text of the quote. Call `document.createElement("div")` and assign its results to a variable named `quoteText`. On subsequent lines, give the `<div>` a class with the line `quoteText.classList.add("quote-text")`, then set the contents of the `<div>` with the line `quoteText.textContent = quote.text`, then add our new `<div>` to our main `<div>` named `quoteDiv` with the line `quoteDiv.appendChild(quoteText)`.

At this point the entire `buttonClick` function should look like this:

``` javascript
async function buttonClick() {
    const response = await fetch("https://api.megamanquotes.com/random-quote")
    const quote = await response.json()
    console.log("quote: ", quote)
    const quoteDiv = document.getElementById("quote")
    quoteDiv.innerHTML = ""
    const quoteText = document.createElement("div")
    quoteText.classList.add("quote-text")
    quoteText.textContent = quote.text
    quoteDiv.appendChild(quoteText)
}
```

Feel free to test this new functionality out in your browser. When you click the button, the text for a quote should appear on the page (you shouldn't have to open the console or developer tools to see the behavior anymore).

# Add More Quote Info

Let's add the rest of the information about the quote. We're going to add two more `<div>` elements, one for the quote author and another for the source.

Just like for the `<div>` for the quote text, create a new `<div>` element, give it a class, set its `textContent`, and call `appendChild` to add it to the `quoteDiv`. Do this once for the quote author, giving it the class of `quote-author`, and once for the quote source, giving it the class of `quote-source`.

The entire `buttonClick` function should look something like this:

``` javascript
const response = await fetch("https://api.megamanquotes.com/random-quote")
const quote = await response.json()
console.log("quote: ", quote)
const quoteDiv = document.getElementById("quote")
quoteDiv.innerHTML = ""

const quoteText = document.createElement("div")
quoteText.classList.add("quote-text")
quoteText.textContent = quote.text
quoteDiv.appendChild(quoteText)

const quoteAuthor = document.createElement("div")
quoteAuthor.classList.add("quote-author")
quoteAuthor.textContent = quote.author
quoteDiv.appendChild(quoteAuthor)

const quoteSource = document.createElement("div")
quoteSource.classList.add("quote-source")
quoteSource.textContent = quote.source
quoteDiv.appendChild(quoteSource)
```

Again, try it out in your browser. Now each time you click the button you should get the quote text, author, and source (though not all quotes have a source).

# Pretty Things Up

We should have dynamic data displaying on the page at this point. Unfortunately, it doesn't look very good. Let's add some more CSS styles to make it look better.

Add a CSS style for the `<main>` tag so that it is using flexbox column mode and so that its children are centered horizontally. Also give it a `gap` of `16px`.

Create another CSS style for the `quote` id to use flexbox column and center its children horizontally. On the style for `quote`, also set the `font-family` property to `sans-serif` and the `gap` property to `8px`.

Let's also add some styles to the different parts of the quote. Create a style for the `quote-text` class with `font-size` set to `xx-large` and `text-align` set to `center`. Create another style for the `quote-source` class with the `font-size` set to `x-small`.

The four new styles in your `site.css` file should look something like this:

``` css
main {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 16px;
}

#quote {
    font-family: sans-serif;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 8px;
}

.quote-text {
    font-size: xx-large;
    text-align: center;
}

.quote-source {
    font-size: x-small;
}
```

A quick reminder that a "plain" selector (like for `main`) applies to an HTML tag. A selector that starts with `#` (like for `#quote`) applies to an element with that id. A selector that starts with a `.` (like for `.quote-text`) applies to an element with that class.

# What Does It All Look Like?

Your entire `index.html` file should now look something like this:

``` html
<html>
<head>
    <link rel="stylesheet" href="site.css">
</head>
<body>
    <header>
        <h1>Software Crafting Quotes</h1>
        <p>Powered by Mega Man Quotes</p>
    </header>
    <main>
        <div id="quote"></div>
        <button onclick="buttonClick()">Find a quote</button>
    </main>
    <script>
        async function buttonClick() {
            const response = await fetch("https://api.megamanquotes.com/random-quote")
            const quote = await response.json()
            console.log("quote: ", quote)
            const quoteDiv = document.getElementById("quote")
            quoteDiv.innerHTML = ""

            const quoteText = document.createElement("div")
            quoteText.classList.add("quote-text")
            quoteText.textContent = quote.text
            quoteDiv.appendChild(quoteText)

            const quoteAuthor = document.createElement("div")
            quoteAuthor.classList.add("quote-author")
            quoteAuthor.textContent = quote.author
            quoteDiv.appendChild(quoteAuthor)

            const quoteSource = document.createElement("div")
            quoteSource.classList.add("quote-source")
            quoteSource.textContent = quote.source
            quoteDiv.appendChild(quoteSource)
        }
    </script>
</body>
</html>
```

Your entire `site.css` file should look something like this:

``` css
body {
    display: flex;
    flex-direction: column;
    align-items: center;
    background-color: black;
    color: white;
}

header {
    display: flex;
    flex-direction: column;
    align-items: center;
}

main {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 16px;
}

#quote {
    font-family: sans-serif;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 8px;
}

.quote-text {
    font-size: xx-large;
    text-align: center;
}

.quote-source {
    font-size: x-small;
}
```

# Conclusion

While not the correct choice for every project, hopefully this kata showed you that at least for some projects, vanilla HTML, CSS, and Javascript can be a viable option (and potentially much simpler than large front-end frameworks).

# Going Above And Beyond

If you got through this entire kata and would like some additional challenges, here are a few ideas on how the kata could be expanded. They are in no particular order. Feel free to anywhere between none and all of them.

* Do you like the styles we ended up with? Try making your own styles to give your website a different look.
* There are other endpoints in the Mega Man Quotes API besides the one to get a random quote (check the [documentation page](https://megamanquotes.com/api)). Add a way to use these other endpoints to your web page.
* The code to add the `<div>` tags for the different parts of the quote is very similar. Remove the duplication.
* Try implementing the quote as a [web component](https://www.webcomponents.org/introduction).
* Put the Javascript that gets executed when the button is pressed in an external `.js` file instead of in a script tag.
* If you put the Javascript in a separate file, can you add tests for it?
* There is a fair amount of duplication in the `site.css` file. Can you reduce it? Does it make sense to?
* Use your browser's mobile testing tools to see how your web site might look on a mobile device. Does it look good? Can you make it look better?
* Your browser may give you some warnings about your web page as it is currently implmented. Can you find these warnings? How many can you fix? Are there any you don't think you should fix?
* Deploy your web page somewhere public facing. Some easy deployment methods include an AWS S3 bucket, an Azure Storage Account, and GitHub pages, though there are many other options as well.