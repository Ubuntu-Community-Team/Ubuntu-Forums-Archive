---
title: "second HD gone"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by killaray on 2006-11-27
i restarted my computer and all of a sudden my second drive is gone.... help appreciated plz... it has all my media on it

_this is wut it says in "mount"_
```
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

```

_this is wut it says in fdisk -l_
```
Disk /dev/hda: 60.0 GB, 60040544256 bytes
255 heads, 63 sectors/track, 7299 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6999    56219436   83  Linux
/dev/hda2            7000        7299     2409750    5  Extended
/dev/hda5            7000        7299     2409718+  82  Linux swap / Solaris

```

---

### Post by Peepsalot on 2006-11-27
Well, it doesn't look like it is showing up at all in fdisk.  I would first check if there is a loose connection on the data cable or power cable.  Is it IDE or SATA?  Can you hear the drive spin up or make any noises at all.  Have you changed anything in BIOS?  Was this drive working previously?

---

### Post by killaray on 2006-11-27
nothing was touched or changed all i did was restart the PC... drive is IDE... ill take alook see if anything got loose i doubt though

---

### Post by killaray on 2006-11-27
lol i guesss it mustve gotten loose... i turned of my PC and wiggled the cables a bit and its back up.. thats confusing thought it got disconnected by no movement.. sorry mods u can delete my thread

---

### Post by Peepsalot on 2006-11-28
I hope the problem was a loose cable.  Another possible cause is that your hard drive is on the verge of failing.  I would recommend you back up any important data just in case.

Although, I must say I doubt your drive is failing, since I have had a few hard drives fail, and the symptoms have never been like your situation.  Common symptoms before failure are usually corrupt data, a ticking sound, failure to boot, etc.

---

