---
title: "How do you unmount/mount an USB memory stick?"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2007-01-27
How do you unmount/mount an USB memory stick?
I normally use diskmounter with the nice GUI so things get mounted automatically, but when I eject it the icon dissappears making it impossible for me to mount it again.
How do I do this in terminal?

---

### Post by tkjacobsen on 2007-01-27
use the mount command

sudo mount /dev/sda1 /media/sda1

Assuming sda1 is your device and the folder /media/sda1 exists (mkdir -p /media/sda1)
You can check the device using "dmesg". It will show you which devices has been connected.

Use "mount" without any options too see which devices is mounted where.

EDIT:  forgot umount

use "sudo umount /dev/sda1" to unmount the device

---

### Post by jingo811 on 2007-01-27
Also I have another problem lately with my memory stick.  It won't backup a folder containing news articles from the Internet could a file name like this be causing the copying problem
http:@@eros.nutek.se:8080@nbg@checklist.form

Or does memory sticks have a certain lifespan that won't let you copy over 1000 times or something like that?

---

### Post by tkjacobsen on 2007-01-27
> **jingo811 said:**
> 
http:@@eros.nutek.se:8080@nbg@checklist.form


This filename will not work on a fat32 partition which is standard on most usb sticks... You can reformat the stick to use an ext2 partition, this will allow strange names...

EDIT: but then it will not work on a standard windoze machine.

---

### Post by jingo811 on 2007-01-27
I ejected the USB stick by clicking eject on disk mounter and tried to do things in terminal
but it didn't seem to respond well.  Looks like I can only re-mount my ejected USB by physically taking it out and putting it back into the port so diskmounter can auto detect by itself.

> mike@sanka:~$ **mount**
/dev/hda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-27-386/volatile type tmpfs (rw)
/dev/hdb3 on /home type ext3 (rw)
/dev/hda1 on /media/hda1 type vfat (rw)
/dev/hda2 on /media/hda2 type vfat (rw)
/dev/hdb1 on /media/hdb1 type vfat (rw,iocharset=utf8,umask=000)
/dev/hdc on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=mike)
/dev/sda1 on /media/usbdisk type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8')
mike@sanka:~$ **sudo mount /dev/sda1 /media/usbdisk**
Password:
mount: mount point /media/usbdisk does not exist
mike@sanka:~$ **sudo mount /dev/sda1 /media/sda1**
mount: mount point /media/sda1 does not exist
mike@sanka:~$ **sudo umount /dev/sda1**
umount: /dev/sda1: not found
mike@sanka:~$ **sudo umount /dev/usbdisk**
umount: /dev/usbdisk: not found
mike@sanka:~$ **sudo mount /dev/sda1 /media/sda1**
mount: mount point /media/sda1 does not exist
mike@sanka:~$ **sudo umount /dev/usbdisk**
umount: /dev/usbdisk: not found
mike@sanka:~$

> 
You can reformat the stick to use an ext2 partition, this will allow strange names...
EDIT: but then it will not work on a standard windoze machine.
Reformat the stick how do I accomplish that exactly?  Is there a trick to reformat it into a dual partition USB memory stick FAT/ext2?

---

### Post by tkjacobsen on 2007-01-27
you can reformat it by typing:

sudo mke2fs /dev/sda1

when the disk is unmounted...


From your output it looks like your disk is mounted...
check if the mountpoint exists.. "ls /media" if not, create it. "sudo mkdir -p /media/usbdisk"
then mount..
"sudo mount /dev/sda1 /media/usbdisk"


EDIT: it is possible to reformat it to have two partitions..

sudo fdisk /dev/sda

---

### Post by jingo811 on 2007-01-27
Ah now I understand how the umount/mount works for the USB stick.  That eject button didn't mean unmount like in terminal, it totally takes away the disk icon from the menu bar.  That's why I can't unmount/mount it afterwards with terminal correctly.

Note to self don't click eject button in the future use terminal to unmount and re-mount instead :KS 
Tnx for the help by the way!

---

