---
title: "disk numbering -terminal"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by Benontheroad2006 on 2007-04-04
Hello, I am trying to navigate to my USB stick via the terminal so I can find out what disk number it has been allocated - I need this number for a another program.

I have got so far as 'cd /dev' then 'ls -a' but I cannot work out which listing is my usb key and the disk number associated with it.

Can anyone help?

Many thanks

---

### Post by mikeyphi on 2007-04-04
Have a look under SYSTEM - ADMINISTRATION - DEVICE MANAGER
Assuming your USB stick is attached it should be listed - along with everything else!
Hope this is what you need....

---

### Post by taurus on 2007-04-04
It's probably /dev/sda1 but the first question is whether it is mounted?

```
df -h
sudo fdisk -l
```

---

### Post by techstop on 2007-04-04
The easiest thing to do would be to run the command "mount" in a terminal and have a look at the output. Mine looks like this;

> barney@edgy:~$ mount
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
/dev/sda1 on /media/winxp type ntfs (rw,nls=utf8,umask=0222)
//Clarkconnect/shared on /media/clark type smbfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
**/dev/sdf1 on /media/usbdisk type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8)**


The bolded part is my usb flash disk, so my device is /dev/sdf1. HTH...

---

