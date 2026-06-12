---
title: "Best distro for MacBook 2,1 ?"
date: 2012-04-26
forum: Apple Hardware Users
---

### Post by enri2 on 2012-04-26
What distro will run on this , that will be fast?

MacBook 2,1
Intel Core 2 Duo 2ghz (dual core)
**Memory 1GB** ddr2 667 MHZ
GMA 950

OS X leopards seems to slow down a lot when i add 3+ tabs on firefox, and that with only firefox running. Memory is a problem.

Would switching to Ubuntu or other distros make the sustem faster?


What fast distro would you recommend? Unbunto or Fedore 16? 

Thanks:p

---

### Post by linuxopjemac on 2012-04-27
I have Linux Mint 9 (based on Ubuntu 10.04 LTS) running very well on this machine. I dumped Grub2 for classic Grub though.

---

### Post by Lars Noodén on 2012-04-27
It should be enough to run plain Ubuntu.  But if you want speed then you can try Lubuntu, which uses LXDE instead of Unity.  Or you can try using just a [window manager](http://xwinman.org/) by itself instead of a full desktop environment.  Your choices there are Fluxbox, Openbox, FVWM (and FVWM-crystal) or enlightenment.

---

### Post by piwacet on 2012-05-01
I have a macbook 2,1 and have run ubuntu on it for the last few release cycles, and it generally works fine.  I recently upgraded to 12.04, and have not used it much so far, but initial impression is that it works quite well.  I run the 3d unity, and the graphics effects run smoothly, and the whole system is responsive.  I do have 3GB ram, and 'top' shows that just over 1 GB is being used now, but not sure how much this actually reflects a need for more than 1 GB of ram.  I use the x86_64 version.  Computer lore is that using the 32 bit version of Ubuntu would need less RAM, not sure if this is true.

I don't really use bluetooth, and I haven't tried the sound yet in this release, but I remember them working in prior releases.  I think you may need to do some extra steps to get the camera working too, I never use it.

The only problem I've encountered with 12.04 is that the 3-finger "triple-tap" on the touchpad stopped being recognized as a middle-click.  I'm not sure if this was an intentional design decision or not, but it was quite a loss for me.  See for instance bug #754000 and bug #839769 in launchpad.  There is a simple workaround:

/usr/bin/synclient TapButton3=2

Good luck.

---

