---
title: "read-only file system - so i'm unable to alter sysfiles"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by kreislauf on 2007-03-14
hi, 
well, big shot. i'm traveling and so far i left my usb drives at home. using a ibm x30 with no cd drive, so no live cd at all.

what i did is: 

i changed my /boot/grub/menu.lst
```
# defoptions=quiet **splash rootflags=data=writeback**
# altoptions=(recovery mode) **single rootflags=data=writeback**

```

and updated
```
update-grub

```

step 2 was changing /etc/fstab my rootsystem hda2 to 
```
defaults,errors=remount-ro,**data=writeback,noatime** 0

```



well, my system is not going to boot anymore. i will get to busybox, every time i'm trying.
recoverymode lets me feel quite comfortable, but i am not allowed to change my files, i altered (and backuped.save)

```
mount -o remount,rw /dev/hda2
```
brings 
```
mount: / not mounted already, or bad options
```

all executed as sudo...

how can i regain control of my wracked read-only filesystem?

---

### Post by gus sett on 2007-03-14
rather than ask questions/interview, I'll make a statement and if you can
follow it, you probably know enough to proceed and gather more relevant
options.  
All files and directories have read and write permissions that can be viewed
using the -l flag, and which can be set using the root account--*man*
is/was invaluable.


> **kreislauf said:**
> hi, 
well, big shot. i'm traveling and so far i left my usb drives at home. using a ibm x30 with no cd drive, so no live cd at all.

what i did is: 

i changed my /boot/grub/menu.lst
```
# defoptions=quiet **splash rootflags=data=writeback**
# altoptions=(recovery mode) **single rootflags=data=writeback**

```

and updated
```
update-grub

```

step 2 was changing /etc/fstab my rootsystem hda2 to 
```
defaults,errors=remount-ro,**data=writeback,noatime** 0

```



well, my system is not going to boot anymore. i will get to busybox, every time i'm trying.
recoverymode lets me feel quite comfortable, but i am not allowed to change my files, i altered (and backuped.save)

```
mount -o remount,rw /dev/hda2
```
brings 
```
mount: / not mounted already, or bad options
```

all executed as sudo...

how can i regain control of my wracked read-only filesystem?

---

### Post by kreislauf on 2007-04-09
well, solved. i simply booted with a DSL cd and restored the broken files...
rather simple...

---

