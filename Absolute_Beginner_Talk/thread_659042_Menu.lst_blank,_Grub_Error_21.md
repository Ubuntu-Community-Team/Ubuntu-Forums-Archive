---
title: "Menu.lst blank, Grub Error 21"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by dfault312 on 2008-01-05
I have two internal harddrives;

SCSI1(0,0,0)(sda) 80GB (windows xp installed here)
SCSI1(0,1,0)(sdb) 6.4GB (ubuntu installed here)

When I try to boot, GRUB gives error 21, so I tried checking menu.lst

sudo gedit /boot/grub/menu.lst

But the output is blank. What do I need to do to fix GRUB? The only thing I can boot right now is the live CD.

fdisk -l in case it helps.
> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe4651a0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9725    78116031    7  HPFS/NTFS

Disk /dev/sdb: 6448 MB, 6448619520 bytes
255 heads, 63 sectors/track, 784 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xba94ba94

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         743     5968116   83  Linux
/dev/sdb2             744         784      329332+   5  Extended
/dev/sdb5             744         784      329301   82  Linux swap / Solaris


---

### Post by skymera on 2008-01-05
err imn not a GRUB expert but try

```
 sudo update-grub 
```

or boot the live CD and reinstall grub

```

sudo grub
find /boot/grub/stage1
root (hd0,0)
setup (hd0)

```

change (hd0,0) to match your drive

---

### Post by overdrank on 2008-01-05
> **dfault312 said:**
> I have two internal harddrives;

SCSI1(0,0,0)(sda) 80GB (windows xp installed here)
SCSI1(0,1,0)(sdb) 6.4GB (ubuntu installed here)

When I try to boot, GRUB gives error 21, so I tried checking menu.lst

sudo gedit /boot/grub/menu.lst

But the output is blank. What do I need to do to fix GRUB? The only thing I can boot right now is the live CD.

fdisk -l in case it helps.

Hi and please correct me if I am wrong but when booting the live cd and you enter that command it will be black. You will need to mount your drive and view the menu.lst from nautilus.

---

### Post by dfault312 on 2008-01-07
i figured it out! i feel really dumb, but the reason grub was giving error 21 is because the secondard hard drive was turned off in the bios. i turned it on, tried booting again, and it worked perfectly. thanks for your replies.

---

