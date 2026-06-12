---
title: "[SOLVED] Dumped windows, now can't boot."
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by brennydoogles on 2007-09-23
So last night I decided to make the leap of faith from a dual-boot with XP to an Ubuntu only machine. I formatted /dev/sda1 to ext3, and planned on making it a partition for photos and videos. I removed windows from my /boot/grub/menu.lst, and continued on with my life. I turned off my computer for the night/next day (I knew I would be unable to use it, so I thought I would save power), and now I can't boot. Every Kernel I try to boot into sends my to a command prompt (with a failed fschk being the first thing I see, and it also tells me that apt is not installed (and tells me to apt-get install it **WTF??** ). Every command I type is unrecognized, and I'm not sure what is wrong. Any ideas on what could have happened??

---

### Post by alienexplorers on 2007-09-23
Please list > sudo fdisk -l
Please list your menu.lst file > cat /boot/grub/menu.lst

---

### Post by mc4man on 2007-09-23
I believe something similar to this happened to me last  year . As i remember the boot partition was the one with windows in it (sda1)

---

### Post by brennydoogles on 2007-09-24
Ok, it seems that there was an issue in my fstab, where /dev/sda1 was showing up twice. A little patience and my good friend Nano proved to be all I needed!! Thanks for the help!!

---

