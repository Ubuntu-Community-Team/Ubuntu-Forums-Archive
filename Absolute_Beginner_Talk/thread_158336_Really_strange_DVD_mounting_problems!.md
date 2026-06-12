---
title: "Really strange DVD mounting problems!"
date: 2006-04-11
forum: Absolute Beginner Talk
---

### Post by Books on 2006-04-11
[SIZE="2"]Ok, I've got a mess of weirdness here. I think it has to do with a mounting problem, and it might have started after updating some system files but I'm not sure.

I first noticed a problem when nothing showed up in the KDE Open Dialog under "Storage Media" except for "Floppy Drive". (Before it also showed my drive partitions and DVD drive.) I tried to make a copy of a data DVD and that's when I knew I had a problem -- it wouldn't copy the files without stalling or copying incredibly slow. And K3b and Konqueror refuse to copy the files, which are showing up in the Konqueror dialog when I stick in the DVD. But here's the thing -- my FAT hard drive partitions aren't showing up either (in KDE's "Storage Media"), so I think it's an issue with mounting rather than a DVD-specific problem.

Here are some symptoms:

* My FAT partitions are still accessable under /media/(partition name), but don't show under KDE's "Storage Media". And the DVD doesn't show under /media/cdrom0/ -- nothing is there.

* I tried to use K3b to make a copy of a data DVD and it couldn't find the drive.

* I stick in the DVD and Konqueror pops up "media:/hdc" window and the files show. When I try to copy them to the hard drive it goes very slow, then stalls.

* I tried Nautilus, and it says "Audio CD" in the side directory but when I click on it it says: "cdda:///dev/hdc" is not a valid location"

* The /dev/ directory doesn't show any of the drives like hdc or my FAT partitions, only an "fd" that I assume is the floppy, which Linux boots on.

* I stick in the DVD and Konqueror pops up "media:/hdc" window and the files show. When I try to copy them to the hard drive it goes very slow, then stalls.

* I used "kdesu mount /media/cdrom0/" to try to mount the DVD drive manually, and while I files show us on "media:/hdc" still nothing shows up under /media/cdrom0/ in Konqueror. 

* I tried to eject the DVD and it said "Eject /dev/hdc failed!"

* The files ARE there on the DVD that I'm trying to copy... It isn't a case of a defective DVD. The files show up when I stick it in, I just can't copy them without it stalling out.

* When I turn off the computer and the words go by, I've caught a glimpse of "can't unmount" or something like that, but then it turns off too fast to read it.

Here is my /etc/fstab[/SIZE]
```
[SIZE="2"]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
/dev/hda5       /media/g_part  vfat    iocharset=utf8,umask=000   0       0
/dev/hda6       /media/d_part  vfat    iocharset=utf8,umask=000   0       0
/dev/hdb5       /media/f_part  vfat    iocharset=utf8,umask=000   0       0[/SIZE]
```

[SIZE="2"]Does anyone have any ideas? I've been updating my system, and I'm wondering if it started after a system update.

**Thank you** for helping with such a tricky problem!!! ](*,)

Books[/SIZE]

---

### Post by quincyjones on 2006-07-03
maybe check out: 
[http://www.ubuntuforums.org/showthread.php?t=183682](http://www.ubuntuforums.org/showthread.php?t=183682)

---

