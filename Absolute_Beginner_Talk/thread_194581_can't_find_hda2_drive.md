---
title: "can't find hda2 drive"
date: 2006-06-11
forum: Absolute Beginner Talk
---

### Post by sbuntu on 2006-06-11
Hi

I dont see second hard drive on my machine.
I dont think i mounted the second hard drive during installation

Did i do something wrong ?

While installing i didnt specify the partitions, i let the linux decide it i.e i chose the option of installing everything on the drive 1 since it said its the best way of doing it.

Please tell me if there was a better way of doing it if i had 2 drives like this so that
next time i do the right way.




sb@athena:/home/anyone$ sudo fdisk -l

Disk /dev/hda: 3166 MB, 3166765056 bytes
255 heads, 63 sectors/track, 385 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start       End      Blocks         Id  System
/dev/hda1   *           1          364     2923798+   83  Linux
/dev/hda2             365         385      168682+     5  Extended
/dev/hda5             365         385      168651       82  Linux swap / Solaris

Disk /dev/hdc: 3228 MB, 3228696576 bytes
16 heads, 63 sectors/track, 6256 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
sb@athena:/home/anyone$ df -l


Filesystem      1K-blocks   Used        Available Use% Mounted on
/dev/hda1       2877840   1335156   1396496  49%     /
varrun            128144        84           128060   1%      /var/run
varlock           128144         4            128140   1%      /var/lock
udev               128144        68           128076   1%     /dev
devshm          128144         0            128144   0%     /dev/shm
lrm                 128144     18856    109288  15% /lib/modules/2.6.15-23-386/volatile****

---

### Post by djsroknrol on 2006-06-11
That doesn't sound right...

Can you post your output of /etc/fstab

---

### Post by sbuntu on 2006-06-11
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by djsroknrol on 2006-06-11
what's on the drive ? How is it formated ?...

You can always write it into fstab in terminal

```
sudo gedit /etc/fstab
```

It would look something like this, depending on your drive format

```
/dev/**hdb**1 / ext3 defaults,errors=remount-ro 0 1
```

---

