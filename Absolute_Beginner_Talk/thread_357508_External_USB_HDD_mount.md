---
title: "External USB HDD mount"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by Omnisuite on 2007-02-09
I have two external hard drives: one is firewire and the other is usb2. The firewire mounts automatically without having to change fstab. The usb one is a 500gb my book from WD. It does not mount when ubuntu boots up or if i turn it on after. How do I get it to mount automatically? (Not sure if it matters, but im currently using Breezy) Thanks

---

### Post by taurus on 2007-02-09
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by Omnisuite on 2007-02-09
sudo fdisk -l

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19456   156280288+   7  HPFS/NTFS

Disk /dev/hdb: 30.7 GB, 30738677760 bytes
255 heads, 63 sectors/track, 3737 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        3581    28764351   83  Linux
/dev/hdb2            3582        3737     1253070    5  Extended
/dev/hdb5            3582        3737     1253038+  82  Linux swap / Solaris

Disk /dev/sda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        7475    60042906    6  FAT16

---

### Post by taurus on 2007-02-09
Is it on and plugs in because I don't see it anywhere from the list?

---

### Post by Atmuh on 2007-02-09
I actually have the same issue. Here is my output for that command.

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8342    67007083+   7  HPFS/NTFS
/dev/sda2            9177        9729     4437720   12  Compaq diagnostics
Partition 2 does not end on cylinder boundary.
/dev/sda3            8394        9176     6289447+  83  Linux
/dev/sda4            8343        8393      409657+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24321   195358401    7  HPFS/NTFS

---

### Post by taurus on 2007-02-09
> **Atmuh said:**
> I actually have the same issue. Here is my output for that command.

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8342    67007083+   7  HPFS/NTFS
/dev/sda2            9177        9729     4437720   12  Compaq diagnostics
Partition 2 does not end on cylinder boundary.
/dev/sda3            8394        9176     6289447+  83  Linux
/dev/sda4            8343        8393      409657+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24321   195358401    7  HPFS/NTFS

Which one you want to mount now, /dev/sda1 or /dev/sdb1?

---

### Post by Atmuh on 2007-02-09
> **taurus said:**
> Which one you want to mount now, /dev/sda1 or /dev/sdb1?

/dev/sdb1

---

### Post by taurus on 2007-02-09
> **Atmuh said:**
> /dev/sdb1

```
sudo mkdir /media/sdb1
sudo mount -t ntfs /dev/sdb1 /media/sdb1 -o nls=utf8,umask=0222
df -h
```

---

### Post by Omnisuite on 2007-02-09
The drive is on and plugged in. If I boot up in Windows, it finds the drive.

---

### Post by Atmuh on 2007-02-09
Oh I think I was asking the wrong question. It is a read-only drive in ubuntu but I want to make it writable.

---

### Post by Omnisuite on 2007-02-09
Writing to an NTFS partition is usually a bad idea.

---

### Post by taurus on 2007-02-09
> **Atmuh said:**
> Oh I think I was asking the wrong question. It is a read-only drive in ubuntu but I want to make it writable.

Then you need to use ntfs-3g instead of ntfs to mount it.

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by Omnisuite on 2007-02-09
The WD My Book is suppoed to turn on and off with the computer, which it seems to do fine with windows, but doesn't seem to be recognized when booting into Ubuntu. It came formatted with FAT (32?) and other usb drives are recognized just fine on ubuntu for me. Any ideas on why this one isn't being recognized or something else I might try to figure out what the problem could be?

---

### Post by dannyboy79 on 2007-02-09
i disagree, the ntfs-3g has actually just been released at RC1. [http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)
this thread will help you set it up. [http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g](http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g)

if you have a external usb device, make sure it's NOT in fstab and it should just appear when you plug it in. if it's fat or fat32 or ext3 it should mount with read/write support. it's handled by pmount. there is TONS of threads already regarding this issue just search of it.

---

### Post by dannyboy79 on 2007-02-09
> **Omnisuite said:**
> The WD My Book is suppoed to turn on and off with the computer, which it seems to do fine with windows, but doesn't seem to be recognized when booting into Ubuntu. It came formatted with FAT (32?) and other usb drives are recognized just fine on ubuntu for me. Any ideas on why this one isn't being recognized or something else I might try to figure out what the problem could be?

it's possible that your usb port isn't giving off enough power. is this a dual boot machine? if it is than that's not the problem. i am surprised that WD doesn't have a power plug. or does it? I am assuming it doesn't based on the comment you made that the computer turns it on and off when you turn the computer off and on.

---

### Post by Omnisuite on 2007-02-09
It is a dual boot with 2 internal drives, windows xp and ubuntu breezy. The WD my book has its own power, but its just supposed to turn itself off when you turn the comp off. I wasn't sure if that might be related to the problem so I included it. I have tried plugging it in after Ubuntu boots and before. Same problem though.

---

### Post by dannyboy79 on 2007-02-09
this is a problem like i suggested, power issue I bet. it's been discussed since march of 2006. check it out here, [http://ubuntuforums.org/showthread.php?p=1713035](http://ubuntuforums.org/showthread.php?p=1713035)
sorry, you might be out of luck on this one if you can't get more power to it because I can tell you that i have a 500gb wd hard drive that I hooked a generic usb to ide adapter to it WITH external power and I have no issues!

---

### Post by louieb on 2007-02-09
I have a WD my book also. Rebooting the computer  does not seem to affect its on off state. When I want it on I have to push the button,  then is shown up ready for use. Doesn't matter if I'm rebooting to Ubuntu or XP. Don't power down the PC often so can't remember what a shutdown and power off does.

---

### Post by dannyboy79 on 2007-02-09
oh, well thanks for posting this. the way the other uy made it sound was that there was no power button and that it was just suppose to turn on wehn the computer turns on. I am glad this drive works as I am sure many people have these or will get them.

---

### Post by Omnisuite on 2007-02-09
power button on 500gb WD my book seems to have no helpful effect.
I did find some more info [here]("http://ubuntuforums.org/showthread.php?t=271600") but not enough to solve the problem.

---

### Post by hazyumps on 2008-02-12
> **Omnisuite said:**
> The WD My Book is suppoed to turn on and off with the computer, which it seems to do fine with windows, but doesn't seem to be recognized when booting into Ubuntu. It came formatted with FAT (32?) and other usb drives are recognized just fine on ubuntu for me. Any ideas on why this one isn't being recognized or something else I might try to figure out what the problem could be?

I was having the same problem with my WD MyBk 250...i had to go into windows and safely remove hardware (WD 250gB), unplug it, then plug it in after bootup. may help

---

