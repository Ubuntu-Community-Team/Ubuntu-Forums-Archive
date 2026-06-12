---
title: "HD's will not automount on bootup"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by garyed on 2007-08-20
I'm trying to mount my windows drives at bootup. I can manually mount them after I boot up with no problem using the command:
  sudo mount  /dev/hda1  /media/c_windows  & " d_windows" for the other one.
On my other Edgy computer I have virtually the same fstab & I don't have to manually mount my drives after boot up. Any ideas what I'm missing?
Here's my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb2
UUID=34c795ec-cde2-4670-b879-de9b03b4bd08 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=14535c50-0a3b-4dd4-8e62-d1cfec8278f7 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1    /media/c_drive vfat auto  iocharset=utf8,unmask=000  0    0
/dev/hdb1    /media/d_drive vfat auto  iocharset=utf8,unmask=000  0    0

---

### Post by Aishiko on 2007-08-20
someone else had a similar problem and was told that writing a shell script would be what is needed, just search the forum and uit should be an easy find it was only int he last 2 days

---

