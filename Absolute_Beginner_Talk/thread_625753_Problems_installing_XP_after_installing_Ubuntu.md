---
title: "Problems installing XP after installing Ubuntu"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by must4rdgas on 2007-11-28
Hi all,

A friend's XP notebook was getting very slow, so I formatted it. After format there was a bit of a HDD problem, and I couldn't install XP or Win2k. So I formatted and installed Ubuntu with the Gutsy CD and that worked 100%. Problem he isn't a Linux fan. So I got hold of an XP SP2 disc to install over Ubuntu.

When I restart with the XP disc in the drive, everything is normal. I get the "Boot from CD..." text and it proceeds to the "Setup is inspecting your system's hardware" screen. But after that, the screen goes black and it just hangs. I've tried the disc on my desktop PC and it boots up normally, i.e shortly after the "Inspecting your system's hardware" screen, it goes on to the blue-background screen which starts installing things etc.

What could be the problem with the notebook? Could you help me out?

Thanks,

must4rdgas.

---

### Post by gn2 on 2007-11-28
Try booting a Gparted Live CD and delete all the partitions on the hard drive, then try the XP CD again.

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

---

### Post by must4rdgas on 2007-11-28
Thanks, I'll try that.

---

### Post by gn2 on 2007-11-28
And make sure nothing's plugged in, no second monitors, no USB devices, no ethernet, no printers, no memory cards in any slots, no cardbus devices, WiFi switched off if possible and connect it to mains power, don't rely on the battery.....

---

### Post by must4rdgas on 2007-11-28
Alright, nothing is plugged in except power.

I'm in. Do you know what would I select to format the drives?

I'm at [this](http://www.tuxdistro.com/sshot/gp_live1.gif) screen. There are a couple more options below, namely "Boot mbr on first hard drive", "Boot partition #1-#4 on first hard drive", "Boot mbr on second hard drive" and "Boot partition #1 on second hard drive".

---

### Post by must4rdgas on 2007-11-28
Bump.

---

### Post by spec-chum on 2007-11-28
I think just select the top highlighted option.  That looks like it's asking how to run the live CD.  You haven't got to the disk partitioning bit yet.

---

### Post by gn2 on 2007-11-28
Spec-chum is correct, just press enter with the top line selected.

---

