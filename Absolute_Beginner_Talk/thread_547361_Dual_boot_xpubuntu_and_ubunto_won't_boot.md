---
title: "Dual boot xp/ubuntu and ubunto won't boot"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by cooCat122 on 2007-09-09
I had xp installed and working on hda and then installed ubuntu on hdb. When I boot grub comes up and show ubuntu and xp. If I choose xp it boots fine but when I choose ubuntu it goes to a blank screen with a blinking cursor and just sits there. Anyone have any suggestions?

---

### Post by alienexplorers on 2007-09-10
reload grub.  Follow the direction in my signature line.  Sounds like a bad install.

---

### Post by cooCat122 on 2007-09-10
This is what I did and I still can't get ubuntu to boot.

grub> find /boot/grub/stage1
 (hd1,0)

grub> root (hd1,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 d (hd0) (hd0)1+17 p (hd1,0)/boot/grub/stage2 /bo
ot/grub/menu.lst"... succeeded
Done.

grub> quit

menu.lst

#This doesn't work#
title           Ubuntu, kernel 2.6.20-15-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=f892174f-b1ec-4851-86ea-c877170258c2 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

#This does work#
title           Microsoft Windows XP Professional
root            (hd0,1)
savedefault
makeactive
chainloader     +1

---

### Post by Sef on 2007-09-10
Was there any problems with the Live CD?

---

### Post by hyper_ch on 2007-09-10
once in the live-cd, can you post the output of this:

```

sudo fdisk -l

```

(Not sure if the sudo is needed in the live-cd)

---

### Post by cooCat122 on 2007-09-10
> **Sef said:**
> Was there any problems with the Live CD?

There were no problems with the live cd.

---

### Post by cooCat122 on 2007-09-10
> **hyper_ch said:**
> once in the live-cd, can you post the output of this:

```

sudo fdisk -l

```

(Not sure if the sudo is needed in the live-cd)


$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8       19452   156191962+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19075   153219906   83  Linux
/dev/sdb2           19076       19452     3028252+   5  Extended
/dev/sdb5           19076       19452     3028221   82  Linux swap / Solaris

---

### Post by cooCat122 on 2007-09-12
Does anyone have anymore suggestions?

---

### Post by Tyke91 on 2007-09-12
dunno if this will help... here's part of my menu.lst file... it works (for me at least) :D

```
title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=2bd772a8-adbf-4012-8b66-f4cba87d1ef0 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault
```


obviously you would use (hd1,0) for yours... but otherwise..


EDIT: disregard this... i have a different kernel than you... oops

---

### Post by skymera on 2007-09-12
you sure you done your grub right?

0 = 1
1 = 2 
2 =3
etc

since you did hd1,0

im guessing its hard drvie 2 and partition 1?

---

### Post by slira on 2007-09-12
Hi

just another idea: you had "something" in the hdb before installing ubuntu?
I tried that one once and got the same error (that hdd was my backup disk; I had one partition with data and lots of free space, and tried to install unbuntu there) ..

then I cleaned the hdd and reinstalled ubuntu from scratch; all went well; I saved some space when made the ubuntu partitions and (after having ubuntu installed) I made another partition and copied data back there;

it's working with no problems. :)

Edit: Just remembered: Check that your device.map file in /boot/grub is correctly configured. it should be something like
```

(hd0)   /dev/hda
(hd1)   /dev/hdb

```

Hope it works for you too.
slira

---

### Post by cooCat122 on 2007-09-17
> **skymera said:**
> you sure you done your grub right?

0 = 1
1 = 2 
2 =3
etc

since you did hd1,0

im guessing its hard drvie 2 and partition 1?

I think I did. Yeah it is on drive 2.

---

### Post by cooCat122 on 2007-09-17
> **slira said:**
> Hi

just another idea: you had "something" in the hdb before installing ubuntu?
I tried that one once and got the same error (that hdd was my backup disk; I had one partition with data and lots of free space, and tried to install unbuntu there) ..

then I cleaned the hdd and reinstalled ubuntu from scratch; all went well; I saved some space when made the ubuntu partitions and (after having ubuntu installed) I made another partition and copied data back there;

it's working with no problems. :)

Edit: Just remembered: Check that your device.map file in /boot/grub is correctly configured. it should be something like
```

(hd0)   /dev/hda
(hd1)   /dev/hdb

```

Hope it works for you too.
slira

I checked device.map and it is the same as yours.
(hd0)   /dev/hda
(hd1)   /dev/hdb

The disk I installed on was brand new and empty.

Still no luck.

---

### Post by slira on 2007-09-17
sorry, no more ideas...
if something comes up, I'll post
best
slira

---

### Post by mikeize on 2007-09-18
I had a similar problem, that I finally solved.  my problem was that my grub menu file was wrong.  Using the live CD, I did sudo gedit to (my ubuntu disk/partition)/boot/grub/menu.lst
Scrolling down to the bottom, I realized that the disks/partitions were addressed all wrong.  I simply corrected them (ie, from hd1,0 to hd 0,0), etc.  
Another thing you check from the live cd, is you can run gparted, and make sure that the correct disk is flagged as 'boot'.  For some reason, one of my storage disks was labeled as boot, and that probably caused my menu.lst problem.  Hope this helps, good luck.

-mike

---

### Post by alienexplorers on 2007-09-18
Stupid question, but in cooCat122's fdisk -l list it shows 2 bootable partitions. One on each disk.  Why is that.  I am running dual disks with windows and Ubuntu 6.06 and mine only shows one bootable partition on the windows disk on drive hda1.

---

### Post by alienexplorers on 2007-09-18
Please check this out.

> This is what I did and I still can't get ubuntu to boot.

grub> find /boot/grub/stage1
(hd1,0)

grub> root (hd1,0)

grub> setup (hd0) 
[COLOR="Red"]should be setup (hd1)[/COLOR]

grub> quit


---

### Post by mikeize on 2007-09-18
> **alienexplorers said:**
> Stupid question, but in cooCat122's fdisk -l list it shows 2 bootable partitions. One on each disk.  Why is that.  I am running dual disks with windows and Ubuntu 6.06 and mine only shows one bootable partition on the windows disk on drive hda1.


I had the same thing on mine.  My main disk has 4 partitions:  XP, Feisty (home, / and swap).  XP was flagged as boot, so I switched it to my / partition.  My other disk is a piece of junk that I have some backup files on, but it is divided in half.  For some reason one of those was flagged as boot also.  They are formatted as ext3, but other than that...  I could have set it accidentally, when I was messing with the Super Grub disk.

side note:  I got mine to boot from the hard disk, it was a fresh install, so I loaded all the updates (including kernel), and rebooted...  wouldn't go!  wouldn't even boot the live cd or xp!  So I restarted and hit F2 to enter bios, and it booted the live cd!  I checked my menu.lst file, and it had the new kernel version, but had changed all the drive/partition designations back to the wrong thing!  So I switched them again, and was able to boot.  How can I make these settings persist?  It may be that only kernel upgrades will mess it up, but even so, I'd like to fix it completely.

-mike

---

### Post by cooCat122 on 2007-09-19
> **alienexplorers said:**
> Please check this out.

I went into grub and changed setup to hd1 and I am still not able to boot.

grub> find /boot/grub/stage1
(hd1,0)

grub> root (hd1,0)

grub> setup (hd1)

grub> quit

---

### Post by cooCat122 on 2007-09-19
I checked menu.lst and everything look good.

current setup
windows xp 
sda = hd0
sda1
sda2 *boot

sdb = hd1
sdb1 Linux * boot
sdb2 extended
sdb5 swap

still can boot into windows no problem but when I pick ubuntu from grub nothing.

---

### Post by Tirex on 2007-09-29
Cat,

I noticed that you have the Dell Utility partition.  I'm experiencing the same thing on a Dell.  I can boot into Windows XP.  And then when trying to boot into Linux after a reboot, it just hangs and nothing....

Sometimes if I keep restarting repeatedly it will on occasion let me into Ubuntu.

I even deleted the Dell partition and reinstalled Ubuntu and all its partitions and am still getting this problem.

I did notice that the Windows partition is flagged as boot.  Can anyone tell me how to change this back to the /boot partition I have?

---

