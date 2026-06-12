---
title: "[SOLVED] Miss my old Firefox"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by marbig on 2007-10-26
Mucked around on and off now for a while yet still class myself as a newbie to Ubuntu. Only just returned again to give it another go.
Have just clean installed 7.10 and everything (knock on wood) going okay. 
However I just can't seem to get Firefox to work like it does on my windows XP. Font sizes seem to be all over the place. In this forum all the fonts are extremely small. Have to use ctrl ++ to increase all the time. Go to google home page and the fonts there are supersize. Never had this problem in XP. 
Any ideas anyone please.
FWIW - video card (ATI Radeon) and driver operating okay. Other applications work fine.

---

### Post by crav on 2007-10-26
Does changing the system default fonts / font size help at all?

(Easy way: Right click desktop, Fonts tab)

---

### Post by Crafty Kisses on 2007-10-26
> **crav said:**
> Does changing the system default fonts / font size help at all?

(Easy way: Right click desktop, Fonts tab)

That might do the trick.

---

### Post by sneezymelon on 2007-10-26
yet how could the problem occur all by itself??

---

### Post by Crafty Kisses on 2007-10-26
> **sneezymelon said:**
> yet how could the problem occur all by itself??

I don't think the problem occurs by itself.

---

### Post by marbig on 2007-10-26
>          Does changing the system default fonts / font size help at all?Only alters the menu bars fonts. not the web page fonts.

---

### Post by MatthewPlanchard on 2007-10-26
try going to about:config and making sure all the font: settings are consistently above 12 point

---

### Post by marbig on 2007-10-26
> **MatthewPlanchard said:**
> try going to about:config and making sure all the font: settings are consistently above 12 point
Did that Matthew as you suggest. All above 12.

---

### Post by marbig on 2007-10-26
Going to leave forum for a while. Will return later to see if any further suggestions.

---

### Post by MatthewPlanchard on 2007-10-26
I've been messing about with Firefox tweaking ever since I read this thread, and I found something else you might be able to use.
If you go into your home folder and show hidden files, then follow this path:
.mozilla->firefox->xxxxxxxx.default->chrome
(the xxxxxxxxx will be a unique string on your system. Mine's mqkrtm6l)
There should be a file there called userChrome-example.css
It describes a way of increasing all default font sizes.
You could simply un comment the line about font size and set it to whatever size you wish.

---

### Post by marbig on 2007-10-26
Thanks for your help Matthew. Tried your idea. But didn't seem to work. Played further with Edit > Preferences > Content > fonts > advanced and finally sorted something out.
Thanks again. I'm a happy chappy now. \\:D/

---

### Post by alienexplorers on 2007-10-26
Why don't you just go to mozilla and download on of the older builds if you want to.
Older builds can be found at:
> [http://releases.mozilla.org/pub/mozilla.org/firefox/releases/](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/)

---

