---
title: "itouch"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by stevensonfire on 2008-04-07
my itouch is jailbroken
and when i
ipod-touch-mount
i get

"iPod is not responding to pings at ipod.
Please set the environment variable IGNOREPING if you want to ignore this."


what environment variable?

---

### Post by fluffman86 on 2008-04-07
Last I heard you couldn't mount an ipod touch as a hard drive.  But you can try!  It looks like your problem is with the sytax of your command, and that "touch" is already a linux command that you can't use to name a device.

First find out what your ipod is according to the system.  Unplug the iPod, then:
```
cd /dev
ls
```
do that in a terminal, and find the area that begins with sda.  sda is your main Hard Drive, sdb is probably another hard drive if you have one, etc.  Now plug in the ipod and do that again.  You should have a new sdc showing up (or whatever letter comes next).

now create a place to mount it, and mount your ipod:
```
sudo mkdir /media/ipod
sudo mount -t vfat -o defaults /dev/sdc /media/ipod 
```

I know that works for a Windows formatted 5.5 Gen iPod Video, but like I said, I think Apple changed some stuff with the touches that may prevent you from doing that.

Good Luck!

---

### Post by xelapond on 2008-04-07
> and that "touch" is already a linux command

Mount is also a GNU/Linux command, so you can't have that in there either if fluffman86 is indeed correct.

---

### Post by stevensonfire on 2008-04-08
thanks didnt help 
it'll soon enough be hacked.. hopefully
fuckn hate windows... 
com'on Itouch hackers you can do it!!!

---

