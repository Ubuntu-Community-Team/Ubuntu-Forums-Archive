---
title: "Broke My Installation, HELP!!!"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by nothinghead on 2007-09-09
Ok, there's another post out there about my ipod, but to do what I needed to do with it, I needed to get into Windows so I used a "Lite" installation of XP on one CD.  It was supposed to be bootable and I thought it would be a good quick fix.

The setup program ran but wasn't able to make a partition or do anything without formatting an entire drive it seemed.  So I decided to cancel that and exit the setup.  I thought I could get back to Ubuntu to stake out a partition for the XP install.  However, when I tried to reboot it just hung at a blank screen with a blinking cursor.

I tried rebooting with a Super Grub Disk, it attempted to fix my MBR but couldn't do anything for me.  I played around with SGD a bunch and made no progress.

So, then I put in my live CD and tried to boot and at first it somehow was putting something out to my monitor that made my monitor say "format not supported."  So I had to try the live CD over again and start it in graphics safe mode.

If SGD is doing nothing how can I get my install back?  I know I stopped the installation program before it could format or partition anything.  I think my install must be there but I can't boot.  

I really don't know how to explain my problem better, but I would greatly appreciate anything you could tell me and give you any info that would help diagnose things.

---

### Post by SOULRiDER on 2007-09-09
If i were you I would check that the partitions are still there and that windows didnt do anything evil, just in case. When you reboot, you dont see GRUB at all? If you dont boot with the live CD and recover GRUB.

To recover GRUB follow this linki (I would follow the steps in #2 but #1 is ok too):
[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

---

### Post by nothinghead on 2007-09-09
How can I see if the partitions are still there from the Live CD?

And when I reboot it just shows me a totally blank screen with a blinking cursor that does nothing.

And Super GRUB disc couldn't repair anything.

---

### Post by SOULRiDER on 2007-09-09
Type
```
 df -h
```

---

### Post by nothinghead on 2007-09-09
I don't see my boot drive. 

> 
tmpfs                 470M   39M  432M   9% /lib/modules/2.6.20-15-generic/volatile
tmpfs                 470M   39M  432M   9% /lib/modules/2.6.20-15-generic/volatile
varrun                470M  100K  470M   1% /var/run
varlock               470M     0  470M   0% /var/lock
udev                  470M  112K  470M   1% /dev
devshm                470M     0  470M   0% /dev/shm
tmpfs                 470M   12K  470M   1% /tmp
/dev/sdb1             466G  289G  178G  62% /media/Media


/dev/sdb1 is my external/media drive

---

### Post by nothinghead on 2007-09-09
sudo fdisk -l gives me the following output

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
86 heads, 15 sectors/track, 378602 cylinders
Units = cylinders of 1290 * 512 = 660480 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      208090   134217727+   4  FAT16 <32M

Disk /dev/sda1: 137.4 GB, 137438952960 bytes
86 heads, 15 sectors/track, 208089 cylinders
Units = cylinders of 1290 * 512 = 660480 bytes

     Device Boot      Start         End      Blocks   Id  System
/dev/sda1p1   *           1      208090   134217727+   4  FAT16 <32M

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS

```

I think /dev/sda1 is my boot drive

---

### Post by nothinghead on 2007-09-09
I'm trying to use "sudo cp /dev/sda1" and copying it to an external HD.  It's saving it as an executable called "sda1."  Will this file be worth anything?

---

