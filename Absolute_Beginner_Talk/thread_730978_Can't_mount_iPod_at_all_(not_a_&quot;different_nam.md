---
title: "Can't mount iPod at all (not a &quot;different name&quot; problem)"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by komori on 2008-03-21
I'm running Ubuntu Gutsy. Until now, my iPod (a 3G Nano Video) has worked just fine, but today I can't get it to mount at all. Sometimes when I plug it in I get an error saying "/dev/sda1 is already mounted or /media/IPOD is busy", and trying to mount it by hand returns the same. Amarok detects there's an "iPod at /dev/sda1", even though it isn't mounted. And I've been able to mount it once: don't know how, but it just automounted as usual.

There seems to be nothing wrong with the iPod itself: it plays music just fine and the database shows no corruption on first view.

dmesg | tail returns either a block of "Bad block number requested" or
```
[ 3962.956000] device-mapper: table: 254:2: linear: dm-linear: Device lookup failed
[ 3962.956000] device-mapper: ioctl: error adding target to table
```

I just don't understand it.

---

### Post by wolfen69 on 2008-03-21
i had this problem for a little while with my PSP. it would work for a while, then stop. now it is working fine. i gave up trying to figure it out. perhaps someone may be able to shed some light on this.

---

### Post by komori on 2008-03-21
There must be some explanation! On 2.6.20 it works fine after disabling usefree, but 2.6.22 keeps giving me this "bad block" error :confused:

---

