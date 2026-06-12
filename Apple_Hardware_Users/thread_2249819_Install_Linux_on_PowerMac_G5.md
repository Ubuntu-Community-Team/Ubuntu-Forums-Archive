---
title: "Install Linux on PowerMac G5"
date: 2014-10-24
forum: Apple Hardware Users
---

### Post by jashtiani on 2014-10-24
I tried installing ubuntu 14.04.1 desktop for PowerPC from a dual layer DVD+DL disc. However, when booting up into Lubuntu, the screen flickers, and did not install. Also, when I unplugged the monitor, parts of the Lubuntu text are still left on the screen. Can anyone help me with this installation so I can turn my PowerMac G5 into a usuable computer? 


Thank you in advance for your help

---

### Post by howefield on 2014-10-25
Thread moved to "*Apple Hardware Users*" where you are more likely to get assistance.

---

### Post by este.el.paz on 2014-10-25
> **jashtiani said:**
> I tried installing ubuntu 14.04.1 desktop for PowerPC from a dual layer DVD+DL disc. However, when booting up into Lubuntu, the screen flickers, and did not install. Also, when I unplugged the monitor, parts of the Lubuntu text are still left on the screen. Can anyone help me with this installation so I can turn my PowerMac G5 into a usuable computer? 


Thank you in advance for your help

@jashtiani:

PPC is its own special niche these days . . . probably you should just use a single layer DVD of the iso . . . after checking md5sum number of the file.  First try to boot the LiveDVD . . . you will probably have to read the PowerPCFAQ to see if you can find the right boot parameters to get the video driver to give you a clean GUI . . . you could try just the "live video=ofonly" and see if that works.  And, for 14.04 you will probably need an xorg.conf file that matches your computer . . . you can find some that **might*** work on the "mac-on-linux" web site . . . .

If this is your first venture into linux, might be easier to try to get 12.04 running . . . there are a lot of threads on the forum about PPC for 12.04 . . . 14.04 is starting to push the hardware envelope . . . you can do it, might take a few tries.

e.e.p.

---

