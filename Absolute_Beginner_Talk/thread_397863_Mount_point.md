---
title: "Mount point"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by RizingDamp on 2007-03-31
Hey,

Im still trying to get an icon on my desktop to show my FAT32 partion.  This is my etc/fstab file...

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       /home           ext3    defaults        0       2
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda6	/media/osshare vfat iocharset+utf8,umask=000	0	0


The last line is what I have just added having gathered info from this forum.  It has created an icon in my Places>Compter Folder but I would like to be able to change the name of it form Volume7.0GB to that of OSshare if I can.


Any help wud be appreciated.


Thanks,

Andy.

---

### Post by pollywog on 2007-03-31
Hey, I used the guide at:

[https://help.ubuntu.com/community/AutomaticallyMountPartitions?highlight=%28automatically%29%7C%28mount%29](https://help.ubuntu.com/community/AutomaticallyMountPartitions?highlight=%28automatically%29%7C%28mount%29)

to automatically mount my fat32 partition, and it puts an icon on your desktop. I cannot seem to rename the icon however- I'm stuck with hdb3. -P.W.

---

### Post by SentientFluid on 2007-03-31
> **RizingDamp said:**
> Hey,

Im still trying to get an icon on my desktop to show my FAT32 partion.  This is my etc/fstab file...


/dev/hda6	/media/osshare vfat iocharset+utf8,umask=000	0	0


Try changing it to something like this:

```

/dev/hda6       /media/osshare       vfat    defaults,utf8,umask=007,gid=46 0       1
```

That's what I'm using and it automounts with read/write access and shows on the desktop.

---

### Post by Skrynesaver on 2007-03-31
You will need to install mtools then use mlabel to change the disc's label to OSShare

---

