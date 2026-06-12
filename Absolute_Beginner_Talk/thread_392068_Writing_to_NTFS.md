---
title: "Writing to NTFS"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by DdlyArcher on 2007-03-24
I'm having a problem writing to a NTFS partition.  I heard that Ubuntu can't write to NTFS by default so I installed the package "nfts-3g" in Synaptic.  But that did not fix the problem it still says that it is a read only disk.

---

### Post by lamalex on 2007-03-24
you will need to remount that partition with support for writing.

edit fstab to something like this
```

dev/hda3 /media/windows ntfs-3g defaults,locale=en_US.utf8 0 0
```
thats not what yours will be necessarily, but similar. if you post your fstab```
cat /etc/fstab
``` someone can probably give you exact syntax

---

### Post by DdlyArcher on 2007-03-24
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=0bae5c3b-4fa0-4098-95e2-3ffcdff69b87 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda2
UUID=D4D83EF9D83EDA06 /media/Windows  C       Drive           ntfs    defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hda1
UUID=7EFA-09BD  /media/WindowsRecovery vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=bc90462a-8b2a-44e9-ae34-b5a7fce9c56a none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

```

My drive I want to be able to write is not there it is "sda3", it is on a external harddrive.

---

### Post by Michaelt74 on 2007-03-24
It's a bit tricky, but this guide should help:

[http://opensourceroolz.wordpress.com/2007/02/26/writing-to-windows-ntfs/](http://opensourceroolz.wordpress.com/2007/02/26/writing-to-windows-ntfs/)

---

### Post by ComplexNumber on 2007-03-24
> **DdlyArcher said:**
> I'm having a problem writing to a NTFS partition.  I heard that Ubuntu can't write to NTFS by default so I installed the package "nfts-3g" in Synaptic.  But that did not fix the problem it still says that it is a read only disk.
i wouid suggest that you try[ this]("http://flomertens.free.fr/ntfs-config/"). it worked for me without me even having to touch the fstab file. make sure all dependencies are satisfied though.

---

### Post by x1a4 on 2007-03-24
It's also a good idea to install FUSE in addition to ntfs-3g.

---

### Post by DdlyArcher on 2007-03-24
Michaelt74 guide worked thanks.

What does Fuse do? I can't find anything that  explains it well.

---

### Post by x1a4 on 2007-03-25
> **DdlyArcher said:**
> 
What does Fuse do? I can't find anything that  explains it well.

[http://fuse.sourceforge.net/](http://fuse.sourceforge.net/)

---

