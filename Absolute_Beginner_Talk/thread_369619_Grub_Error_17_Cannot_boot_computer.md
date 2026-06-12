---
title: "Grub Error 17/ Cannot boot computer"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by jprb85 on 2007-02-24
I have been having some major problems with my computer and now when it is about to load  Ubuntu, it always says Error 17. I would greatly appreciate any help how how to actually load my computer and not have it say

GRUB loading, please wait ....

Error 17

Thanks

:popcorn:

---

### Post by n8bounds on 2007-02-24
Are you using a SCSI or SATA drive?

GRUB Error 17 indicates that it can see the partition, but it can't recognize the filesystem type. Perhaps your root(x,y) settings are incorrect?

The Gentoo guys are all absolutely crazy, so read up on their forums too, not just here.

I found this:

[http://forums.gentoo.org/viewtopic.php?t=120802](http://forums.gentoo.org/viewtopic.php?t=120802)

It looks full of good hints...

(Here's the grub manual:

[http://www.gnu.org/software/grub/manual/html_node/](http://www.gnu.org/software/grub/manual/html_node/)

)


If you can't figure it out, boot from a live cd, post the output of a 
```

sudo fdisk -l

```

and the contets of your /boot/grub/menu.lst  file on whatever partition your boot or folder lives in right now (you'll have to mount it manually from the Ubuntu Live CD)

..and we'll try to help

---

### Post by jprb85 on 2007-02-24
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       38180   306680818+  83  Linux
/dev/hdc2           38181       38913     5887822+   5  Extended
/dev/hdc5           38181       38913     5887791   82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

### Post by foxmulder881 on 2007-02-24
> **n8bounds said:**
> The Gentoo guys are all absolutely crazy, so read up on their forums too, not just here.

I second that comment. The knowledge of some of the Gentoo blokes is just mind boggling. I'm a regular visitor and contributor to the Gentoo forums. But half of the time I have no idea what the hell they're on about. :(

---

### Post by n8bounds on 2007-02-24
We'll also need your grub menu.lst file from your hard drive (not the one from the live cd make believe file system)

---

