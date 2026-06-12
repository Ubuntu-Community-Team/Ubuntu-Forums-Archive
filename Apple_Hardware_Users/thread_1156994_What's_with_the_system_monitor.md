---
title: "What's with the system monitor?"
date: 2009-05-12
forum: Apple Hardware Users
---

### Post by Benboom on 2009-05-12
When I run the system Monitor in Ubuntu 9.04 on my PPC G4 it shows that the System Monitor is using more CPU than anything else! The load seems to be ridiculous - it uses up to 50% of the processor (sometimes more; especially if I go to the Resources pane with the graphic display) so it's plainly not usable at those times when you already have something that's a heavy user. It's System Monitor 2.26.0.1

I downloaded a KDE package which inludes System Monitor 4 (KDE 4.2.2) and not only is it much more like what I am used to on the Mac, it doesn't seem to have the preposterous CPU load the GNU monitor does.

Is there any reason to even mess with the GNU monitor?

---

### Post by stream303 on 2009-05-12
Nice catch!  I remember something about this awhile back - I guess to prove it is working it makes sure that it grabs the most resources. :)

I just checked this in my Debian Testing ppc setup and same resource-hogging issue.  It even blew out my hotrod-gNewSense amd64 box.  So you're not alone.

In lieu of this, my absolute favorite util to keep an eye on things is **HTOP**.

Other than that, I use the gnome hardware-sensors module (sensors-applet), htop, and cpufrequency scaling monitor active at times.  A bit lighter on the resources for sure.

---

### Post by Benboom on 2009-05-12
Well, I have installed the KDE package and the System Monitor that comes with it is not so unfriendly resource-wise so I'm using it for now when I need to kill something, but I also have an extremely ugly ( :D ) Conky window to look at too and that serves well to show when something is hogging the system without doing any hogging itself. I'm finding stuff all over the place to try out!

Now if I could just find a low-resource MP3 player. But that's another thread. :D

---

