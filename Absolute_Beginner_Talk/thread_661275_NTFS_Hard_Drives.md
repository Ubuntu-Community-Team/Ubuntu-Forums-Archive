---
title: "NTFS Hard Drives?"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by davemo on 2008-01-07
I seem to not be able to gain any of the permissions to my hard drive. I am using Ubuntu 6.06 LTS. I don't have permisions to anything but my home folder. Please help me. A friend of my suggested  that I have Linux installed on an NFTS formatted hard drive. Is this why?

---

### Post by snickers295 on 2008-01-07
type this in the terminal:```
mount
``` post the output here.

---

### Post by davemo on 2008-01-07
```
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-29-386/volatile type tmpfs (rw)
/dev/hdc on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=dave)
```

---

### Post by snickers295 on 2008-01-07
what are you trying to get access to?
linux is made so you cna't just go and messing with anything but your home directory, and niether can program  its a security thing.

---

### Post by davemo on 2008-01-07
well, I'm trying to install Pidgin. And it says something when I try to get my WiFi about not having the rights to access my broadcom WLAN adapter.

---

### Post by davemo on 2008-01-07
Is there a way I can change the ownership of my drive from root to my username?

---

### Post by taurus on 2008-01-07
If you need to modify something outside your $HOME, use sudo (or gksudo) instead.  Don't just change the ownership or permissions just because it's easier for you.  Applying blinding could cause some serious problems for your machine.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by snickers295 on 2008-01-07
ya hes right, its also a security  hazard too.

---

