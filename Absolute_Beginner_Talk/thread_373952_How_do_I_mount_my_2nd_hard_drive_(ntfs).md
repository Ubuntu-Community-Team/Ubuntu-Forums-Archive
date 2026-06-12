---
title: "How do I mount my 2nd hard drive? (ntfs)"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by BurgesS on 2007-03-01
I have read through several posts and tried several times but have had no luck.  Here is what I get after "sudo fdisk -l":

Disk /dev/hda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7476    60050938+   7  HPFS/NTFS
/dev/hda2            7477       14639    57536797+  83  Linux
/dev/hda3           14640       14946     2465977+   5  Extended
/dev/hda5           14640       14946     2465946   82  Linux swap / Solaris

Disk /dev/hdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9964    80035798+   7  HPFS/NTFS

Here is my /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=fcf4517d-d3b5-4b75-ab1e-2b35d1e8691b /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=112a676d-4af2-458b-971c-0227409c7bc5 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

Any help with what I need to edit into this file with some explanation of what the edited text is doing would be great.  I am trying to learn.

Thanks in advance.

---

### Post by taurus on 2007-03-01
Edit /etc/fstab

```
sudo cp /etc/fstab /etc/fstab.bak
gksudo gedit /etc/fstab
```
and add these two lines to the end of it.

```

/dev/hda1   /media/hda1   ntfs   nls=utf8,umask=0222   0   0
/dev/hdb1   /media/hdb1   ntfs   nls=utf8,umask=0222   0   0

```
Save it.  Then, create two new mount points and mount them.

```
sudo mkdir /media/hda1 /media/hdb1
sudo mount -a
df -h
```

---

