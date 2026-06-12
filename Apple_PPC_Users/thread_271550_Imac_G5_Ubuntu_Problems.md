---
title: "Imac G5 Ubuntu Problems"
date: 2006-10-04
forum: Apple PPC Users
---

### Post by StarWind856 on 2006-10-04
Well, i have tried many distros(like 5 or 6) all from the ubuntu downloads section, and i have booted them, to some extent(this is on my Imac G5) and whenever it tries to load ppbuttonsd(something like that) i have searched in google, and i have found that this is for the volume, eject, and screen brightness buttons on apple laptop keyboards, but the imac isnt a laptop, but Ubuntu insists on loading it, and it always fails to load, which screws up the load screen and goes blank and then goes black screen, but the display is still on, just completly black except for the backlight, so what is going on ad how can i fix it so i can finally boot an ubuntu live cd?(and btw i have a standard apple keyboard with a microsoft intellimouse wireless laser 6000 mouse)

---

### Post by stmiller on 2006-10-05
The ubuntu live ppc cd does not boot on G5 hardware. Sound, video, and thermal support is not there for iMacG5s. It's an old kernel image. You CAN install ubuntu using the alternative CD, and compiling a new kernel from kernel.org.

See post #5 here:
[http://ubuntuforums.org/showthread.php?t=232908&highlight=powermac+g5](http://ubuntuforums.org/showthread.php?t=232908&highlight=powermac+g5)


And pbbuttonsd IS used by all current mac hardware. Not just for laptops. You do want it.

---

### Post by wagerrard on 2006-10-07
All Mac G5's are not the same. The instructions in that link don't work for late-model iMac iSight G5's. No fault of the instructions, the problem seems to be lack of support in the kernel.

BTW, has anyone successfully built 2.6.18 from kernel.org on an iMac iSight?

---

### Post by stmiller on 2006-10-07
Ask here:

[http://forums.gentoo.org/viewforum-f-24.html?sid=ebcb9f8927d1200e3e6471840f656fdf](http://forums.gentoo.org/viewforum-f-24.html?sid=ebcb9f8927d1200e3e6471840f656fdf)

or join the irc channel mentioned here:

[http://forums.gentoo.org/viewtopic-t-497222-highlight-imac.html](http://forums.gentoo.org/viewtopic-t-497222-highlight-imac.html)

> PostPosted: Mon Sep 11, 2006 7:36 pm    Post subject: isight owners needed  	Reply with quote
We need people with these boxes to help us test install media. Please consider helping us out as you can make a difference! Join us on irc @ #gentoo-ppc64
_________________
-->
rangerpb
<--

---

