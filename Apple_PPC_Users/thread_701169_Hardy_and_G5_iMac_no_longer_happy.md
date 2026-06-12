---
title: "Hardy and G5 iMac no longer happy"
date: 2008-02-19
forum: Apple PPC Users
---

### Post by stream303 on 2008-02-19
Ok it's only an alpha, but man today was rough on my G5.  Unlike my earlier sucessfull Hardy alpha install, this one hit the skids.

Started with fresh daily image and the installer still fails to recognize internal cdrom after loading kernel.  Same bug as before.

My workaround of burning TWO iso images still works.  This time, I tried using just a USB-CDrom drive, and install picks right up on the cdrom after the internal cd fails.  So far so good until they can fix this big bug.

You could also boot from a firewire cdrom using open firmware.

The really bad news is that it won't even detect my internal hard drive anymore, won't install any modules, and even fails to partition my external firewire even though it tries.

I DID notice that they increased the size of the Apple New World partition from the usual 977K to 1MB, and this caught my attention immediately since there have been problems when partitioning the New World partition on the 1mb boundary.  Could this be the reason that partitioning, in guided or manual modes lets you go through the motions, but eventually fails?   ARRRGGGHHH

Now I'm officially paranoid - planning to get what I can out of feisty and gutsy and back up all my updated apt-cache packages for safekeeping.  Be sure to grab a compiler.

I can't say if they got around to fixing the thermal support, because on the early G5 iMac I have, the fans always scream until an install is finished.

Man, not looking good for PPC owners, but I guess it is only February.

---

### Post by ssam on 2008-02-19
the live cd still has not picked up the new kernel which should fix the IDE issue :-(

---

### Post by BladeMelbourne on 2008-02-19
The IDE issue was a problem for me, but updated kernel packages fixed that problem.

I upgraded to Hardy by changing "gutsy" to "hardy" in /etc/apt/sources.list

I kept my 2.6.22 kernel installed - because Mac on Linux (MOL) doesn't compile on 2.6.24

I also had to compile my radeon driver from git as "xserver-xorg-video-ati_6.6.3-2_powerpc.deb" wont install on Hardy. There is one issue with the latest radeon source:
[https://bugs.freedesktop.org/show_bug.cgi?id=14446](https://bugs.freedesktop.org/show_bug.cgi?id=14446)

Overall, I'm happy enough.

---

### Post by stream303 on 2008-02-19
For a distraction, I tried the latest debian testing and it too fell down right when it tries to detect the cd.

Something is not well in Camelot! :)

Guess I'll wait a few days and try again on both systems....

---

