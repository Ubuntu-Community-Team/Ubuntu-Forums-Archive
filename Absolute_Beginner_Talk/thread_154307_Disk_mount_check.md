---
title: "Disk mount check"
date: 2006-04-02
forum: Absolute Beginner Talk
---

### Post by cliff0108 on 2006-04-02
Hi 
I have Ubuntu installed on my system - as well as 3 internal HDs (ntfs) and a USB hd  (which I just re-formatted to Fat32 (to use as an intermediary)
All seems working well - but I wonder if someone knowledgeable can have a look at the terminal display after the command 'mount'.
I am a little concerned about the " **(rw,errors=remount-ro)**" entry.
I'll also paste in my fstab file.
I only had to edit it to mount the two ntfs drives.
Thanks

cliff@ubuntu:~$ mount
/dev/hdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-10-386/volatile type tmpfs (rw,mode=0755)
/dev/hda1 on /media/oldc type ntfs (rw,nls=utf8,umask=0222)
/dev/hde1 on /media/photodrive1 type ntfs (rw,nls=utf8,umask=0222)
/dev/hdg1 on /media/photodrive2 type ntfs (rw,nls=utf8,umask=0222)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda5 on /media/COPY OF C type vfat (rw,nosuid,nodev,quiet,shortname=winnt,uid=1000,gid=1000,umask=077,iocharset=utf8)
cliff@ubuntu:~$


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto 0       0
/dev/hda1       /media/oldc     ntfs    nls=utf8,umask=0222 0   0
/dev/hde1       /media/photodrive1 ntfs  nls=utf8,umask=0222 0   0
/dev/hdg1       /media/photodrive2 ntfs  nls=utf8,umask=0222 0   0

---

### Post by nanotube on 2006-04-03
hey
do not be concerned about that
what "(rw,errors=remount-ro)" means is that it should try to mount as read/write (rw), but if it encounters any errors, it should try to remount it as read only (ro).
that's perfectly fine and sensible, don't worry about it. :)

---

