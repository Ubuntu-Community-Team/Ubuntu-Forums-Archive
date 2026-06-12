---
title: "[SOLVED] Grub+sata+ide= Not Playing Well Together"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by kindafunnylookin on 2008-01-07
I have Gutsy on my SATA and XP on my IDE. I cannot get GRUB to boot the IDE drive. I have tried Super Grub and the "Herman Zone" and I can still not figure it out. Please help if you can. Here are the most important outputs:
```
peter@Gutsy7_10:~$ sudo fdisk -l
[sudo] password for peter:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006f4f3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29644   238115398+  83  Linux
/dev/sda2           29645       30401     6080602+   5  Extended
/dev/sda5           29645       30401     6080571   82  Linux swap / Solaris

Disk /dev/hdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfe47c63f

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       16708   134206978+   7  HPFS/NTFS
peter@Gutsy7_10:~$ 

```and my /boot/grub/menu.lst
```

## ## End Default Options ##

title        Ubuntu 7.10, kernel 2.6.22-14-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=59705f2a-e24e-4303-aa6d-2d484d52e041 ro quiet splash
initrd        /boot/initrd.img-2.6.22-14-generic
quiet

title        Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=59705f2a-e24e-4303-aa6d-2d484d52e041 ro single
initrd        /boot/initrd.img-2.6.22-14-generic

title        Ubuntu 7.10, kernel 2.6.20-16-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=59705f2a-e24e-4303-aa6d-2d484d52e041 ro quiet splash
initrd        /boot/initrd.img-2.6.20-16-generic
quiet

title        Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=59705f2a-e24e-4303-aa6d-2d484d52e041 ro single
initrd        /boot/initrd.img-2.6.20-16-generic

title        Ubuntu 7.10, kernel 2.6.20-15-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=59705f2a-e24e-4303-aa6d-2d484d52e041 ro quiet splash
initrd        /boot/initrd.img-2.6.20-15-generic
quiet

title        Ubuntu 7.10, kernel 2.6.20-15-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=59705f2a-e24e-4303-aa6d-2d484d52e041 ro single
initrd        /boot/initrd.img-2.6.20-15-generic

title        Ubuntu 7.10, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title        My Windows XP on the IDE hard drive
root        (hd1,0)
configfile     /boot/grub/menu.lst
```

---

### Post by Tekno_Cowboy on 2008-01-07
Try changing the windows entry to:

```
title        My Windows XP on the IDE hard drive
root        (hd1,0)
chainloader +1
```

---

### Post by kindafunnylookin on 2008-01-07
Thanks. This is the first positive thing that's happened in this 2 week long process. After adding chainloader +1 the grub response is > Starting Up.....
then nothing boots but that's probably because I've screwed up the XP installation in all my experementing. 
I will install again tomorrow and give it a shot again. At least my GRUB problem is solved.

---

### Post by Tekno_Cowboy on 2008-01-07
You should try Super Grub Disk before reinstalling. It can boot darn near anything, and it's free. Google it and it should be the first link that pops up.

---

