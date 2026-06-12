---
title: "Problem with System-&gt;Administration-&gt;Disks"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by jprb85 on 2007-02-21
I posted a question recently about my external hard drive not letting me save anything. Then someone told me it is probably the permissions on it and told me to go to System->Administration->Disks and work it from there. My problem is that the menu does not show up and does not exist. I would greatly appreciate if you could tell me how I can get that menu or suggest an alternate method to allow Ubuntu to save files onto my external hard drive. Thank you.

---

### Post by skyhopper88 on 2007-02-21
Is your drive NTFS? Linux can't write to that natively, you'll need ntfs-3g
[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

### Post by tonyr1988 on 2007-02-21
System -> Administration -> Disks was removed from Edgy. Please open a Terminal (Applications -> Accessories -> Terminal) and type:

> mount

Please copy / paste the results here.

---

### Post by jprb85 on 2007-02-21
jprblinux@jprblinux-desktop:~$ mount
/dev/hdc1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-11-generic/volatile type tmpfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sde1 on /media/usbdisk type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8)
/dev/hda on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=jprblinux)
jprblinux@jprblinux-desktop:~$ mount
/dev/hdc1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-11-generic/volatile type tmpfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/hda on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=jprblinux)
/dev/sde1 on /media/usbdisk type ntfs (rw,nosuid,nodev,uid=1000,gid=1000,umask=077,iocharset=utf8)
jprblinux@jprblinux-desktop:~$ 
jprblinux@jprblinux-desktop:~$ 
jprblinux@jprblinux-desktop:~$

---

