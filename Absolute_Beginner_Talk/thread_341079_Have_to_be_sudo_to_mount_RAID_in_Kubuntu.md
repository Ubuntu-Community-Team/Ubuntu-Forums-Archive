---
title: "Have to be sudo to mount RAID in Kubuntu"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by DOD1951 on 2007-01-18
This is contents of my fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /mnt/windows         ntfs   nls=utf8,umask=0222 0 0
[COLOR="Blue"]/dev/mapper/pdc_bfagacaai /mnt/raid vfat iocharset=utf8,umask=000 0 0[/COLOR]
/dev/sda2 /mnt/ipod vfat user,noauto,umask=000 0 0

I cannot get /dev/mapper/pdc_bfagacaai to load in Kubuntu, it says:

dennis@dhcppc1:~$ sudo mount /dev/mapper/pdc_bfagacaai
mount: /dev/mapper/pdc_bfagacaai already mounted or /mnt/raid busy
 but when i try to umount it say its not mounted:
dennis@dhcppc1:~$ sudo umount /dev/mapper/pdc_bfagacaai
umount: /dev/mapper/pdc_bfagacaai: not mounted

Confused? I certainly am :(

Anyone know where I am going wrong?

---

