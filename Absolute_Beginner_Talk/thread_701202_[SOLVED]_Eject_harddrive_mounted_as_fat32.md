---
title: "[SOLVED] Eject harddrive mounted as /fat32?"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by Programmerer on 2008-02-19
Hi there, I have two harddrives, one with 200GB, and an other with 40GB.
I have installed Ubuntu 7.10 on the 200GB harddrive, and when I installed Ubuntu I made the 40GB harddrive to mount to /fat32 (For testing). The fat32 harddrive is formatted, and not in use.
But I wonder if I could eject it, and use it on an other computer without having to reinstall Ubuntu. I hope it won't be to difficult to remove the harddrive, when it is mounted to /fat32 on my Ubuntu harddrive:confused:

Thanks for helping.

---

### Post by hyper_ch on 2008-02-19
please post

```

sudo fdisk -l

```

and

```

df -l

```

---

### Post by Programmerer on 2008-02-19
I took a chance, and removed it, and after reinstalling Grub to MBR and rewrite the menu.lst file I deleted my /fat32 folder. And it works:)

But anyway:

> 
$ sudo fdisk -l
[sudo] password for "myusername":

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00006057

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6687    53713296   83  Linux
/dev/sda2            6688        7079     3148740   82  Linux swap / Solaris

Disk /dev/sdb: 2062 MB, 2062548992 bytes
16 heads, 32 sectors/track, 7868 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x6d552ec8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7868     2014192    b  W95 FAT32

$ df -l

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             52870076  30106024  20078388  60% /
varrun                  257920        88    257832   1% /var/run
varlock                 257920         0    257920   0% /var/lock
udev                    257920        72    257848   1% /dev
devshm                  257920         0    257920   0% /dev/shm
lrm                     257920     16488    241432   7% /lib/modules/2.6.22-14-generic/volatile
/dev/scd1              6928392   6928392         0 100% /media/cdrom1
/dev/sdb1              2010248   1656248    354000  83% /media/X


I had my USB in (/media/X)

Thanks for your interest, hope you understand my English:KS

---

### Post by hyper_ch on 2008-02-20
it's a USB drive then?

---

### Post by Programmerer on 2008-02-23
> **hyper_ch said:**
> it's a USB drive then?

No, I just had my USB stick inside when I ran the command, but thank you for replies:)

---

