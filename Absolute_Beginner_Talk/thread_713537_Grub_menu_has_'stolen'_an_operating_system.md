---
title: "Grub menu has 'stolen' an operating system"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by Kevin Jones on 2008-03-02
I recently installed Ubuntu 7.10 on a Dell xps 210
Before installing I was able to boot either windows vista, or Suse 10.3
I am unable to boot suse 10.3 since it is not on the boot menu.
I am fairly sure that the suse system has not been deleted. 
If any one can tell me how to check the system to ensure that the suse 10.3 is still available I would be grateful!
If any one can help me re-write the grub menu to show suse as an option, I would like to have a go at at. (I am very new, and my command line skills are not much)

Kevin

---

### Post by seventhc on 2008-03-02
If your in ubuntu open a terminal and paste or type this in
```
sudo fdisk -l
```
This should show you your partitions.

---

### Post by Kevin Jones on 2008-03-02
Thanks for the quick response 
This is a copy of  fdisk -l
Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e1a70

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       14499       21580    56886165    7  HPFS/NTFS
/dev/sda2           23866       27048    25567447+   5  Extended
/dev/sda3               1         262     2104483+  82  Linux swap / Solaris
/dev/sda4             263       14498   114350670   83  Linux
/dev/sda5           23866       27048    25567416   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 4127 MB, 4127194624 bytes
255 heads, 63 sectors/track, 501 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x91f72d24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         502     4030432    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(500, 254, 63) logical=(501, 196, 14)
kevin@kevin-desktop:~$ 


I am sure the suse OS is sda 5
I am don't know if the extended partition is a problem.
Does this report help?

thanks for the help

Kevin

---

### Post by seventhc on 2008-03-02
you might just need to add it into grub then, it's been so long since I've added anything to grub, I'm not sure what you need. Someone here will probably be able to tell you what to add.

---

### Post by bhold on 2008-03-02
I highly recommend the super grub disk for investigating and repairing grub problems. Although the main web site for the super grub disk seems to be down at this time, you can also get a lot of info here...
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

I have tried about half a dozen linux distros, and usually keep about 3 at a time available for multi-boot. I won't go into more detail about how I handle your current situation however, because you have Windows in your mix which I think changes things and I don't have that experience yet.

---

