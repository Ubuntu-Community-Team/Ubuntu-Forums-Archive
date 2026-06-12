---
title: "Fonts for LCD Monitors"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2007-08-12
I just got a really nice flat panel LCD and unfortunately my fonts don't look the greatest in ubuntu. I've 
seen links to patched fonts for LCD's, but it seems all of the repos are dead.

I've already tried changing settings and creating ~/.fonts.conf files, but nothing seems to make my fonts look better. Any ideas on how to make LCD's look beautiful as they should?

---

### Post by SOULRiDER on 2007-08-12
try going to:

System > Preferences > Fonts and tinker witht he settings a bit. I have an LCD monitor and ive selected Subpixel Smoothing with Full Hinting.

---

### Post by shanepardue on 2007-08-12
I have done this already to no avail. Thanks anyway!

---

### Post by SOULRiDER on 2007-08-12
Does ti happen everywhere or just in some apps. In my case for example it only happens in Firefox, but not allowing pages to load their own fonts fixed it.

Also,maybe your monitor needs other xorg settings, i suggest you backup the xorg config and reconfigure it, maybe that will help.

---

### Post by shanepardue on 2007-08-12
The way Firefox is displayed I understand can be changed, but the application itself has a 
horrible looking menu. It seems many apps aren't what they should be.

What do you suggest tweaking in my xorg? I'm not familiar with any xorg config settings 
that could help the look of my fonts.

---

### Post by starcraft.man on 2007-08-12
Hmmm, well the the blunt truth is that the best font rendering I've had is with the Text Render plugin (both installed and on by default) with Beryl. I assume it's the same or better with compiz fusion. Oh and by best, I do mean against Windows (with or without cleartype) and the Apple rendering. Maybe it's just me, I dunno.

If you got a decent card (GeForce 6 series/ATI equivalent or higher) I recommend just installing Beryl (or compiz fusion) and letting the text render do the work (it doesn't need any tweaking, it just looks great as is). It is easy to install, follow the ubuntu guide link in my guide and install from that (search for beryl, it's got a section).

That's my thoughts on font rendering, good luck.

---

### Post by shanepardue on 2007-08-12
I managed to find what I was looking for. I compiled the latest of the Freetype font among other free fonts. Thanks!

---

### Post by shanepardue on 2007-08-16
The latest freetype and the others is in an amd64 repo that is dead now. Does anyone know a repo for them?

The one I used was...

deb [http://ubuntu.moshen.de](http://ubuntu.moshen.de) feisty experimental
deb-src [http://ubuntu.moshen.de](http://ubuntu.moshen.de) feisty experimental


Thanks!

---

### Post by DrNick on 2007-08-25
Sure it's not that you're just using the wrong screen res?

---

### Post by shanepardue on 2007-08-25
> **DrNick said:**
> Sure it's not that you're just using the wrong screen res?
Yes I am. I've been using the 32-bit setup for awhile now. These repos are only available
 for 32-bit at the moment and in every experience I've had, ubuntu on an lcd looks horrible 
without these fonts.

---

### Post by qamelian on 2007-08-25
You may need to adjust the DPI in the advanced font settiings. Ubuntu defaulted mine to 75 DPI and it looked awful. Adjusting to 96 DPI fixed the font rendering and made all my fonts look great.

---

