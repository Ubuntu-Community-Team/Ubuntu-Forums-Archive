---
title: "device mapping problem when update kernel"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by pnix on 2007-09-27
hi all, let me explain my situation.
I have two disks ide and sata. I stalled ubuntu in sata, installed grub in sata MBR, in bios  boot sequence setting is cdrom>ide>sata so
ubuntu known ide as (hd0) and sata as (hd1).
here is my device.map
(hd0)    /dev/hda
(hd1)    /dev/sda
 and in /boot/grub/menu.lst has this line.
root    (hd1,0)

few months ago for some reason.
I change boot sequence in bios like this cdrom>sata>ide
then when ubuntu boot, grub can't find root partition because it look in (hd1,0)[now it's ide]. To make it boot again I change my menu.lst to
root    (hd0,0)
and my device.map
(hd0)    /dev/sda
(hd1)    /dev/hda

but the problem is everytime that has kernel update my menu.lst will be changed back to original state e.g.
root    (hd1,0)
but device.map doesn't change.

I don't know where ubuntu remember my device map
How to make ubuntu doesn't change my menu.lst back[to root(hd1,0)] when kernel update.

thanks

---

### Post by overdrank on 2007-09-27
Hi I really don't know much if anything  about the grub but I did remember seeing something that your talking about. You may find your answer here
[http://users.bigpond.net.au/hermanzone/p15.htm#DEBIAN_AUTOMAGIC_KERNELS_LIST](http://users.bigpond.net.au/hermanzone/p15.htm#DEBIAN_AUTOMAGIC_KERNELS_LIST)
Good luck and hope this helps! :popcorn:

---

### Post by pnix on 2007-09-27
sorry, I found the solution just change this line in menu.lst.
```
# groot=(hd0,2)
```

---

### Post by logos34 on 2007-09-27
> **pnix said:**
> the problem is everytime that has kernel update my menu.lst will be changed back to original state e.g.
root    (hd1,0)
but device.map doesn't change.

I don't know where ubuntu remember my device map
How to make ubuntu doesn't change my menu.lst back[to root(hd1,0)] when kernel update.

You need to change the 'groot' line

---

