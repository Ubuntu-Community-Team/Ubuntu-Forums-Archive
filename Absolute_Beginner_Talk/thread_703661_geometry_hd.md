---
title: "geometry hd"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by Walc on 2008-02-21
evening guys
i just experienced grub error 17 on my dual vista/ubuntu pc.
now ive read that tutorial: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Super_Grub_USB_Disk](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Super_Grub_USB_Disk)

and i wanna install super grub disk on my pendrive.

Now geometry(hd) command gives me 3 results: hd0, hd1, hd2. 
I know i have only one physicall hdd, on it i have 4 vista partitions and from one of it ive taken some space for linux. 
In this tutorial hd2 is the pendrive, but when i hit geometry (hd2) it returns me with:

> error 18: selected cylinder exceeds max supported by BIOS 
> partition num: 0-3
>drive 0x82: C/H/S = 1023/1/20, nr of sectors = 20479, /dev/sdg

is it my pendrive? <i have pqi 4 gb>

---

### Post by marufaberlin on 2008-02-22
Well... how have you formatted your pendrive? If you have grub installed on it, which root hd does it use? If it uses the pendrive as a root hd, then you should have the /boot/grub dir on it. Maybe you should check your grub config?:-?

---

