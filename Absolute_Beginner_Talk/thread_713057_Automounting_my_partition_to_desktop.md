---
title: "Automounting my partition to desktop?"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by uhappo on 2008-03-02
Here is my fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=fc52d7c5-ad70-487d-9f38-c8465a2dbeb9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=311b1410-ac1c-4c89-a1c5-6750d6478350 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

Here are my partitions

[img]http://stashbox.org/87319/Desktop.png[/img]

I want my  14,46gb partition to automount on desktop

Desktop address is /home/urkki/Desktop

How to do that?

---

### Post by scragar on 2008-03-02
```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/hda3
UUID=fc52d7c5-ad70-487d-9f38-c8465a2dbeb9 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5
UUID=311b1410-ac1c-4c89-a1c5-6750d6478350 none swap sw 0 0

# add this line
/dev/hda2 /home/USERNAME/Desktop auto rw,auto,exec 0 0

/dev/hdc /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec 0 0
```
then remount the drive:
```
umount /dev/hda2
mount /dev/hda2
```

---

### Post by uhappo on 2008-03-02
Aargh, I need to clarify myself a bit more...

I don't need the content of the disk to be displayed on the desktop, just the disk-icon...

Just like when you mount the disk it gives you the disc-icon on the desktop...

---

### Post by scragar on 2008-03-02
if you just set the file to mount somewhere in /media it will apear on the desktop:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/hda3
UUID=fc52d7c5-ad70-487d-9f38-c8465a2dbeb9 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5
UUID=311b1410-ac1c-4c89-a1c5-6750d6478350 none swap sw 0 0

# change to this, replace disk with whatever you want it called.
/dev/hda2 /media/disk auto rw,auto,exec 0 0

/dev/hdc /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec 0 0
```
again, unmount then remount the drive(You may need to create the folder for it's contents if it doesn't already exist).

---

### Post by uhappo on 2008-03-02
Wuhuu! Thanks alot! It's working now, I created the folder in nautilus, and rebooted and voilla.

---

### Post by jan quark on 2008-03-02
you can check what is what is displayed on the desktop by doing:

```
gksudo gconf-editor
```

navigating to apps > nautilus > desktop
and checkong what you need

---

