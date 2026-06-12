---
title: "Missing OS in GRUB"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by DrPppr242 on 2007-04-29
I recently decided to completely get rid of windows which I had in a dual boot so I formated both my hard disks, I have a SATA as my primary and another IDE drive, and the installed Feisty onto my main drive, now when I try to install another OS on my second hard drive it doesn't show up in GRUB, how can I make GRUB show both hard drive's OS?

---

### Post by confused57 on 2007-04-29
See section #9, booting multiple linux distros,  on this site:

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by DrPppr242 on 2007-04-29
thanks this is a huge help I found the /boot/grub/menu.lst, and I'm trying to configure it but it says to put root        (hd0,0)  for where the OS is how do I find out what to put for those two values, I would assume that because Ubuntu is listed as hd0 it's probably hd1 for my other hard drive but what is the other 0?

---

### Post by confused57 on 2007-04-29
> **DrPppr242 said:**
> thanks this is a huge help I found the /boot/grub/menu.lst, and I'm trying to configure it but it says to put root        (hd0,0)  for where the OS is how do I find out what to put for those two values, I would assume that because Ubuntu is listed as hd0 it's probably hd1 for my other hard drive but what is the other 0?
You can get a list of your hard drive(s) partitions by opening a terminal:
```
sudo fdisk -l
```
the -l is a small "L"

Yes, the Ubuntu drive you boot to first is hd0, and your second hard drive is hd1...therefore, if another OS on your second drive is /dev/sdb1, your root would be (hd1,0)...for /dev/sdb2, root (hd1,1).  From the link I gave, you can use the configfile method to boot the other OS...to use chainloading, you'd need to install grub to the root partition of the other OS.

---

