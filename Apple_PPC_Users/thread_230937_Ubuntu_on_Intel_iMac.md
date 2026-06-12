---
title: "Ubuntu on Intel iMac?"
date: 2006-08-06
forum: Apple PPC Users
---

### Post by dgm on 2006-08-06
I've been researching this idea, and really want to install Ubuntu on my Intel iMac. I found this:

[http://www.mactel-linux.org/wiki/Main_Page](http://www.mactel-linux.org/wiki/Main_Page)

Sadly, the instructions are not up-to-date. :( I heard that it could be done with BootCamp somehow, but you didn't actually need Windows XP itself. I've downloaded BootCamp, updated firmware - but now what? I really love and miss Ubuntu, does anybody have any ideas? Any help appreciated.

* EDIT: I found [this](http://bin-false.org/?p=17) in doing some further research. Would this work on my Intel iMac? *

Thanks,
dgm

---

### Post by jakemikey on 2006-08-07
That's what I followed with my iMac Core Duo (actually, I followed the triple-boot guide from onmac).  Everything on the site you mention should work, except wireless (different chipset for the iMac - I believe the bin-false tutorial was written with the Macbook chipset in mind).  For wireless you'll have to use ndiswrapper.

---

### Post by dgm on 2006-08-07
Thanks for the info. I successfully got it installed, but here's my question - how do I figure out the proper horizontal and vertical refresh rates, and all that junk, so my screen doesn't look so stretched out at 1680x1050? I would appreciate any help.

Thanks,
dgm

---

### Post by jakemikey on 2006-08-08
As far as I know, refresh rates have nothing to do with your aspect ratio.  If your xorg.conf file has 1680x1050 and that's what your screen's native res is, then it's not "stretched".

---

