---
title: "Unmounting Iphone?"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by ~~Tito~~ on 2007-10-20
I want it off ubuntu, so I can start a new in virtual box. When ever It connects it recognizes it as a camera and when I click cancel it stops charging? How can I make it start all over again? When I first connected it while on VB it connected for like 5 sec and then stopped. What can I do?

---

### Post by ~~Tito~~ on 2007-10-20
This is what I have mounted.
```
tito@TITOS-LAPTOP:~$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
**procbususb on /proc/bus/usb type usbfs (rw) - I am wondering if its this but I have an external mouse and keyboard so this might be that**
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
**usbfs on /proc/bus/usb type usbfs (rw,noexec,nosuid,nodev,devgid=vboxusers:x:1001:tito,devmode=664)- this is so the proxy error will stop.**
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

```

---

### Post by ~~Tito~~ on 2007-10-20
I need to know because I am leaving in a few. . .

---

### Post by llamakc on 2007-10-20
If it automounts, is it mounting to /media?

cd /media

See what's in there and unmount it.

sudo umount /media/WHATEVER

---

### Post by ~~Tito~~ on 2007-10-20
Nope. Nothing. Well, I was looking in the usb thing and was wondering why it wouldn't connect anymore and when I highlighted it said, unsupported. . . . *SIGHS* I will have to wait untill my dad brings his computer. . .

---

