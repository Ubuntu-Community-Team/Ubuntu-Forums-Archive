---
title: "dualboot double check..."
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by staticvoid on 2008-02-17
btw, i'm posting this in Absolute Beginners talk because i am *clueless* on how to dualboot and even if this will work:

i wanna dual boot archlinux and ubuntu. here's what i got:

**fdisk -l**
```
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c73ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2227    17888346   83  Linux
/dev/sda2            4679        4864     1494045    5  Extended
/dev/sda3            2228        4678    19687657+  83  Linux
/dev/sda5            4679        4864     1494013+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

and the last bit in my grubby grub grub....

**menu.lst**
```
......### END DEBIAN AUTOMAGIC KERNELS LIST

title        ArchLinux
root        (hd0,1)
chainloader +1

```

look good to you guys? i'll be using the same swap partition for both, and i when i install archlinux, i won't install grub. pretty much i'll install the whole thing with cfdisk to /dev/sda2... no swap.. no /home or /boot partitions...

will i suceed?? dun dun dun!

:)

sv

EDIT: woops! where will i be installing arch to..? sda3 instead? so make that (hd0, 2) in the grub? i see sda2 is extended... hmm... looked ok when i did it with gparted livecd  : /

---

### Post by ace007 on 2008-02-17
This is the example from /boot/grub/menu.lst

```
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

```
So maybe you dont need the chainloader line?  And you need a kernel line?

---

### Post by staticvoid on 2008-02-17
ok, i just read someones post that said chainloader +1 was cool....  : /  :) 

so then, according to fdisk -l i would put this

title		 ArchLinux
root		(hd0,2)
kernel	      /vmlinuz root=/dev/hda3 ro

correct?

and then install Arch on sda3?

wait a minute... whats the dif between hda and sda??

:) thanx for the quick responces, hope i can install tonight :)

sv

---

### Post by ace007 on 2008-02-17
sda and hda are different devices.  I think hda is your master hard drive?  sda is the first USB device....that doesn't sound right.  
check out the following for "How to fstab" there is little blurb about the naming of devices I think.

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

PS - if you're asking me if your setup is right, I would not be the right person to be asking!

---

### Post by staticvoid on 2008-02-17
> PS - if you're asking me if your setup is right, I would not be the right person to be asking!

thanks for the link though :D

sv

reading up on it...

---

### Post by staticvoid on 2008-02-17
bump. so hows this:

**fdisk -l**
> 
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c73ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2227    17888346   83  Linux
/dev/sda2            4679        4864     1494045    5  Extended
/dev/sda3            2228        4678    19687657+  83  Linux
/dev/sda5            4679        4864     1494013+  82  Linux swap / Solaris

Partition table entries are not in disk order

**menu.lst**
> title		ArchLinux
root		(hd0,1)
chainloader +1

title		ArchLinux (2nd try)
root		(hd0,2)
chainloader +1

title		ArchLinux (3rd try)
root		(hd0,2)
kernel		/vmlinuz root=/dev/hda3 ro

won't hurt to try 'em all i figure  :)... just gotta make sure i install on the right partition...  :)


sv

---

### Post by gn2 on 2008-02-17
You're going to have a lot of fun with Arch.....:-k

---

### Post by dstew on 2008-02-17
> kernel /vmlinuz root=/dev/hda3 roI think the correct root here should be /dev/sda3

---

### Post by staticvoid on 2008-02-18
> You're going to have a lot of fun with Arch.....

i know it :).  I can't wait to understand linux. they have GREAT wiki... way simpler... and i've heard, way faster too... i'm dualbooing windows > ubuntu > arch... slowly getting there... ;)

> I think the correct root here should be /dev/sda3

aha! thanx for the suggestion, i'll add another entry to try!  :)

sv

---

