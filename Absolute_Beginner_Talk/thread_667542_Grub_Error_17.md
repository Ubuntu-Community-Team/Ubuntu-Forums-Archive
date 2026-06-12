---
title: "Grub Error 17"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by Squizz on 2008-01-14
Hi there

Grub is being nasty to me and won't let me boot.  It's been working fine with Feisty and then Gutsy for the last few months.  At present, I'm running Ubuntu from a Live CD and so I can't great a Supergrub CD (which seems like the most sensible thing to do).

From the live CD, I have a /boot/ folder, but no /grub/ folder within it - so no menu.lst either.

If I try to reinstall Grub, I get this.

```

ubuntu@ubuntu:~$ sudo grub-install /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.

```

I have also tried going into my BIOS and setting all of my hard drives to AUTO, but this made no difference either.

I've also tried creating a boot/grub/ folder and putting a new menu.lst file in there - but that didn't work either.

Any ideas?

---

### Post by philinux on 2008-01-14
Try this

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0)

---

### Post by Squizz on 2008-01-14
I tried something similar from an older thread already.

I can get "sudo grub" up, but the pressing tab does nothing .

Also typing "find /boot/grub/stage1"

gives me "Error 15: File not found"

I then tried using details from my old menu.lst which gave me 

```

grub> root (hd1,0)    
root (hd1,0)
grub> setup (hd1)   
setup (hd1)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found

```

---

### Post by Squizz on 2008-01-14
um, just noticed something.

This is my current output of sudo fdisk -l

```

Disk /dev/hda: 82.3 GB, 82348277760 bytes
240 heads, 63 sectors/track, 10637 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       10636    80408128+   7  HPFS/NTFS

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x62b52755

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       48641   390706232    b  W95 FAT32

```

The last time I needed to post the outcome of that command, it gave me;

```

Disk /dev/hda: 82.3 GB, 82348277760 bytes
240 heads, 63 sectors/track, 10637 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       10636    80408128+   7  HPFS/NTFS

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19271   154794276   83  Linux
/dev/sda2           19272       19457     1494045    5  Extended
/dev/sda5           19272       19457     1494013+  82  Linux swap / Solaris

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       48641   390706232    b  W95 FAT32

```

Does that look like I've lost a hard drive????

---

### Post by SOULRiDER on 2008-01-14
It sort of does =/ for some reason its not showing up at all.. reboot and try again, just in case. Also, make sure all the connections are OK.

---

### Post by dstew on 2008-01-14
Yes, installing grub according to [this document]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0") assumes you have an Ubuntu hard disk system there, and you only need to get it to boot. From your fdisk output, it looks like the original sda disk that had your Ubuntu system is not being detected.

---

### Post by Squizz on 2008-01-14
Looks like it was just a loose SATA connection.  Not sure if it's a dodgy connection or just a loose wire though as my machine hadn't been moved or anything prior, so time for a massive backup I think!

---

