---
title: "[SOLVED] Lost drive."
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by squrl on 2007-01-07
Somewhere I lost a hard drive. Primary SATA holds ubuntu. I added a 120g drive to the secondary master position and set it up as ext3 partion and formatted it. Then went through grub to get the booting straight. 

Everything works fine and boots right. I just can't find the new hard drive. If I understand this I have to find it and get the designator and add it to fstab file.  How do I locate the drive??

---

### Post by riven0 on 2007-01-07
Did you try doing** sudo fdisk -l** to see if Ubuntu recognizes it?

---

### Post by gibbylinks on 2007-01-07
Hi

Go to system > administration > device driver - then  go down the list looking for IDE or SATA devices. when you find your drive click on it then the advanced TAB and you should be able to see what you have to mount in FSTAB i.e. /dev/sda1 or whatever

I'm sure if you do a search in the forums you'll find plenty of help for setting up the FSTAB

8)

---

### Post by squrl on 2007-01-07
I only see one disk here. The new one should be about 110 gig.


squrl@squrl-desktop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19080   153260068+  83  Linux
/dev/sda2           19081       19457     3028252+   5  Extended
/dev/sda5           19081       19457     3028221   82  Linux swap / Solaris

---

### Post by squrl on 2007-01-07
Under system - administration - there is no such animal as device driver.

---

### Post by riven0 on 2007-01-07
From what I know, Ubuntu will not recognize a hd if the motherboard does not recognize it. When you restart the comp, can you go into the BIOS and make sure it shows up there? Maybe something is not plugged in completely?

---

### Post by squrl on 2007-01-07
I finally found the missing drive and it says it is as follows.

/etc/sdb1  7cb60066-0b75-4149-2e24-20ac86ee1ffc

Can someone tell me what the string should look like in fstab to add this drive for it to be mounted on boot up. By the way it has only one partition and is ext3.

Thanks

---

