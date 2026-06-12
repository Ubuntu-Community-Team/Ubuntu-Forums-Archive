---
title: "Colour of visited links especially in Firefox/Google"
date: 2011-01-12
forum: Assistive Technology &amp; Accessibility
---

### Post by grey1beard on 2011-01-12
My wife is using Ubuntu 10.10 on her laptop, and her macular degeneration is such as to make unvisited and visited links in Firefox/Google both appear to be brown.
Not helpful !
Is there any way to change one or other of the colours ?

I realize that web pages normally set this as part of their coding, but I wondered if there was a workaround that I could set up for her ?

Many thanks for any suggestions,
John

---

### Post by sisco311 on 2011-01-12
In Firefox you can change the color of visited/unvisited links under:

Edit -> Preferences -> Content -> Colors... -> Link Colors

---

### Post by grey1beard on 2011-01-12
Many many thanks.
I looked under Tools, but not finding anything tried Google and spent too long "chasing wild geese" ;)
John

---

### Post by sisco311 on 2011-01-12
You're welcome!

---

### Post by grey1beard on 2011-01-13
While my thanks to sisco311 were appropriate, I have since discovered that altering the link colour is only available at the expense of losing the background colours of each web page.
While it does solve the stated problem, it's not really the solution I was looking for.
Perhaps I'm just going to have to accept that there is no solution.:(
I've "unsolved" the thread for the time being, just in case someone else has another idea to try.

John

---

### Post by Mopquill on 2011-01-22
Install the Firefox add-on [Stylish]("https://addons.mozilla.org/en-US/firefox/addon/stylish/").

Once you've restarted Firefox, look in your "add-on bar" or your status bar if you're not using the 4.0 beta. You should see the outline of a white "S" in a white box. Right-click that, and select Write New Style > Blank Style (If you're using the beta, the standard context menu will come up over stylish's- just hit esc to see what we're looking for).

Name it "Google" or something, and paste this in:

```
@namespace url(http://www.w3.org/1999/xhtml);

@-moz-document domain("www.google.com") {
a:visited {color:#0F0!important;}
}
```...replacing #F0F with the hex code for a color she can see, if lime doesn't work. I figured if she can't see blue or purple completely, the cones/rods she's having trouble with would likely be the reds and blues, so, I picked green, as that's the only other one. You can also add in a line like so:

```
a:link,a:hover,a:active {color:#F0F!important;}
```directly below the a:visited... line to pick a color for links to be normally. I picked magenta for that, as it's the direct opposite of lime, but, that might just be brown to her.

I hope this helps. =]

---

### Post by grey1beard on 2011-01-22
Thanks Mopquill.
Before I start by trying it out on my own system, is that a fix that will work just for your example of the Google site, or does it become more "global" ?
It is mainly the search engine where such an extra bit of info becomes important, so a global solution isn't really necessary.
Thanks again
John

---

### Post by Mopquill on 2011-01-22
I did [www.google.com](www.google.com), as they usually have subdomains for their separate services (e.g. translate.google.com). However, anything that starts with [www.google.com](www.google.com) will undergo the same changes.

It's really easy to toggle it though, you just click the S, and click the checked style. Same thing to re-check it. They have "per-url" feature, but, as Google doesn't have a specific page it's going to, just options, I wouldn't know how to trigger it without wildcards, which I don't know that it supports.

Anyhow, it's not global per se, just for [www.google.com](www.google.com) - most of which, if I'm not mistaken, is centralized around searching, with maybe the exception of Google Voice.

---

