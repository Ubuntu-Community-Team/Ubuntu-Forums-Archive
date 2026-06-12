---
title: "Adding XP to create dual boot - ease my mind?"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by adamr on 2008-03-05
I'm going to help a friend with their machine tonight, which currently is Ubuntu only. They have a very custom piece of software which will only run on windows, and as such need an XP partition back and a dual boot system. I've done quite a bit of reading and I'm pretty sure I know what I need to do, but I'd just like to check it over with you good folk to make sure I'm a) doing it in the right order, and b) not missing anything obvious.

[LIST=1]
[*]Boot from LiveCD, use gparted to resize current linux partition and create a new one for XP from the free space left
[*]Boot from XP CD, install to new partition
[*]Re-write GRUB - I'm thinking of using the subergrubdisk
[/LIST] 

As far as I can see, that'll do it. Am I right? I'm assuming gparted is a pretty mature partition manager so there's no likely loss of data from the linux partition in resizing it (smaller)?

Thanks in advance.

---

### Post by overdrank on 2008-03-05
> **adamr said:**
> I'm going to help a friend with their machine tonight, which currently is Ubuntu only. They have a very custom piece of software which will only run on windows, and as such need an XP partition back and a dual boot system. I've done quite a bit of reading and I'm pretty sure I know what I need to do, but I'd just like to check it over with you good folk to make sure I'm a) doing it in the right order, and b) not missing anything obvious.

[LIST=1]
[*]Boot from LiveCD, use gparted to resize current linux partition and create a new one for XP from the free space left
[*]Boot from XP CD, install to new partition
[*]Re-write GRUB - I'm thinking of using the subergrubdisk
[/LIST] 

As far as I can see, that'll do it. Am I right? I'm assuming gparted is a pretty mature partition manager so there's no likely loss of data from the linux partition in resizing it (smaller)?

Thanks in advance.

HI and always back up your data, and have you given thought to a virtual machine to run windows for that software?

---

### Post by adamr on 2008-03-05
I had thought about it, but was wondering what the hardware interfaces and support is like, and I don't really know the best one to use.

The software is for an embroidery machine, which can be connected to the PC.

Any suggestions as to which virtual machine software is best, and the likelihood of full interface/hardware support?

---

### Post by Mauler5858 on 2008-03-05
Sounds about right.  And yea make sure you back up.

---

### Post by stalkingwolf on 2008-03-05
You May run into an issue with xp.  As I recall windows always wants to be first.  But I think even 
that is fixable.

---

### Post by Mauler5858 on 2008-03-05
If its an issue you can set grub up similar to this: (correct me if im wrong)

title Windows XP
rootnoverify (hd0,0)
makeactive
map (hd0,1)(hd0,0)
map (hd0,0)(hd1,0)
chainloader +1

---

