---
title: "Partition won't mount to desktop"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by yochaigal on 2007-02-17
Hello everyone.
New to ubuntu.  I recently re-installed it to fix some video issues (messed up my xorg.conf) and now, one of my partitions won't appear as a drive on the Places menu or the Desktop!  It works fine besides, i've tried mounting/unmounting, moving the mount point, etc but can't get it to appear as anything but a folder at /home/yochai/media (that's the current mount point).
On the previous install, it allowed me to see the drive on the desktop. I've tried reformatting. I've checked gconf-editor, and it shows a check next to "show volumes on desktop."  my external hard drive mounts just fine.... I just don't know how they differ.   
Is there some other way of adding this partition to the list of volumes?  

thanks!

---

### Post by phidia on 2007-02-18
What does your /etc/fstab list for drives. Post your fstab here.
Another couple of things to try is too look at the output of dmesg to see how that partition is being called out and if you created the mount point "/home/yochai/media" you may want to delete it and see if it automounts when you logout and back in again.

---

### Post by tiptip on 2007-02-18
In console write :
```
gconf-editor
```
and then apps->nautilus->desktop

Make sure you have 'V' on volumes_visible

---

### Post by yochaigal on 2007-02-18
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc               proc         defaults                    0  0
# /dev/hda3
UUID=11645c70-2ea9-4025-a915-505b051bd295  /                   ext3         defaults,errors=remount-ro  0  1
# /dev/hda2
UUID=cc883f7f-330c-44d9-afb6-a623fc33e7ce  none                swap         sw                          0  0
/dev/hdb                                   /media/cdrom0       udf,iso9660  user,noauto                 0  0
/dev/                                      /media/floppy0      auto         rw,user,noauto              0  0
/dev/hda1                                  /home/yochai/media  ext3         errors=remount-ro,user      1  2

/dev/hda2                                  /media/hda2         swap         defaults                    0  0
/dev/hda3                                  /media/hda3         ext3         defaults                    0  0
/dev/sda1                                  /media/sda1         vfat         defaults                    0  0

---

### Post by yochaigal on 2007-02-18
i also seem to be unable to change the ownership of /dev/sda1... 
i've tried : sudo chown username:group /dev/sda1
and other combinations... it stays root.

---

### Post by yochaigal on 2007-02-20
an update, for any web crawlers out there.
i deleted the entry for hda1 out of fstab.  then, i mounted the drive to /media/hda1
then i rebooted. viola. it works.

as for the chown thing, i needed to specify not just the /dev/sda1 but also the mount point. from root.

thanks!

---

