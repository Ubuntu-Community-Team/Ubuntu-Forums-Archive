---
title: "WD Passport external drive not working, help?"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by leathco on 2008-02-04
having an odd problem with my external hard drive I just got, a Western Digital 160 gig USB hard drive.  Drive is recognized in XP and Vista, so it's not hardware related.  Drive is also formatted in FAT32.  

chris@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc202b441

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris
chris@ubuntu:~$

Doesn't even look like the OS sees it as a drive at all.  The 120 is the internal drive.  

Running Ubuntu 7.10

Any ideas?

---

### Post by pdub on 2008-02-04
What does dmesg show when you connect the drive?

```
dmesg | tail
```

---

### Post by wormser on 2008-02-04
I have one of those drives.  It worked perfectly in Ubuntu with out having to do a thing.  Did you 'safely remove hardware' when using XP?  Sometimes drives to not like to be recognized when removed improperly and some flag is set.  Try plugging it into the XP box and use the safely remove hardware.  Then plug it back into the Ubuntu box.  Make sure you unmount it when running in Ubuntu.

---

### Post by Rocket2DMn on 2008-02-04
I would say check to make sure the cable is very secure.  My roommate's WD Passport did this yesterday, turned out to be the cable wasn't very tight :)

---

### Post by leathco on 2008-02-04
Odd, after a second reboot it recognized it, but two times over.  There are two icons for it on the desktop.  Only one in the Places dropdown menu though.  But it works, that's all I care about.  Thanks.

---

