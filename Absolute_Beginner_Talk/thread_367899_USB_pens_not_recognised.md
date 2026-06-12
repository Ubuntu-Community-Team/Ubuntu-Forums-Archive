---
title: "USB pens not recognised"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by tartarian on 2007-02-22
I've noticed in the last couple of days that USB pens don't seem to be recognised when they are plugged in. I can't access any files on them, and when I try to mount them with the 'mount' command, I get an error message.

I tried to mount my Windows partition a couple of days ago aswell, and I had to modify /etc/fstab to do this. Being stupid, I didn't make a back up. Maybe this has done something???

My /etc/fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=8ac011ff-6774-4f7c-9332-088b9c1d2254 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda2
UUID=836e064a-4df6-457a-a855-760d0e64a974 /home           ext3    defaults        0       2
# /dev/hda1
UUID=8AB80039B80025F3 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda4
UUID=9bca10e9-19b9-48e8-9d9c-68b66f890fae none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1   /windows   ntfs   user,fmask=0111,dmask=0000   0   0

```

My CD-ROM doesn't work either :(

Thanks!

---

### Post by tzulberti on 2007-02-22
If you are using Gnome, go to Setting, Preferences, Removable devices. Check if the options to automatically mount the cd and the pen driver are checked.

---

