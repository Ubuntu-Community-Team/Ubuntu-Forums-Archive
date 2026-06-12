---
title: "What program for editing font characters and text manipulation?"
date: 2008-12-22
forum: Art &amp; Design
---

### Post by Timbow on 2008-12-22
Greetings from a newbie. Sorted out all the installation problems but I still don't have Ubuntu really ready to go to work:

Graphic design:- in Windows I was using an old copy of Corel Draw and I need the Ubuntu equivalent. In particular I need to convert font Characters to curves or paths to edit the shape of the letters for making a corporate logo I was working on.

I also need to prepare some simple letterheads for print so I need opinions and advice on what program makes reliable eps files.

Thanks,

Tim W

---

### Post by smartboyathome on 2008-12-22
Fontforge. I use it, and except for the version on Arch Linux not having the ability to import SVGs, its great.

---

### Post by MarkBremmer on 2008-12-24
Font Studio Pro is an excellent program if you want a full blown font creation software. I use it professionally preparing fonts for both PC and Mac. It has some really nice pro features that makes life so much nicer!

[http://www.fontlab.com/font-editor/fontlab-studio/](http://www.fontlab.com/font-editor/fontlab-studio/)

Mark

---

### Post by Timbow on 2008-12-25
Thanks, has anyone used Xara Xtreme? Is it good enough for semi-professional work?

---

### Post by smartboyathome on 2008-12-26
> **Timbow said:**
> Thanks, has anyone used Xara Xtreme? Is it good enough for semi-professional work?

I would say use Inkscape instead of Xara for SVG work. Xara does not have a very good SVG export filter (svg is the universal vector graphics file format). Also, Xara is pretty much dead right now, with no support from either the company that open sourced it nor the open source developers.

By the way, if you want, you can design your font in Inkscape and then import it into fontforge. See [here]("http://ospublish.constantvzw.org/tools/import-inkscape-in-fontforge") for how. Note that it doesn't work for me on Arch Linux, though I don't know about other distros.

---

### Post by Timbow on 2008-12-28
Thanks Smartboy I will take your advice, but sheesh this is a struggle changing OS! It's okay for simple home stuff like email and surfing and a bit of open office but it is hard even to get off the blocks with anything more demanding.

I have found where the fonts are. Now I can open a font in Font Forge. Looks like it will do what I need, but I need to install fonts. I could do all this in seconds last month in windows, and i haven't even started with trying to get sketchup working under Wine and exporting DXFs to a program that can use them.

---

### Post by smartboyathome on 2008-12-29
> **Timbow said:**
> Thanks Smartboy I will take your advice, but sheesh this is a struggle changing OS! It's okay for simple home stuff like email and surfing and a bit of open office but it is hard even to get off the blocks with anything more demanding.

Of course it is. Linux is not Windows, and you have to "unlearn" all the stuff you thought you knew when changing OSes as it is knowlege specific to one platform. The only way for it *not* to be that hard is by making Linux a clone of Windows. ;)

> **Timbow said:**
> I have found where the fonts are. Now I can open a font in Font Forge. Looks like it will do what I need, but I need to install fonts. I could do all this in seconds last month in windows, and i haven't even started with trying to get sketchup working under Wine and exporting DXFs to a program that can use them.

To install a font, just put it in the /home/username/.fonts folder and it will get added to each application when it starts/restarts. Note that with FontForge, you have to export a font there instead of save it, as saving it saves it in FontForge's native file format.

---

