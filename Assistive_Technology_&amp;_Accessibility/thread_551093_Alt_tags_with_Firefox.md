---
title: "Alt tags with Firefox"
date: 2007-09-14
forum: Assistive Technology &amp; Accessibility
---

### Post by Cozza on 2007-09-14
Hi :)

I have recently been coding a new website I've been testing it on my Macintosh, my Windows and my new version of Linux 7.04.

I use IE (Yes I know it's useless- but people still use it and I still have to test it), Safari, Opera and Firefox

I've been putting "alt" tags on my images, I've tried my Mac, my Windows and all the browsers, including Firefox.

But for Firefox in Linux they don't show up. Are there any settings I have to change?

Thanks,
Cara x

---

### Post by Ubris on 2007-09-15
Hi Cara

First, pedantry &#8211; "alt" is an attribute, not a "tag" (which I prefer to call elements). :D

I'm not quite sure what you mean by "showing up". I'm going to assume you mean that you expect a tooltip to appear when you hover over the image like IE does. If not, disregard my answer and correct me!

IE's behaviour (at least IE6, I can't speak for 7 - and nor do I care!) goes very much against the [intent of the alt attribute]("http://www.w3.org/TR/1999/REC-html401-19991224/struct/objects.html#h-13.2"), which is that it should provide "alternate text that is rendered when the image cannot be displayed". By displaying it as a tooltip, IE (and others?) is rendering what is intended to be a **substitution** for the image, which is redundant. I suspect it clashes with the title attribute, too, which is appropriately rendered as a hover tooltip (don't have IE to test this and, again, don't care!).

So good luck. [Just describe what the image is]("http://www.w3.org/TR/1999/REC-html401-19991224/struct/objects.html#h-13.8") in the alt attribute, so that:
[LIST]
[*]a user agent (browser etc) not showing it can present a meaningful description, *and/or*
[*]a user not seeing it can be presented a meaningful description.
[/LIST]
(Actually, there are plenty of helpful guides to producing good alt text online - search around or start at [456 Berea Street]("http://www.456bereastreet.com/")).

---

### Post by Cozza on 2007-09-15
My lecturer would kill me if he saw this post now! I mean attribute :rolleyes: #-o

The tool tip does not display when I hover over images. It's an accessibility issue to web users. I've done two modules of this at University but for some reason I can't get them to display :(

:confused:

Cara xx

---

### Post by Ubris on 2007-09-19
I'm sorry - probably wasn't a good idea to post just before going away and offline, hey. :smile:

Thanks for clarifying. If you want tooltips, try the title attribute, but that really is a misuse of the standard even if it provides the effect you (or your lecturer) wants. If your lecturer is telling you that alt attributes not showing up as tooltips is an accessibility issue, then I'd be interested to hear his reasoning, both before and after reading the W3C documentation.

A user who can see a rendered image has *no* issue if its alternative is not rendered visually. He/she will be "consuming" the image (via its alt attribute) in some other way, commonly aurally. If you're providing good alt text, you are doing the right thing and no testing should be necessary. The only way to stay sane is to trust that browsers will do sensible things with standard markup. If they don't, you have to see it as their problem. Really.

Don't just take my word for it, I'm nobody :D:

[LIST]
[*][Alt text is an alternative, not a tooltip]("http://www.456bereastreet.com/archive/200604/alt_text_is_an_alternative_not_a_tooltip/")
[*][Creating Accessible Images - Creating Effective Alternative (alt)Text]("http://www.webaim.org/techniques/images/alt_text.php")
[*][W3C QA tip: Use the alt attribute to describe the function of each visual]("http://www.w3.org/QA/Tips/altAttribute") (and n.b. it also helps searchers)
[/LIST]

I hope that all helps you to rethink your intent. Come on over and join us in the standards camp!

---

