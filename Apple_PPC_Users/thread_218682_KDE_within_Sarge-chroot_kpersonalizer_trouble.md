---
title: "KDE within Sarge-chroot? kpersonalizer trouble"
date: 2006-07-18
forum: Apple PPC Users
---

### Post by RavenOfOdin on 2006-07-18
Hey, I've been trying to get a 32-bit Debian Sarge-chroot set up on my iMac as per the debootstrap man page.  After a while of mounting and changing user settings I've managed to get a nearly usable system.  I've bound /dev and /tmp to my main (Ubuntu) /dev and /tmp respectively.  

I'm trying to get KDE running, and I've had to install packages such as xfonts-base for the X server to be able to start up.  It doesn't seem like its able to listen on tty7 (where GDM is) and I've tried to get it running on tty8.  

After I've managed to do this, kpersonalizer is now failing to start via the "startkde" script in /usr/bin.

The messages I get are something along the lines of:

```

Xsetroot: unable to open display ""
Xset: unable to open display ""
kpersonalizer: Cannot connect to xserver

```

and the last line repeats over and over until I either kill startkde through a different tty or restart the computer.

How can I fix this? I've tried looking in the startkde script but I can't see anything that would help.

Thanks in advance to anyone who can help me figure this out.
.

---

### Post by RavenOfOdin on 2006-07-19
Hmm, for some reason when I set startx to tty8 it came up automatically - without KDM.

3.3 doesn't look that good compared to 3.5, but then again I DID set my iMac's processor to "slow." :D

---

