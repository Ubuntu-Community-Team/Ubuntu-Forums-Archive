---
title: "Effectively embedding fonts in a webpage"
date: 2010-02-17
forum: Art &amp; Design
---

### Post by WebDrake on 2010-02-17
Hello all,

I've been doing some experimenting with the CSS3 @font-face feature on my website, as per instructions here:
[http://randsco.com/index.php/2009/07/04/cross_browser_font_embedding](http://randsco.com/index.php/2009/07/04/cross_browser_font_embedding)

I was able to get the chosen fonts to appear, but with a problem: each time the page loaded, or I clicked on a link, there was a short pause while the page was displayed using system fonts, before the page shifted to using the embedded fonts.

It seems like each time a new page loads, the page must re-download the .ttf definitions -- there is no caching of fonts, even though the CSS file never changes.

Is there any way round this problem?  It seems an ugly and unfortunate issue that makes me favour not using embedding at all ... :-(

Thanks & best wishes,

    -- Joe

---

### Post by hxcobd on 2010-02-17
Probably not the answer you're hoping for, but in the web design world, embedding non-standard fonts is very looked down-upon anyway, definitely not a recommended way to get a specific font appearing on a page.

It's much preferred to use them sparingly, as image files.

However, if you're dead set upon doing it, there are a few possible solutions to the issue you're having:

1.) Look into Javascript pre-loads for text and/or fonts. If you can get the text to preload before the rest of the page, it should switch fast enough that no one would see the system font.

2.) Look into CSS solutions, possibly the "hidden" attribute, to hide the system font that's coming up.

---

### Post by WebDrake on 2010-02-17
No worries about the 'don't do it' heads-up.  Always good to have warnings. ;-)

In my case I'm not wanting to embed loads of fonts -- my site only has 2 different font-faces -- but I'd like to determine them to be a particular pair, since those look better than the 'standard' web fonts.

If I can't do it effectively, there's no big deal, but if I can do it without hurting anybody, it'd be nice. :-P

Anyway, will check out your suggestions -- thanks for the ideas!

Best wishes,

    -- Joe

---

