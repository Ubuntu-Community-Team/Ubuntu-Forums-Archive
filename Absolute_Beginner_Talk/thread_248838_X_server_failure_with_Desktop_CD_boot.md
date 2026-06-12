---
title: "X server failure with Desktop CD boot"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by MaxBrains on 2006-09-01
Hi. I'm totally new to everything Linux, so this is the forum for me, apparently ...

I have a Desktop CD I'm trying to boot from. However, I get the following blue dialog:
> Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?
However, imediately afterwards, the terminal pops up over the dialog, preventing me from responding.

Following some advice I viewed /var/log/Xorg.0.log and therein I discovered the following errors:
> Cannot read V_BIOS
> VBE initialization failed
> Screen(s) found, but none have a usable configuration
I'm running a Celeron with 512MB of RAM and a FX5200 with 128MB on it.

---

### Post by bodhi.zazen on 2006-09-01
Sorry, sounds like Ubuntu live CD is not so good with your hardware.

You would have to use the alternate CD, install, and then configure X, likely downloading drivers.

I would try an alternate version of Linux unless you have some experience, in which case ....

Can you post the contents of xorg.conf?

---

