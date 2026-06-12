---
title: "Stuck on mem test"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by marbobj on 2007-09-14
Using Ubuntu 7.04.  When Grub comes up all my other application work as far as booting, except for Ubuntu.  It goes to mem test instead of booting.  I accessed the menu list through my other applications and it shows the normal boot entries there.

Is there any way to get past the mem test?

Thanks a lot

---

### Post by bone2006 on 2007-09-14
grub seems to be off

I would boot up your liveCD, then mount your root, generally I just open up the file manger from the top and if you click on the drive menu on the left it mounts it for you.

then type in sudo gedit /boot/grub/menu.list and take a look there and see why it's defaulting to memtest.

---

### Post by marbobj on 2007-09-14
Thanks, I'll try that.

---

### Post by marbobj on 2007-09-14
I only have the 6.10 live cd.  I can't find anything that specifically says file manager.  When I try to mount  the partition with the terminal (I'm on partition 9 with Ubuntu) it says no mount point.

I thought there was a way to get into the menu list by hitting esc while the grub was loading, but that doesn't seem to work.

What am I doing wrong on this one?

Thanks a lot.

---

### Post by alienexplorers on 2007-09-14
Try hitting "e" while booting.

---

### Post by bone2006 on 2007-09-15
when I boot with the liveCD on the top panel I click on home, which fires up nautilus and once nautilus is up, I see on the lift side the file system and all my partitions.  Normally if I'm not mistaken it will give you the size, if you click on it once it mounts it, click on it twice it opens it up.  Once you mount it and then open it up.  Be sure to open up the root partition, then you'll see boot/grub/menu.list

---

