---
title: "Firefox fonts wrong after installing fonts..."
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by encompass on 2006-09-29
I just installed a pile of new fonts in the font dir (./fonts) and now my firefox displays a terrible looking font.  I have fixed the problem for now by setting a default font for all pages.  But would like it is I had it fixed.
Outside of removing and sorting thre each and every font I have...(6000+) is there a way for me to fix this issue?
:-|

---

### Post by Arthur Archnix on 2007-09-28
Installing new fonts shouldn't change how pages are rendered. That is, if you don't have the ms core fonts installed firefox will revert to some default choice, which you've apparently now changed, but otherwise will render fonts as the pages request. 

At least, that's been my experience.

Check out the ubuntuguide for installing ms fonts if you haven't already, then restore firefox to defaults.

Also, what version of ubuntu and firefox are you running? That might explain it as well if you're not running feisty / feisty version.

---

### Post by kerry_s on 2007-09-28
you should pick your own font, it helps with speed.
it's probably loading bitmapped fonts, you can turn them off.

**sudo dpkg-reconfigure fontconfig-config**

---

### Post by Beretta_NZ on 2008-07-09
> **encompass said:**
> I just installed a pile of new fonts in the font dir (./fonts) and now my firefox displays a terrible looking font.  I have fixed the problem for now by setting a default font for all pages.  But would like it is I had it fixed.
Outside of removing and sorting thre each and every font I have...(6000+) is there a way for me to fix this issue?
:-|
I would like to know if you managed to fix this problem.

I had the same thing when i installed ubuntu, so I just forced Firefox to use the fonts I chose, rather than letting websites determine the font. But that's not a real solution. I have now just installed Linux Mint, which is a version of Ubuntu, and I have just installed my font collection, and the same thing has happened again. Something is causing it to use some ugly font in firefox, and also in some parts of thunderbird - and ALSO when I create a pdf with openoffice, that same ugly font is used.

So it's a universal setting hidden somewhere in ubuntu that I appear to have no control over.

---

### Post by adrenal1n3 on 2008-07-09
I have extremely weird problems with the fonts. I want the tahoma font to use with Ubuntu but it won't work. I read the guides but I just don't get it if someone could just please help me with this, PM me a msn or some way to contact you.

---

