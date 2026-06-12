---
title: "Should I have any compatibility issues with ubuntu &amp; portable projector?"
date: 2010-12-21
forum: Apple Hardware Users
---

### Post by ChowderDown1 on 2010-12-21
I've had ubuntu on my macbook for quite some time and it works well. Some bugs here and there, but it comes with the territory. I recently got an **[aaxa tech m2 micro projector]("http://www.aaxatech.com/products/m2_micro_projector.htm")** as a gift and I wanted to set it up with my macbook. The projector itself is pretty awesome. No bigger than two bars of soap and can project 80 inches easy. It also has native xga 1024x768 and hdmi input. 

I would still have to use the mini DisplayPort-to-VGA in order to use the projector, right? But would I need to have any other programs or software to make it work? For other devices its rather simple, but Im wondering if I would have to do anything else. 

Thanks for the help :)

---

### Post by lael on 2010-12-21
I had an issue with 2 older Projectors that didn't communicate an [EDID]("http://en.wikipedia.org/wiki/Extended_display_identification_data").  It kept my resolution at 640x480 :-(  I read up on it and there apparently was a way to manually fix it with some Xorg.conf settings, but couldn't get it to work.  I don't know if it was my fault or just the fact that I have a mbp 6,1 that has the split integrated/discreet gfx cards.

Newer Projectors shouldn't have any issues though.  Good luck!

---

### Post by futn001 on 2010-12-21
The projector is to bar inside is installed, or you might be guests  blocking, can ask some professional personage

---

### Post by RandomJoe on 2010-12-22
I haven't tried a projector with a Macbook, but for years ran a projector as one head of a multi-head system.  Worked a treat, until Xorg went to the "no xorg.conf file" setup.  I fought with X for a long time, including creating an xorg.conf for it, and never could get things to work right.

The projector itself wasn't a problem - it was the other LCD panel (which does report EDID info) that was attached.  Whenever I connected the projector, X would only run the LCD at 800x600 or something very low.  If I only needed one or the other everything was fine, just never was able to get both working simultaneously.

That was with Ubuntu on an Intel Mac Mini.  I got frustrated with fighting it, and put OS X back on.  Of course, both the LCD and projector worked flawlessly first time out on OS X!  *sigh*

Good luck!

---

### Post by skullmunky on 2010-12-28
It should work fine... though if it doesn't let us know, I want one of these too.

---

