---
title: "Downgraded video driver - did I do it right?"
date: 2008-02-22
forum: Apple PPC Users
---

### Post by stream303 on 2008-02-22
I just fixed a problem my G5 iMac was having with Gutsy which was a shifted/wrap around screen with the nv driver.  (resolution was correct, and it worked fine in Feisty)

I just took the nv_drv.so file out of Feisty's /usr/lib/xorg/modules/drivers directory, and used it in my Gutsy install.  Works great and fixed my problem!

However I see other threads describing installing an entire deb package to an earlier version of the x server as a way to downgrade.

Am I losing or gaining anything by copying just the nv_drv.so file rather than installing an older deb package?

---

### Post by BladeMelbourne on 2008-02-22
The next time an updated nv driver appears in apt repositories, your file will be over-written when you choose to install updates.

I suggest opening Synaptic, searching for "xserver-xorg-video-nv" (that's the package name in Hardy, hopefully the same for you), selecting the package by clicking on it once, then go to the Package menu and select "Lock Version".

I had to do this with the ATI package in Gutsy (so I could continue to use the Feisty driver).

HTH.

---

### Post by stream303 on 2008-02-22
Thanks - I wondered about that.

Luckily, I copied the nv_drv.so file over immediately after installation of Gutsy and then did the update routine as a test.  The file survived (this time I guess ) and I made sure to make a backup copy of the Feisty driver so I could restore it if an upgrade took it back out.

Right now, it's kind of a watch-dog to see if any video driver upgrades come down the pike. :)

But that's exactly what I am wondering - is it better to use just this one file rather than swap out the entire xserver - in other words have I just *tweaked* the existing driver, rather than do a full downgrade back to the Feisty driver?

I'll have to try your method of a full xserver downgrade and try it out.  Somehow it feels right, and right now I think I'm just getting away with something. :)

Your tip is going straight into the Firefox scrapbook extension!  I'm not a huge fan of the Tomboy mini-wiki notetaker.

---

