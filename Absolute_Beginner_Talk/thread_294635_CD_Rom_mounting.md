---
title: "CD Rom mounting"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by XPuntu on 2006-11-06
I thought I had all my mounting issues settled but I guess not. 

I have a CD RW drive and DVD RW drive. I've set them both up in fstab (I hope properly):

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd	/media/cdrom1	udf,iso9660 user,noauto		0	0

I've been able to access media on both drives even though I don't see them when I type the mount command:

/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-27-686/volatile type tmpfs (rw)
/dev/hda2 on /home type ext3 (rw)
/dev/hdb1 on /media/hdb1 type ntfs (rw,nls=utf8,umask=007,gid=46)


I've just burned a bunch of mp3 files to my CDROM drive using Gnomebaker. when I eject the disk and reload it, CD-RW shows up as a place on Nautilus but when I double click I get "Unable to mount selected volume". If I pop it in the DVD drive it shows up on nautilus (and my desktop) and can be explored without any error message. Put it back in the CD ROM drive and still no love.:-k 

Have a missed something mounting the drives? 

Thanks.

---

### Post by po0f on 2006-11-06
XPuntu,

What happens when you remove "udf" from the fstab entry for your CDRW?

---

### Post by XPuntu on 2006-11-11
No luck. And today the problem has reversed. I've loaded a CDROM in both drives and although nautilus shows both drives, it only lets me "explore" the cd drive. 

1. Is it right to name the drives CDROM0 and CDROM1 in fstab? Somewhere I thought I saw my devices listed as CDROM and CDROM0 but that doesn't make sense.
2. Even when I try to explore the CD in the CD drive it automatically loads sound juicer. Can't I just have a directory of the files instead?

Thanks.

---

