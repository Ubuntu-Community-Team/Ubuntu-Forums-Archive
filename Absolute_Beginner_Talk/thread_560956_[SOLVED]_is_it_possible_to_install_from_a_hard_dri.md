---
title: "[SOLVED] is it possible to install from a hard drive?"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by erisianmonkey on 2007-09-27
since I'm having such trouble getting Ubuntu to recognize my DVD drive (see: [http://ubuntuforums.org/showthread.php?t=560658](http://ubuntuforums.org/showthread.php?t=560658) for details), is it possible to use XP to put files onto the hard drive to have Ubuntu boot up and install from that drive?

If so, can someone give me some basics?

TIA

---

### Post by dpar on 2007-09-27
Wubi?      [http://wubi-installer.org/](http://wubi-installer.org/)

Never used it myself.......just a thought

---

### Post by erisianmonkey on 2007-09-27
Hmm. Looking at their website, I should be able to install with Wubi, then use LVPM to turn that into a real install. I'm off to try it, I think. will report back with my findings.

Thanks for the idea!

---

### Post by stillingen on 2007-09-27
> **dpar said:**
> Wubi?      [http://wubi-installer.org/](http://wubi-installer.org/)

Never used it myself.......just a thought

Cool! There is also a similar Debian project [http://goodbye-microsoft.com/](http://goodbye-microsoft.com/)

---

### Post by erisianmonkey on 2007-09-27
Wubi worked. I am typing this from Firefox on Ubuntu now. As far as their warning about "slight" degradation of disk access time, read that as slow as molasses in an Arctic January. I'm still grateful as hell to them, because I was sick of punding my head against this thing trying to get up and running. Next project is to try LVPM to migrate to a real partition to see if I can't improve my access time. Then I can worry about my dvd drive and my wireless KB & mouse.

Thanks again, I'm off to try LVPM.

---

### Post by erisianmonkey on 2007-09-28
LVPM works, somewhat. I cannot get grub to install on either HDD. I've even created a partition on the larger hard drive to try and get a grub install that way. I'm tinkering with super grub disk now, but I will probably be getting into hardware config changes tonight to make something click.](*,)

---

### Post by erisianmonkey on 2007-09-28
So I got everything working now, as far as my cd drives go. I installed an old cd-rom drive from another computer and it cleared all my problems up to use the Live CD to install a real copy of ubuntu. I'm now heading back over to windows to kill the Wubi install and then get my big hard drive put back into one piece. I'm going to mark this as solved, even though I only got halfway there, but you get the gist.

---

