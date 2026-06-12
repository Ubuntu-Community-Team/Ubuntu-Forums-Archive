---
title: "PowerMac G4 466 (Digital Audio) Ubuntu installation problem"
date: 2007-08-09
forum: Apple PPC Users
---

### Post by uzwa on 2007-08-09
Hi!

I've 2 hard drives and I'm trying to install to Ubuntu to slave hard drive. Master hard drive has mac os x 10.4.10. I also have 1gb SDRAM.

So I'm having problems with Ubuntu 7.4 installation. It is ppc desktop version. When I try to boot it I just got "Kernel panic - not syncing: Attempted to kill init!". And when I write "live video=ofonly" Ubuntu screen comes and starts to load installation. But after the installation has loaded itself console comes and it won't start installing Ubuntu. Then I could write something but I don't have any clue what should I write.

So could someone help me to solve this or should I do something differently?

From: Linux noob from Finland

---

### Post by stmiller on 2007-08-09
This setup is somewhat picky to do, as even if you want ubuntu on a different drive, you will still have to write yaboot (the bootloader) to your boot drive (the OS X drive). And the current ubuntu powerpc installer may have trouble doing this.

Try the alternative PowerPC CD instead of the Live CD (goes right to an installer) and at the point of installing, make sure to specify the other hard disc to install on. It should install fine on that disc, but you may have booting issues at first. Let us know.

---

### Post by jdusablon on 2007-08-09
You should be able to get what you want to do done by manually editing the partition map rather than using the guided scenario.

<EDIT> Be sure to remember your disk names so you know where to write the yaboot boot loader.

---

### Post by uzwa on 2007-08-11
Hi. I tried installing Alternative CD but it won't work. I did install it and after reboot it just told me that GUI won't work. The bugreport told me this:

Using config file: "etc/x11/xorg.conF"
***Inwalid IO Allocation***
Unable to find a valid framebuffer device
R128(0): Failed to open framebuffer device, consult warnings and/or errors above for possible reasons

Fatal server error:
no screens found

(ww) open /dev/fb1: No such file or directory
...
(ww)open /dev/fb7: No such file or directory

---

