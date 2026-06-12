---
title: "Hard disk drives not appearing in nautilus"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by canter690 on 2006-09-03
Hi

My problem is that the hard disk drives in my computer do not appear under Nautilus either before a mount or even after they are mounted.

```
sudo fdisk -l

Disk /dev/hda: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       14589   117186111   83  Linux

Disk /dev/hdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1       14593   117218241   83  Linux

Disk /dev/sda: 120.0 GB, 120033041920 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14215   114181956   83  Linux
/dev/sda2           14216       14593     3036285    5  Extended
/dev/sda5           14216       14593     3036253+  82  Linux swap / Solaris

Disk /dev/hdi: 240.0 GB, 240068231168 bytes
255 heads, 63 sectors/track, 29186 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdi1               1       29186   234436513+  83  Linux

```

```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdh        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1       /mnt/hda1       ext3    defaults        0       2
/dev/hdc1       /mnt/hdc1       ext3    defaults        0       2
/dev/hdi1       /mnt/hdi1       ext3    defaults        0       2
```

```
 df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            112388644   3137588 103541960   3% /
varrun                  518048        84    517964   1% /var/run
varlock                 518048         4    518044   1% /var/lock
udev                    518048       156    517892   1% /dev
devshm                  518048         0    518048   0% /dev/shm
lrm                     518048     18856    499192   4% /lib/modules/2.6.15-26-386/volatile
/dev/hda1            115345508    131228 109354976   1% /mnt/hda1
/dev/hdc1            115377640    131228 109385500   1% /mnt/hdc1
/dev/hdi1            230757428   8428564 210607040   4% /mnt/hdi1
```

and a picture of nautilus after all of the above.

Help :confused:

---

### Post by kinematic on 2006-09-03
i remember reading that your harddrives only appear under my computer if you mount them under /media so you might want to try that.

---

### Post by canter690 on 2006-09-03
Yup

Tried that.  No joy.

---

### Post by jorn on 2006-09-03
Have you made the directories in the first place?
> sudo mkdir /media/choose_a_name
and then:
> sudo mount /dev/hdi /media/choose_a_name

---

### Post by canter690 on 2006-09-03
Already tried but didn't work.

Even tried it again just now, just in case, still didn't work.

:(

---

### Post by jorn on 2006-09-03
To be sure please paste your new fstab with corrections.
to view your disks you must go to /media. Sorry if I point things out very clear.

---

### Post by canter690 on 2006-09-03
Didn't modify fstab to test this. Used following command sequence.

```
df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            112388644   3139364 103540184   3% /
varrun                  518048        84    517964   1% /var/run
varlock                 518048         4    518044   1% /var/lock
udev                    518048       156    517892   1% /dev
devshm                  518048         0    518048   0% /dev/shm
lrm                     518048     18856    499192   4% /lib/modules/2.6.15-26-386/volatile
/dev/hda1            115345508    131228 109354976   1% /mnt/hda1
/dev/hdc1            115377640    131228 109385500   1% /mnt/hdc1
sam@big-beast:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            112388644   3139444 103540104   3% /
varrun                  518048        84    517964   1% /var/run
varlock                 518048         4    518044   1% /var/lock
udev                    518048       156    517892   1% /dev
devshm                  518048         0    518048   0% /dev/shm
lrm                     518048     18856    499192   4% /lib/modules/2.6.15-26-386/volatile
/dev/hda1            115345508    131228 109354976   1% /mnt/hda1
/dev/hdc1            115377640    131228 109385500   1% /mnt/hdc1
```

then

```
sudo mkdir /media/hdi
sudo mount /dev/hdi1 /media/hdi

```

```
df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            112388644   3139444 103540104   3% /
varrun                  518048        84    517964   1% /var/run
varlock                 518048         4    518044   1% /var/lock
udev                    518048       156    517892   1% /dev
devshm                  518048         0    518048   0% /dev/shm
lrm                     518048     18856    499192   4% /lib/modules/2.6.15-26-386/volatile
/dev/hda1            115345508    131228 109354976   1% /mnt/hda1
/dev/hdc1            115377640    131228 109385500   1% /mnt/hdc1
/dev/hdi1            230757428   8428564 210607040   4% /media/hdi
```

see attached screen shot....no joy.

---

### Post by jorn on 2006-09-03
I made a typing mistake
> sudo mount /dev/hdi1 /media/hdi
should be:
> sudo mount /dev/hdi1 /media/hdi1
Then open nautilus, browse down to /media/hdi1
Is something there?
You will not be able to see it in My Computer.
hda1 and hdc1 you also have to mount in /media/

---

### Post by canter690 on 2006-09-03
Jorn

See my previous reply.  Noticed the typo in your response but understood what you meant.  Had already tried that and sadly to no avail.

Need some fresh ideas or areas to look at.

---

### Post by bodhi.zazen on 2006-09-03
Mount under /media, then

re-start gnome
```
Ctrl-alt-Backspace
```
Login.

---

### Post by canter690 on 2006-09-04
Well a big thank you to everyone.  Restarting gnome with ctrl-alt-backspace didn't actually do the trick on my system but a complete reboot did.  

Icons now appear on desktop as well.  :) 

I thought I read somewhere that by convention hard disks should be mounted under mnt and removeable media such as CDROMs and USB Drives should be mounted under media.  

Anyway - problem solved so thank you to all agin.
=D> =D> =D>

---

