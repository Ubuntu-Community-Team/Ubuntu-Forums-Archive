---
title: "DVD playback Problem..."
date: 2006-05-10
forum: Absolute Beginner Talk
---

### Post by nip37 on 2006-05-10
I am a n00b to ubuntu and using it since last one month, i have every thing working fine except DVD, i installed all codecs restricted formats from wiki tried all different players totem, totem-xine, oogle, okle, my dvd-rom worked absolutly fine with windows so i know dvd-rom is ok
whenever i try to play it at totem i get this error
> Failed to play Audio/Video Disc
Failed to find mountpoint for device /dev/hdb in /etc/fstab
and other programmes like okle simply can not find disk in the drive?
i have tried everything, googled around for the solution but unfortunately cant find anywhere ](*,) 
below is the result for my /etc/fstab
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc1       /media/hdc1     ntfs    defaults        0       0
/dev/hdc5       /media/hdc5     ntfs    defaults        0       0
/dev/hdc4       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


thanx for your help.

---

### Post by Kobalt on 2006-05-10
What happens exactly when you insert your dvd ? What prompt do you have ?

---

### Post by nip37 on 2006-05-10
[QUOTE=Kobalt]What happens exactly when you insert your dvd ? What prompt do you have ?[/QUOTE]
when i insert DVD nothing happen, i mean like when i insert CD into CDROm, an icon apears on desktop but nothing like this happend when i insert DVD into DVD-ROM.
And if i try to open DVD by clicking on CD-ROM/DVD-ROM Drive this error shows
```
**Unable to mount the volume. There is probably no media in the device.**
Warning: device /dev/hdb is already handled by /etc/fstab, supplied label is ignored
mount: No medium found
Error: could not execute pmount

```
and if try to play it from totem
```
**Failed to play Audio/Video Disc**
Failed to find mountpoint for device /dev/hdb in /etc/fstab

```
and when try to play with okle it says
```
**Seems there is no disc in your DVD drive.**
If there is a disc in the drive make sure that /dev/dvd really refers to your DVD device or change the DVD device path in File -> Settings.

```

---

### Post by Perfect Storm on 2006-05-10
Are you on Dapper? I've similar problem with audio and DVD, if so would you like to add commen to the bug report for dapper I made some days ago: [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/43192](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/43192)

---

