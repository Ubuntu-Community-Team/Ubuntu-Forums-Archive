---
title: "HD in file browser"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by krisfrajer on 2007-05-13
Hi 
I cant see one of my HD in my file browser, ubuntu graphical version. I know I have it though since I can access it from the win terminal:

cd /export/home

How can I get this drive to show up in my graphical version of ubuntu. Do i have to mount it? Just in case you wonder about my fdisk and fstab outputs... they are like this

__________________________



oot@NARUTO:/# fdisk -l

Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 1 8052 64677658+ 83 Linux
/dev/hda2 8053 24321 130680742+ 5 Extended
/dev/hda5 23971 24321 2819376 82 Linux swap / Solaris
/dev/hda6 8053 23970 127861272 83 Linux

Partition table entries are not in disk order

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hdb1 * 1 9728 78140128+ 7 HPFS/NTFS
root@NARUTO:/#
____________________________
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/hda1
UUID=601d89de-166e-485f-bd7f-9464a7586628 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda6
UUID=15d9b8bd-c34f-477a-87b8-a54400855074 /export/home ext3 defaults 0 2
# /dev/hdb1
UUID=C800E53F00E534DA /media/hdb1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hda5
UUID=43628781-6785-4072-8766-2ec290bbd01a none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
root@NARUTO:/etc#
_______________________

Notice that dev/hd6 is mounted as /export/home. I did this during ubuntu installation.
I can get access to my windows through the file browser (Yes write/reading privileges thxs to ubuntu feisty). I just I can see that extra HD space about 140 GB. However I notice that in my root directory I can see that folder. Is that folder the missing hard drive?

---

### Post by annda on 2007-05-13
your fstab looks fine and seems to be consistent with the fdisk output - so hda6 should be mounted on boot.

what do you mean you can't see it in GUI? if you open nautilus, go to file system>export, there is no home directory? or is it empty?

---

### Post by krisfrajer on 2007-05-13
yeah it is not empty... I have home and inside I have lost+found

so then finally i get to understand... I access that logical partition as a folder in my root file?

---

### Post by annda on 2007-05-13
actually you can mount anything anywhere in your filesystem - partitions, directories and even single files that will be treated as filesystems. they all look like folders, which means you can browse them and use them as disks/folders.

you have an empty ext3 partition there. now you can do anything you want with it.

---

### Post by krisfrajer on 2007-05-13
great thxs for the reply. i will get some reading in the mount command but everything seems clear. At least I know that drive/space is still there willing to be used...

---

