---
title: "Problem Building GRUB"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by Claude on 2006-08-10
[img]http://upit.be/uploads/images/hmm3111.png[/img]

i couldnt install it during the big install for some reason soi went without a bootloader and now im attempting to install one from the live cd, that is what i keep getting :\

---

### Post by syedn on 2006-08-10
it looks like you're missing the essential tools for building/compiling from source. (such as the gcc)

i'm not sure what to do though as i am relatively new to ubuntu/linux. sorry. :(

---

### Post by tehnad on 2006-08-10
from a terminal in your live cd type: sudo grub

It will say that it is probing devices and such then brings you to the grub prompt grub>

code: root(hdx,x)  replace x for your harddrive partitions that contain root.  example would be if your HD is 0 and root is on on partition 1 then it will be (hd0,0).

next code: setup (hdx)   replace x for your HD number.

next code: quit

Reboot your machine and you should be fine.  Grub will be in the MBR.

edit: This is how I installed grub back into the MBR on my machine with only one harddrive.

```
root(hd0,0)
setup (hd0)
quit
```

---

### Post by Claude on 2006-08-10
ya, i was missing a few essential package, fixed that

---

### Post by tehnad on 2006-08-10
So where you installing grub into the MBR or where you just compiling it on your system?

---

### Post by mlind on 2006-08-10
Why are you compiling GRUB?

You should probably install it from Ubuntu repositories, so it's already configured for Ubuntu system
```

sudo aptitude install grub

```

Then run **grub-install** /dev/xxx, where /dev/xxx is the device (not a partition!) where you want grub to be installed.

---

### Post by tehnad on 2006-08-10
Just a question about the device thing.  Isn't the first number the device and the second the partition root is on?  Or is all of it just refering to the device?

---

### Post by mlind on 2006-08-10
> **tehnad said:**
> Just a question about the device thing.  Isn't the first number the device and the second the partition root is on?  Or is all of it just refering to the device?

/dev/hda or /dev/sda refers to a physical device, where /dev/hda1 or /dev/sda1 refers to first partition on that device.

If you want to install grub on the MBR of you first IDE hdd (/dev/hda), you'd execute *grub-install /dev/hda*. If you use /dev/hda1 instead, you're screwed..

---

### Post by Claude on 2006-08-10
```

ubuntu@ubuntu:~$ sudo grub-install /dev/hda
Could not find device for /boot: Not found or not a block device.

```

i get that now

---

### Post by mlind on 2006-08-10
> **Claude said:**
> ```

ubuntu@ubuntu:~$ sudo grub-install /dev/hda
Could not find device for /boot: Not found or not a block device.

```

i get that now

Post the outputs of
```

sudo fdisk -l
df

```

---

### Post by Claude on 2006-08-10
Disk /dev/hda: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1275    10241406    7  HPFS/NTFS
/dev/hda2   *        1276        2428     9261472+  83  Linux
/dev/hda3            2429        2482      433755    5  Extended
/dev/hda5            2429        2482      433723+  82  Linux swap / Solaris

Disk /dev/hdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               2        4998    40138402+   f  W95 Ext'd (LBA)
/dev/hdb5               2         639     5124703+   7  HPFS/NTFS
/dev/hdb6             640        4487    30909028+   b  W95 FAT32
/dev/hdb7            4488        4998     4104576    b  W95 FAT32
ubuntu@ubuntu:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
unionfs                 894960    763460    131500  86% /
varrun                  257968        80    257888   1% /var/run
varlock                 257968         4    257964   1% /var/lock
udev                    257968       136    257832   1% /dev
devshm                  257968         0    257968   0% /dev/shm
lrm                     257968      9000    248968   4% /lib/modules/2.6.15-23-386/volatile
tmpfs                   257968        16    257952   1% /tmp
/dev/hdb7              4096556   3436328    660228  84% /media/windows

---

### Post by mlind on 2006-08-10
Did you install GRUB on livecd environment or on your actual root ?

You probably want GRUB on /dev/hda (which is first on boot order?)
```

sudo mount /dev/hda2 /mnt
sudo chroot /mnt /bin/bash

# just to be sure grub is installed
aptitude install grub
grub-install /dev/hda

```


Or use this nice HOWTO [http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

---

### Post by Claude on 2006-08-10
```

ubuntu@ubuntu:~$ sudo chroot /mnt /bin/bash
root@ubuntu:/# sudo aptitude install grub
Reading package lists... Done
Segmentation faulty tree... 0%
root@ubuntu:/# grub-install /dev/hda
bash: grub-install: command not found

```

:\

---

### Post by mlind on 2006-08-10
> **Claude said:**
> ```

ubuntu@ubuntu:~$ sudo chroot /mnt /bin/bash
root@ubuntu:/# sudo aptitude install grub
Reading package lists... Done
Segmentation faulty tree... 0%
root@ubuntu:/# grub-install /dev/hda
bash: grub-install: command not found

```

:\

Did you try updating the package lists first while on chroot environment?
```

aptitude update

```

(you don't need to use sudo because you're already logged as root)

---

