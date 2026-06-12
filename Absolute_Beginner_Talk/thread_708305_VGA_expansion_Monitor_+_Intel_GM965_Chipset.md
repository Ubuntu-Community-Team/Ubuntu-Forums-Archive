---
title: "VGA expansion Monitor + Intel GM965 Chipset"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by bachibusuc on 2008-02-26
Hi,

I just bought a new lenovo laptop with the integrated Intel GM965 x3100 Chipset. I've been looking all around the places for a driver and How to install it. The most interesting thing I found was [http://intellinuxgraphics.org/](http://intellinuxgraphics.org/). I tried to mess a little bit with xorg.conf but still doesn't work. I tried the download part on [http://intellinuxgraphics.org/download.html](http://intellinuxgraphics.org/download.html) and still didn't work.
I'm trying all these because I come from Windows where I can expand my desktop on another Monitor on only one VGA port. and do a little bit of more 3D effects(not much but still). I've also read at some places that the chipset was blacklisted from the kernel? I don't know what it means but doesn't seem nice. lol. I went in screens and resolutions trying to change my "Graphic Card" but it seem to always come back to something VESA ... so I really don't know what to do.

Anyways, I was wondering if anyone could help me ?

Thank you

---

### Post by bachibusuc on 2008-02-26
Anyone?

---

### Post by Iehova on 2008-02-26
:confused:

The 965 driver should be enabled by default in ubuntu, I know it was for me... You shouldn't need to go hunting about anywhere. Maybe in a terminal enter 'glxgears' and make sure that they spin at a relatively fast rate... or possibly more effective run "glxinfo | grep renderer" and see if you get something like "OpenGL renderer string: Mesa DRI Intel(R) 965GM 4.1.3002", or even look in your xorg.conf.

EDIT: Oh, the X3100 is blacklisted by Compiz by default, but that's easy enough to get around. Also, in 'screens and graphics', under Graphics Card I have vesa > intel and vesa > vesa.

---

### Post by bachibusuc on 2008-02-27
Do you know how to configure in Compiz to be able to expand the dekstop onto another monitor by vga? 

And in screens and grphis, I change to intel 965 but it keeps coming back to vesa!

Thanx

---

### Post by Tom--d on 2008-02-27
I've got an 965 intel chip set thingy.

Its was enabled automaticly. Got the 1280x800 on the live CD. and now running full Ubuntu, its worked fine. 

Well, I wouldn't mind if the effects and all that to work!!! But I heard it was blacklisted. What will happen is I take it off the black list? What problems will I get?

---

### Post by Iehova on 2008-02-27
> **bachibusuc said:**
> Do you know how to configure in Compiz to be able to expand the dekstop onto another monitor by vga? 

And in screens and grphis, I change to intel 965 but it keeps coming back to vesa!

Thanx

If you have compiz running then it sounds like the 965 driver is working. The fallback driver isn't capable of running compiz. If you want to be sure, you can run "glxinfo | grep renderer" in a terminal. I got "OpenGL renderer string: Mesa DRI Intel(R) 965GM 4.1.3002" and you should get something similar. Either that or paste your /etc/X11/xorg.conf file here.

I'm afraid I know nothing about using multiple monitors...

---

