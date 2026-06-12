---
title: "Can't Mount A Drive"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by tlinux on 2007-05-27
I want to mount a cd drive and write to it but I can't figure out how to do it. The Manual page on Mount is as clear as mud to me. Here's what I got when I ran "mount" :

[INDENT][INDENT]tom@HP:~$ mount
/dev/hda8 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw)
tom@HP:~$
[/INDENT][/INDENT]

The contents of /etc/fstab are:

[INDENT][INDENT]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda8
UUID=a1bb4bc1-5f79-47c2-b81a-26f66a3380af /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda9
UUID=cd199098-ba3f-44f5-ae14-6b01261f7f73 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
[/INDENT][/INDENT]

The cd is at /media/cdrom0 but I don't know how to mount it. Help will definitely be appeciated.

Thank you.

---

### Post by taurus on 2007-05-27
If you want to burn something to a CD, use any burning app that is available in Ubuntu.  Even though I run Gnome, I like k3b.

```
sudo aptitude update
sudo aptitude install k3b
```
It should now be in Applicatons -> Video & Sound.

---

### Post by tlinux on 2007-05-27
K3b is installed. I've tried to use it before without success. I tired it just now and it started out with the following messages:

[INDENT][INDENT]Successfully created data project iso

Using Woodin 1.1.2 ....

Starting TAO at 12x speed[/INDENT][/INDENT]

At this point it freezes up. I have to turn off the computer and reboot. Every time I've tried K3b it has frozen up on me. 

Any thoughts as to what is causing this problem?

---

