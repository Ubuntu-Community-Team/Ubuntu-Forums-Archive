---
title: "Chasing better web fonts"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by TreverT on 2008-02-18
OK, I'm trying to improve my browsing experience in Firefox, on Ubuntu 7.1.  I've got the mstcorefonts, have subpixel smoothing turned on for my flatscreen monitor, and here's a direct comparison:

[IMG]http://img442.imageshack.us/img442/8521/fontcomparoox2.jpg[/IMG]

Those examples are screenshots taken from my Ubuntu system and my wife's XP laptop.  In the top two, you see ubitquitous web font 'Verdana', which I find a little constricted and hard to read - ergo, that's why I sometimes override the page-selected fonts with my own favorite, Ubuntu's "sans" (see third pic).  I just think it's prettier, smoother, and easier for my forty-one year old eyes to read.  **Unfortunately**, jillions of sites out there seem specifically designed for Verdana only, and all the menus and text fields can go out of whack if I use the sans font.

I'm prone to just stick with Verdana and squint, except that it has an annoying glitch that really bugs my eyes after a while:

[IMG]http://img411.imageshack.us/img411/8362/xkilloql5.png[/IMG]

As seen above, Ubuntu's rendition of Verdana has a strange problem with letters x, k, and 2, plus other characters that have angled lines.  It's really distracting when trying to read a lot of text, to have these strange faded bits sprinkled throughout.  Is this a known issue with Ubuntu's font rendering of Verdana?  And if so, are there any font alternatives to Verdana that match it better and look better, to help preserve the website layouts that absolutely **must have** Verdana to look right?

---

### Post by mattismyname on 2008-02-18
I have the same problem with the 'x's and the 'k's! 

Wish I was more of a font expert to know what's wrong with it...

---

### Post by ice60 on 2008-02-18
i did this on my suse OS, it should work with ubuntu too.
[http://www.suseforums.net/index.php?showtopic=43475](http://www.suseforums.net/index.php?showtopic=43475)

all the fonts i use i installed myself from various places, i much prefer them to the default fonts.

---

### Post by mattismyname on 2008-02-18
ice60- Does the method on that page specifically fix the x, and k issue in Verdana?

thanks!

---

### Post by ice60 on 2008-02-18
> **mattismyname said:**
> ice60- Does the method on that page specifically fix the x, and k issue in Verdana?

thanks!

i don't know. 

Verdana is just a font that's a really, really bad ripoff of helvetica. you could maybe try a helvetica clone instead, here -
IndUni-H.zip on this page -
[http://bombay.indology.info/software/fonts/induni/index.html](http://bombay.indology.info/software/fonts/induni/index.html)
each font is exactly the same size as Verdana's, but slightly better shaped, so there's no chance it will render differently.

---

### Post by ice60 on 2008-02-18
you might as well try it out because the whole thing is reversible. i've posted pictures of fonts in the past and no one who doesn't have the problem can see it lol. so, the x's and k's look just as good as the other charactors to me :) to me the f's, r's and t's in the XP screenshot look the worst!, they look really faded.

---

### Post by TreverT on 2008-02-19
I DLed the IndUni-Helvetica font to try out.  Here is a comparison shot of using Verdana as my web font and forcing pages to render in IndUni-H instead:

[IMG]http://img411.imageshack.us/img411/9576/verdanaindunihly6.jpg[/IMG]

(Don't be distracted by the different formatting of the paragraph - that's just the difference between Firefox and Opera)

IndUni looks nice and perfectly fits Verdana fields in the horizontal sense, but it's a bit squashed and short by comparison -  a 10 pt IndUni text is much less readable than a 10 pt Verdana text, for example.  And if I crank up the minimum font size to make it more legible, that blows the layout of anything that depends on having small Verdana fonts, again.  I guess for the time being I'll just have to stick with Verdana and live with the odd x/k/2 glitch.  

Out of curiosity, if I didn't want to have to override web page fonts with my own choices (for maximum compatability across size ranges) but wanted so switch to something different than Verdana as the most commonly used, could I not just move the Verdana fonts out of the font folder, then rename whatever I wantt to use as Verdana?  Wouldn't that cause the web page to display that font, thinking it was Verdana, and keeping all other web page settings (sizes & colors) intact?

---

### Post by ice60 on 2008-02-19
i don't know about renaming Verdana, it should work, if you remove Verdana altogehter the page will use the second font given in the CSS i suppose, i'm not a web developer so know nothing about it!

you can use a custom user.css too to forcw different page rendering.

i do know if you work to get your fonts looking good system wide you probably won't have any more problems. try the link to the suse forum, then logout and back in, if it doesn't work you can reverse it.

---

### Post by hopelessone on 2008-02-19
Hi,

I installed Ubuntu** restricted extras** in add/remove...worked for me..<< search for Ubuntu"

hope that helps..

---

### Post by Teber on 2008-02-19
yes Ice60 that's how it works. whenever there's a sequence of fonts in the css your browser will look for the leftmost one and if it's not installed will try the one right next to it. etc...

---

