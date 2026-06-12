---
title: "Borked Grub"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by drbob07 on 2007-04-15
OK, so I was messing around with repartitioning my drive and my main linux partition (/dev/hda2) is now /dev/hda4

GRUB doesn't know this though, so when I boot I get ERROR 22 (no prompt nothing)

EVERY GUIDE I have found tells you how to fix the MBR with windows disks, only problem is, I don't want to install the MS bootloader, I want GRUB back!

How can I repair the grub bootloader so that it looks for the configuration on /dev/hda4 instead of the old location /dev/hda2 ...?

---

### Post by freebird54 on 2007-04-15
Using the Live CD is one the easiest, then you can edit the file as needed.  This link will explain better than I can:

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

If you get a chance to hit <esc> when booting, you can redirect it from there instead - then edit once you ae in.

(file is /boot/grub/menu.lst)

---

