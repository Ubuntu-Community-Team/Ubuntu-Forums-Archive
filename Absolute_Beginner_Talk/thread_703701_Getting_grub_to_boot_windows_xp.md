---
title: "Getting grub to boot windows xp"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by steelmole on 2008-02-21
Ok, so at the moment I had to reinstall ubuntu because lots of things were messed up with booting.  The fresh install works great, and boots into windows boot manager from grub.  I wanted to get xp to boot from grub, so I only used 1 boot menu instead of 2.  Here are the lines I added to menu.lst:
```
title		Windows XP
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```

But this just comes up with an error along the lines of "no boot manager, press ctr-alt-del to restart.  I don't know if this means I got the wrong partition (I don't think so, because I get a different message with other partitions).  Can someone tell me what I need to do to get windows xp to boot from grub.

---

### Post by louieb on 2008-02-21
Your XP entry looks ok. But you need to know in what partition XP is installed.
Please post the output of your partition table.

```
sudo fdisk -l
``` (lowecase L)

Probably just a matter of tweaking the **root (hd0,1)** line

---

### Post by steelmole on 2008-02-22
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x06100610

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2955    23736006    7  HPFS/NTFS
/dev/sda2   *        2956        6080    25100288    7  HPFS/NTFS
/dev/sda3            6081       60801   439546432+   f  W95 Ext'd (LBA)
/dev/sda5            6081       53445   380459331    7  HPFS/NTFS
/dev/sda6           53446       55995    20482843+   7  HPFS/NTFS
/dev/sda7           59643       60315     5405841   83  Linux
/dev/sda8           60316       60801     3903763+  82  Linux swap / Solaris
/dev/sda9           55996       59642    29294496   83  Linux

```

I'm pretty sure sda2 is the windows XP partition.  Atm I can boot to the windows vista boot manager and then get to xp from there.  Annoying really.

---

### Post by dstew on 2008-02-22
Are you sure the correct root isn't (hd0,0)? Another possibility is that there really is no boot loader on the partition. Maybe when you set up Vista boot manager it changes the XP boot loader somehow. You can install a boot loader on a Windows partition using the Recovery Console (on the Windows CD) command **fixboot**.

---

### Post by steelmole on 2008-02-22
I did a repair using vista, so that's probably what's changed the bootloader.  I'll find my windows xp disc and try using fixboot.  Thankyou.

---

