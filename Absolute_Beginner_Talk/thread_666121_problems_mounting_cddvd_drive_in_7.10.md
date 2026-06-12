---
title: "problems mounting cd/dvd drive in 7.10"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by e1ektrob0y on 2008-01-13
guys, i have this problem with my dvd drive. right click mount volume on cdrom1 i get an error that says 
```
unable to mount selcted volume. special device /dev/scd0 does not exist
```

I can watch avi files from the drive from a disk but when i try to select the input device in gxine, i get the same error as above?

---

### Post by Xavieran on 2008-01-13
That's very strange...:confused:

Can you mount it like so:

```
sudo mount /dev/cdrom /media/cdrom
```

If that doesn't work replace cdrom with scd0

---

### Post by e1ektrob0y on 2008-01-13
this is what i get from your suggestion...

```
mediabot@mediabot-desktop:~$ sudo mount /dev/cdrom1 
[sudo] password for mediabot:
mount: /dev/hda already mounted or /media/ANGEL_S5_DISC1 busy
mount: according to mtab, /dev/hda is already mounted on /media/ANGEL_S5_DISC1
mediabot@mediabot-desktop:~$ sudo mount /dev/cdrom1 /media/cdrom0/
mount: block device /dev/hda is write-protected, mounting read-only

```
here is fstab for the record...
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=6aba017f-79a8-4169-b500-c3b5b5458230 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=387939aa-2e0a-41e9-bbeb-7f1f3b7931f6 /home           ext3    defaults        0       2
# /dev/sda2
UUID=d1ad942b-3f82-4cc4-9601-600e276a934a none            swap    sw              0       0
/dev/scd0        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

---

