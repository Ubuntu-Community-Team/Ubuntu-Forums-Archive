---
title: "Mounted devices names"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by SirGrant on 2007-04-23
Hi I would like to rename my USB devices after they are mounted but I don't know how to do that.  For example my ipod when plugged in automatically gets mounted as SIRGRANT's (my username) and my thumbdrive mounts as drive.  I have attached a picture.  I would like to remain it to something like iPod and Thumbdrive.  Anyone know how I can go about doing this.  Thanks. 

[IMG]http://img222.imageshack.us/img222/4172/screenshotuj1.png[/IMG]

---

### Post by spin2cool on 2007-04-23
This should help:
[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

---

### Post by SirGrant on 2007-04-23
Thanks, that worked for renaming my thumbdrive but my ipod wouldn't rename it still says

> Can't open /dev/sda2: No such file or directory
Cannot initialize '::'
mlabel: Cannot initialize drive


---

### Post by SirGrant on 2007-04-23
bump anyone know how to rename my ipod?

---

### Post by Cypher on 2007-04-23
When everything is mounted, type
```

mount

```
and show us the results..

Regards

---

### Post by mmikelst on 2007-04-23
I'm trying to do the same thing, but I keep getting 

init :: non DOS media
Cannot initialize '::'
mlabel: Cannot initialize drive

as my error....Any ideas?? I just reformatted it as Fat32.

---

### Post by SirGrant on 2007-04-23
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

---

### Post by SirGrant on 2007-04-24
bump could still use some help.

---

### Post by Cypher on 2007-04-24
Sorry for not getting back sooner..

It's strange, I would expected to see your Ipod and other things listed there. Are you sure you have connected all peripherals before you typed the "mount" command??

Regards

---

### Post by SirGrant on 2007-04-24
Ahh I fixed it I was typing sudo mlabel -i /dev/sda2 ::iPod 

when the device wasn't sda2 it was sdb2.  Small typo error after correcting it worked out.  Thanks for the help.

---

