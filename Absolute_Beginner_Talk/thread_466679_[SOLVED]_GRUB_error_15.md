---
title: "[SOLVED] GRUB error 15"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by Malalo on 2007-06-07
Ok I'm getting this pesky error 15 while GRUB is loading.

I installed Ubuntu 7.0.4 from the LiveCD. I had the GRUB error 18 at first, and Google told me it had to do with my older hardware's BIOS that can't read a partition of more than X Gb (can't remember the exact number...) So I created the following partitions (results from "sudo fdisk -lu") :

[COLOR="Red"][I]Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63     3004154     1502046   83  Linux
/dev/hda2         3004155    32997509    14996677+  83  Linux
/dev/hda3        32997510   398283479   182642985   82  Linux swap / Solaris[/I][/COLOR]

Here's /etc/fstab :

[I][COLOR="Red"]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2	/               ext3    defaults,errors=remount-ro 0       1
/dev/hda1	/boot           ext3    defaults        0       2
/dev/hda3	none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0[/COLOR][/I]

So as you can see, first partition is /boot, of more or less 1,5 Gb. Finally, the relevant information in Grub's Menu.lst file :

[I][COLOR="Red"]title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,0)
kernel          /vmlinuz-2.6.20-15-generic root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,0)
kernel          /vmlinuz-2.6.20-15-generic root=/dev/hda2 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet
[/COLOR][/I]

Soooooo I have NO idea where this error 15 is coming from. 
Anyone have an idea ?

Thanks for your help !

---

### Post by alienexplorers on 2007-06-07
Could you post the following items
> sudo fdisk -l
> df -h

---

### Post by Malalo on 2007-06-07
Yes of course !

"sudo fdisk -l" :

[COLOR="Red"][I]Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         187     1502046   83  Linux
/dev/hda2             188        2054    14996677+  83  Linux
/dev/hda3            2055       24792   182642985   82  Linux swap / Solaris[/I][/COLOR]

"df -h" :

[I][COLOR="Red"]Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 506M   33M  473M   7% /lib/modules/2.6.20-15-generic/volatile
tmpfs                 506M   33M  473M   7% /lib/modules/2.6.20-15-generic/volatile
varrun                506M  100K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   80K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
tmpfs                 506M   68K  506M   1% /tmp
/dev/hda2              15G  2.0G   12G  15% /media/disk
/dev/hda1             1.5G   51M  1.3G   4% /media/disk-1[/COLOR][/I]

---

### Post by Malalo on 2007-06-07
Can anyone provide help with this problem ?

---

