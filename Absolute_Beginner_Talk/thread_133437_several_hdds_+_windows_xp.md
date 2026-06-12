---
title: "several hdds + windows xp"
date: 2006-02-20
forum: Absolute Beginner Talk
---

### Post by gagatz on 2006-02-20
Hello, I've got the following problem:
The computer  has 2 physical drives. The first one has a Windows XP partition (HDC1) and the second one has 3 partitions, a ext3 one where ubuntu is on (HDD1), one virtual fat one (HDD2) and another ext3 (HDD3). Windows can read from and write on hdc1 and hdd2. Linux can read from hdd2 and hdd3, but only write on hdd3. It is possible to use terminal and some sudo commands to write data on hdd2 and to change the rights, such that user can also write on hdd2, but it not possible to use drag and drop on hdd2. I would like to know, how it is possible have a drive, where both windows as well as ubuntu can write on.
Thanks

---

### Post by xmastree on 2006-02-20
Linux ought to be able to write to hdd2, if it's FAT32, post your etc/fstab file and we'll see what's stopping it.

My shared partition, which linux can drag and drop on to, is listed like this:
```
/dev/hdb3	/mnt/shared	vfat	umask=0000	0	0
```
yours will be /dev/hdd2 and whatever mount point you choose.

Linux will also be able to read (but not write) hdc1, my fstab for my ntfs partition looks like:
```
/dev/hda1	/mnt/winxp	ntfs	umask=0222	0	0
```

---

### Post by gagatz on 2006-02-20
Hello, thanks for answering. My fstab is the following>



# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>________________<dump>  <pass>
proc___________ /proc____________proc___  defaults _____________________0____     0
/dev/hdd1______/________________ext3____defaults,errors=remount-ro__0________1
/dev/hdc1______/media/hdc1______ntfs_____defaults___________________0________0
/dev/hdd2______/media/hdd2______vfat_____defaults__________________0________0
/dev/hdd3______/media/hdd3______ext3____defaults___________________0________0
/dev/hdd4_______none____________swap___sw_________________________0_______0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by xmastree on 2006-02-20
[QUOTE=gagatz]
/dev/hdd2       /media/hdd2     vfat    defaults        0       0
[/QUOTE]
That's the line you need to change.

So, from a terminal, type **sudo gedit /etc/fstab**, enter your password and the editor should open up.
Change that line above to this:
```
/dev/hdd2       /media/hdd2     vfat    **umask=0000**        0       0
```
save the file and exit. Then, do
**sudo umount /dev/hdd2** which will unmount it
then do
**sudo mount /dev/hdd2** which will re-mount it according to the fstab, which will have changed since it was originally mounted.

You should be good to go.

---

