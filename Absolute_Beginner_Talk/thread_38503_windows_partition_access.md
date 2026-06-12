---
title: "windows partition access"
date: 2005-05-31
forum: Absolute Beginner Talk
---

### Post by TheAxeMaster on 2005-05-31
I have set my windows partitions (one primary and one extended) to mout on boot so I can access them, but I can't access them both.  I used exactly the same commands for both (like the guide says) and it lets me access the C: drive, but not the D: drive.  I can access it through a root terminal, but I'd like to have the graphical file manager be able to access it.  How can I do this short of making myself a member of root?

my fstab is this:
```
proc            /proc           proc    defaults        0       0
/dev/sda8       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda6       /boot           ext3    defaults        0       2
/dev/sda7       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdb        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1	/media/winc	ntfs	umask=0222	0	0
/dev/sda5	/media/wind	ntfs	umask=0222	0	0

``` 

I tried changing the options to ro,user,umask=0222, then I tried defaults, and nothing changes it, I still can't browse to it.  Any ideas?  Does it have anything to do with the D: drive being an extended partition?  I checked the permissions with a right click-properties, and it says the owner is root.  I have tried a few of the chown commands found in my searches here, and it didn't make any difference.

EDIT:  nevermind, apparently, a reboot helped, and its all good now.  I love this OS!

---

### Post by Mez on 2005-05-31
```
/dev/hda1       /media/windows-c        ntfs    umask=0222      0       0
/dev/hda6       /media/windows-h        ntfs    umask=0222      0       0
/dev/hda5       /media/windows-f        ntfs    umask=0222      0       0
/dev/hda8       /media/windows-i        ntfs    umask=0222      0       0
/dev/hda7       /media/windows-l        ntfs    umask=0222      0       0
```

Those are my settings for my ntfs disks in my fstab, and I seem to ba able to access my drives perfectly well

edit: ah I just saw your edit :D

---

