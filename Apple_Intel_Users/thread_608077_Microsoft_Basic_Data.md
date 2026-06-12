---
title: "Microsoft Basic Data"
date: 2007-11-09
forum: Apple Intel Users
---

### Post by asymmetric on 2007-11-09
hi!

i've been trying to repartition my macbook's harddrive, but i've had quite a lot of problems so far.. due to a stupid mistake, i have resized the hfs+ partition and created 2 Microsoft Basic Data partitions.

This is the output of diskutil list
```
lrnzs-computer:~ lrnz$ diskutil list
/dev/disk0
   #:                   type name               size      identifier
   0:  GUID_partition_scheme                    *149.1 GB disk0
   1:                    EFI                    200.0 MB  disk0s1
   2:              Apple_HFS Macintosh HD       60.0 GB   disk0s2
   3:   Microsoft Basic Data                    5.0 GB    disk0s3
   4:   Microsoft Basic Data                    83.7 GB   disk0s4
```

now, since i DO NOT want to install Windows on this machine, how can i reformat the last 2 partitions, in order to have them be recognized as Linux partitions?
I have tried booting via OSX's install cd and using  both diskutil and gpt, but with no success, as the partitions' type remains unchanged.

Can i use GParted (maybe via livecd)?

thanks 4 your help
asymmetric

---

### Post by cyberdork33 on 2007-11-09
> **asymmetric said:**
> hi!

i've been trying to repartition my macbook's harddrive, but i've had quite a lot of problems so far.. due to a stupid mistake, i have resized the hfs+ partition and created 2 Microsoft Basic Data partitions.

This is the output of diskutil list
```
lrnzs-computer:~ lrnz$ diskutil list
/dev/disk0
   #:                   type name               size      identifier
   0:  GUID_partition_scheme                    *149.1 GB disk0
   1:                    EFI                    200.0 MB  disk0s1
   2:              Apple_HFS Macintosh HD       60.0 GB   disk0s2
   3:   Microsoft Basic Data                    5.0 GB    disk0s3
   4:   Microsoft Basic Data                    83.7 GB   disk0s4
```now, since i DO NOT want to install Windows on this machine, how can i reformat the last 2 partitions, in order to have them be recognized as Linux partitions?
I have tried booting via OSX's install cd and using  both diskutil and gpt, but with no success, as the partitions' type remains unchanged.

Can i use GParted (maybe via livecd)?

thanks 4 your help
asymmetric
No issue.

Boot your Ubuntu CD, use the partition editor to delete the two partitions. Then start the installer and tell it to use the free space.

BTW, diskutil will always say Microsoft Basic Data even after you format it to a linux partition.

---

### Post by asymmetric on 2007-11-09
great thanks!!

---

### Post by asymmetric on 2007-11-10
doea anyone know how i can set a fat16 drive (a usb pen) as Bootable ?

i've tried diskutil, but it offers nothing like that.. what a crappy tool..

thanks again
asy

---

### Post by pxwpxw on 2007-11-10
> **asymmetric said:**
> doea anyone know how i can set a fat16 drive (a usb pen) as Bootable ?

i've tried diskutil, but it offers nothing like that.. what a crappy tool..

thanks again
asy

Boot flags can be set by fdisk or parted in ubuntu, but that wont make it bootable, depends on the system.

---

### Post by cyberdork33 on 2007-11-10
If you would like to be able to boot it on most PC's, then you need to set the partition as bootable. You can do this in gParted (just make sure you select the right disk!).

What exactly are you trying to do?

---

