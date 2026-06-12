---
title: "Unable to update - corrupted package?"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by Pascalinux on 2007-01-06
Hello! I installed Ubuntu 6.10 as a weekend project, it's going remarkably fine: I solved a video driver card issue (was working with the booth CD, but not once installed), installed packages.

But now I'm trying to update from version Version 2.6.17-10.33 to Version 2.6.17.1-10.34 with the updater, and I get weird error messages.

```
E: /var/cache/apt/archives/linux-image-2.6.17-10-generic_2.6.17.1-10.34_i386.deb: archive du système de fichiers corrompue - archive du paquet corrompue
```

... Archive of the package are corrupted. I got a similar result when trying with command line (sudo apt-get upgrade), even after sudo dselect update, and even after rebooting and starting up with command line.

Here is the mount info:

```
pascalinux@pascalinux-desktop:~$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-10-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
pascalinux@pascalinux-desktop:~$ 
```

Here is the fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=5f60cc90-98c8-4daa-a9ab-05af4aa8aa5d /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=69fca3ca-3227-4d52-8726-8eb124fee3bf none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

```

Is it normal that I don't see a boot drive???

Any help would be greatly appreciated. And I promise to get better with time!

Thanks

---

### Post by teaker1s on 2007-01-06
have a look at this thread
[http://ubuntuforums.org/showthread.php?t=186672]("http://ubuntuforums.org/showthread.php?t=186672")

---

### Post by Pascalinux on 2007-01-06
Thanks for the info. I'll try everything, even staying calm and focused during the numerous steps... Any way to pinpoint more precisely the issue?

---

