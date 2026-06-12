---
title: "Looking for an updated video driver"
date: 2014-08-16
forum: Apple Hardware Users
---

### Post by jacatone on 2014-08-16
I'm using Lubuntu v12.04 for PPC on a Powerbook G4. I'm wondering if there's a newer video driver for the one listed below:

"0000:00:10.0 VGA compatible controller: NVIDIA Corporation NV34M [GeForce FX Go5200] (rev a1)"

If you're wondering why I'm using an older version of Lubuntu, I had too many problems with the newer version.

---

### Post by rsavage on 2014-08-17
Yes there are, but you'll need to compile them (and other packages) yourself

e.g. [http://packages.ubuntu.com/precise-updates/xserver-xorg-video-nouveau-lts-trusty](http://packages.ubuntu.com/precise-updates/xserver-xorg-video-nouveau-lts-trusty)

You can also compile the nv driver in 12.04, but that won't work with compiz or other 3d apps should you wish to use them.

Why are you looking for an updated driver anyway?

More info about PowerPC is here: [https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

---

### Post by jacatone on 2014-08-20
I get the accordian effect when I move windows and video playback is all screwed up which is a clear sign of driver issues. The link above is for the Intel version. I was able to find the link below but my PPC is 1GHz and don't know if this will work.

[http://ubuntuforums.org/showthread.php?t=2131644](http://ubuntuforums.org/showthread.php?t=2131644)

---

### Post by jacatone on 2014-10-30
I don't see this package for the nv driver that I can compile from source? What and where is it?

---

