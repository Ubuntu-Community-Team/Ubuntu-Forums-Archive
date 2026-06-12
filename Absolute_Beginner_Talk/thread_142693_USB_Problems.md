---
title: "USB Problems"
date: 2006-03-11
forum: Absolute Beginner Talk
---

### Post by heyjoe on 2006-03-11
Hi there. I was wanting some instruction on how to mount a 128mb usb flash drive. Breezy Badger doesn't seem to be reocgnizing it.

Secondly, Breezy is recognizing my mp3 player, but i get an error message whenever i unmount it. any help would be much appreciated.

---

### Post by AtinLango on 2006-03-11
What exactly happens when you try to mount the usb drive. Does it return error message or nothing? What do you get if  you type:

```
mount
```

---

### Post by heyjoe on 2006-03-11
Hi, thanks for responding. This is what i get

frank@ubuntu:~$ mount
/dev/hda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-10-386/volatile type tmpfs (rw,mode=0755)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
frank@ubuntu:~$

---

