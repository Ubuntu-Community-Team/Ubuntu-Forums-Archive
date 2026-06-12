---
title: "Drivers messing up"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by Fire Legion on 2007-07-09
**Problem:**

I've managed to, after long hours of wrestling with my PC, dual boot with Ubuntu. Whilst exploring Ubuntu, I clicked on 'Desktop Effects', and it asked me to enable 3D drivers. I did so, and after a short installation time, it asked me to reboot. On rebooting, I started Linux, only to find the X-server not found error.

**Hardware:**

E6400 Processor
Nvidia 640MB 8800 GTS
2GB RAM

**Software:**

Dual booting with Vista (64bit) and Ubuntu 7.04

**Plea:**

Can anyone help me?

---

### Post by steve.horsley on 2007-07-09
use this command:
**sudo nano /etc/X11/xorg.con**f
find the line:
**    Driver   "nvidia"**
and change it back to
**    Driver  "nv"**
which is the original open source driver. This will get your GUI back. You may need to install the driver from nvidia's site (lots of instructions on this forum) - I think I read that the 8800 is too new for the drivers included in the Ubuntu repositories.

---

### Post by Fire Legion on 2007-07-10
My interface is back, thanks. I'll read around for finding the driver :)

---

