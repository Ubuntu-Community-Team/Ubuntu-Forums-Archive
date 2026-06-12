---
title: "African Gremlins ?"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by nnjond on 2007-03-05
i have a duel boot. My data is on an aux disc, ((hdb5), which i can acces in Windows), but the permisions tabs on these directories are all greyed out so i can't write to them and i am informed;

"You are not the owner, so you can't change these permisions"

How can i change these permisions ?


nnjond@nnjond-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda5 / ext3 defaults,errors=remount-ro 0 1
/dev/hda6 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto
/dev/hdb5 /media/hdb5 vfat rw,defaults,user,gid=1000,umask=0222 0 0 0
nnjond@nnjond-desktop:~$ mount
/dev/hda5 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-28-386/volatile type tmpfs (rw)
/dev/hdb5 on /media/hdb5 type vfat (rw,noexec,nosuid,nodev,gid=1000,umask=0222)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda1 on /media/usbdisk type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8)
nnjond@nnjond-desktop:~$

---

### Post by renzokuken on 2007-03-05
should it not be 

[color=red]sudo[/color] mount

???? could be wrong though

---

### Post by johnl on 2007-03-05
You can change permissions with the "chgrp" (change group) "chown" (change owner) and "chmod" (change permissions? :P) commands.  

To make your user the owner of a file or directory, 

```

$ sudo chown myusername thefile

```

If you want to apply this recursively to all files in a directory:

```

$sudo chown -R myusername thedirectory

```

Once you're the owner of the file, you can modify the permissions through the graphical interface (which is probably easier) or through the "chmod" command.  Type "man chmod" for more information.

Hope this helps,

John

---

