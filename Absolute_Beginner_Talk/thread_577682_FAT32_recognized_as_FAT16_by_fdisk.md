---
title: "FAT32 recognized as FAT16 by fdisk"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by sonic167 on 2007-10-16
I just bought a Freecom MediaPLayer 350 WLAN multimedia drive with NDAS, which comes with a hard drive already formated in FAT32 (as it seems .... when connecting it via USB). 
However, when trying to mount it via wifi (and the Ximeta drivers), fdisk shows a partition in FAT16, and therefore only mounts with "msdos" filesystem type:

vincent@oxbow:~$ sudo fdisk -l /dev/ndas-37018340-0

Disk /dev/ndas-37018340-0: 250.0 GB, 250057252864 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

                Device Boot      Start         End      Blocks   Id  System
/dev/ndas-37018340-0p1               1       30401   244196001    6  FAT16

Then I have the following in fstab to mount it automatically:
/dev/ndas-37018340-0p1 /mnt/MediaPlayer msdos defaults,user,noauto 0 0

The problem is the file names show with the infamous 8 character limit (like abcdef~1), which sucks.

Any idea why I can't mount this drive as FAT32 (vfat)?

Thanks,

Vince.

---

### Post by kellemes on 2007-10-16
> **sonic167 said:**
> I just bought a Freecom MediaPLayer 350 WLAN multimedia drive with NDAS, which comes with a hard drive already formated in FAT32 (as it seems .... when connecting it via USB). 
However, when trying to mount it via wifi (and the Ximeta drivers), fdisk shows a partition in FAT16, and therefore only mounts with "msdos" filesystem type:

vincent@oxbow:~$ sudo fdisk -l /dev/ndas-37018340-0

Disk /dev/ndas-37018340-0: 250.0 GB, 250057252864 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

                Device Boot      Start         End      Blocks   Id  System
/dev/ndas-37018340-0p1               1       30401   244196001    6  FAT16

Then I have the following in fstab to mount it automatically:
/dev/ndas-37018340-0p1 /mnt/MediaPlayer msdos defaults,user,noauto 0 0

The problem is the file names show with the infamous 8 character limit (like abcdef~1), which sucks.

Any idea why I can't mount this drive as FAT32 (vfat)?

Thanks,

Vince.

In fstab.. shouldn't msdos be be replaced with vfat?
That's how I mount fat32.

---

### Post by sonic167 on 2007-10-16
> **kellemes said:**
> In fstab.. shouldn't msdos be be replaced with vfat?
That's how I mount fat32.

Thanks for suggesting. I have not tried in fstab, but trying to  mount manually with the following command fails:

mount -t vfat /dev/ndas-37018340-0 /mnt/MedaiPlayer

It fails with the error:

mount: wrong fs type, bad option, bad superblock on .....

So I doubt it will work in fstab, but I'll try.

Vince.

---

### Post by kellemes on 2007-10-16
I guess I wasn't paying attention..
The drive **is** FAT16.
So you have to deal with the long-filename issue **or** reformat the drive.

---

### Post by stchman on 2007-10-16
> **kellemes said:**
> In fstab.. shouldn't msdos be be replaced with vfat?
That's how I mount fat32.

Yes, in fstab use the following:

fat - fat
fat32 - vfat
ntfs - ntfs
ntfs - ntfs-3g (if you wish to write to NTFS partitions, requires ntfs-3g package to be installed)

---

### Post by sonic167 on 2007-10-17
Thanks for the inputs.

Then, why does connecting it via the USB2.0 port make the drive show as FAT32?

The doc for this drive doesn't talk about FAT16 at all. It only talks about being supported when formated in either FAT, FAT32 or NTFS.

Why would they "factory" format it in FAT16?

Does it sound like the best option is to reformat it in FAT32, so it works for both w2k and Ubuntu and via both USB and wifi?

When reformating, the doc talks about having a limitation of 32Gb per partition in FAT32, which for a 250Gb drive would need 7 or so partitions, which sort of sucks. Is there a way around this? Currently there is only one partition (although FAT16!), which is easier to deal with.

I don't have much on the drive yet, so reformating is doable, but is there a way to just "convert" the drive from FAT16 to FAT32 (and keep a single partition)?

Thanks,

Vince

---

### Post by sonic167 on 2007-10-18
Also, which app should I use to get a single FAT32 partition (for 250Gb)?

Thanks,

Vince.

---

