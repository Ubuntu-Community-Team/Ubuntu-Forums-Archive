---
title: "Need a little help with accessing a drive, besides windows. (Solved)"
date: 2005-11-13
forum: Absolute Beginner Talk
---

### Post by Aryxa on 2005-11-13
Hi guys,

I have managed to get into windows from Ubuntu.

If I do a Sudo fdisk this comes up:


```
Disk /dev/hda: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3070    24659743+   c  W95 FAT32 (LBA)
/dev/hda2            3071        3549     3847567+   f  W95 Ext'd (LBA)
/dev/hda3            3550        4982    11510572+  83  Linux
/dev/hda5            3071        3483     3317391    b  W95 FAT32
/dev/hda6            3484        3549      530113+  82  Linux swap / Solaris


```



/dev/hda1 being Windows.

I added the code to give me permissions to access Windows in fstab.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /media/windows  vfat    iocharset=utf8,umask=000   0       0

```


This shows my :F drive from the current fsdisk above.
```
/dev/hda2            3071        3549     3847567+   f  W95 Ext'd (LBA)
```



How do I make my :F drive accessible from Ubuntu :oops: 

What would I do? and what would I type into the fstab(/etc) -gedit window to make :F drive available to me?

Thanks in advance :)

---

### Post by aysiu on 2005-11-13
Same as /dev/hda1 except that you would create a directory with a different name (```
sudo mkdir /windows/files
```, for example).

---

### Post by Aryxa on 2005-11-13
I am sorry but that makes no sense to me :(

---

### Post by aysiu on 2005-11-14
Actually, now that I'm looking at your partition table again, it looks as if F: might be /dev/hda5, not /dev/hda2.

This is what you do. Open up a terminal and type this command in ```
sudo mkdir /media/f_drive
``` This makes a directory called /media/f_drive. Then, ```
sudo gedit /etc/fstab
``` Change your fstab to look like this:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /media/windows  vfat    iocharset=utf8,umask=000   0       0
/dev/hda5       /media/f_drive  vfat    iocharset=utf8,umask=000   0       0

``` Then save the fstab and close it. Type ```
sudo mount -a
``` and then your F: drive should be mounted at /media/f_drive. If not, try rebooting your computer.

---

### Post by Aryxa on 2005-11-14
aysiu,
I really appreciate the help you have given me. The drive has appeared and I am all set.

Once again, Thank you =D>

---

