---
title: "Problem mounting 2nd hardrive:"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by gu014 on 2007-01-30
Hello,
I am having a problem mounting my 2nd hardrive. I have installed the 2nd hardrive, formatted it as ext3 and need to be able to read and write to it.  I am trying to mount it to /mnt/WDCaviar.

Here is my /etc/fstab file:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=366695cd-f270-462c-8a12-41a19bf3d3e2 /               ext3    defaults,errors=remount-ro defaults,errors=remount-ro,data=writeback,noatime 0 0      1
# /dev/sda5
UUID=9dcc280b-e37b-46f1-9a51-20075fb9a66e none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0

#/dev/sdb1
/dev/sdb1                                /mnt/WDCaviar     ext3    auto 1 1

```

I then do a :
```
sudo mount -a   
[mntent]: line 6 in /etc/fstab is bad

```

dmesg | tail shows:
```
[17179790.516000] EXT3-fs: Unrecognized mount option "fmask=0111" or missing value
[17180263.964000] kjournald starting.  Commit interval 5 seconds
[17180263.976000] EXT3 FS on sdb1, internal journal
[17180263.976000] EXT3-fs: mounted filesystem with ordered data mode.

```

Any help would be greatly appreciated.  Thank you.

---

### Post by mangoti on 2007-01-30
Maybe you should not repeat "defaults,errors=remount-ro" in the mount options for sda1. Also try adding rw as option for sdb1. Dont know about the fmask stuff.

---

