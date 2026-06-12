---
title: "Can't write to MyBook and memory stick"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by zumbi77 on 2007-04-20
I can read the information, but when I try to write I get permission denied. The file system on MyBook is fat32, on the memory stick it's fat16.

---

### Post by Nik_Doof on 2007-04-20
run at the command line:

mount
cat /etc/fstab

and put the output of the two commands on here :)

---

### Post by zumbi77 on 2007-04-20
Mount:

/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-11-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda1 on /media/My Book type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8)
/dev/sdb1 on /home/zumbi77/mybook type vfat (rw)
/dev/sdc1 on /home/zumbi77/usbdisk type vfat (rw)

cat /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=848aea87-52cf-4d1c-b893-ac7dc0b657e5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=6851e2b1-0355-4f00-bd33-f9e1b70b5fb1 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda2   /mnt/ipod   vfat   defaults,user,noauto,sync,umask=000

---

### Post by Nik_Doof on 2007-04-20
umm, what permissions and user/group are your two mount points?

/home/zumbi77/mybook 
/home/zumbi77/usbdisk 

Its possible the user/group for these are root, and/or you dont have write access due to permissions

---

### Post by mediax on 2007-04-20
FWIW, I've had similar problems.

I understand that because FAT16 and FAT32 don't recognise changes to file permissions, you need to unmount the relevant device and remount it with write permissions.

Unfortunately, I've not managed to crack the correct syntax of the mount command (yet!). :confused:

---

### Post by zumbi77 on 2007-04-20
Nik_doof: I don't know if they are root, don't really understand why they would be. If so, what can I do to change it?

mediax: let me know when you figure it out?

---

