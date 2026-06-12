---
title: "removing Ubuntu Partition"
date: 2008-11-27
forum: Apple Hardware Users
---

### Post by jonawald on 2008-11-27
Hi, I installed Ubuntu on my new Unibody MacBook, but noticed too late that I had selected the wrong partition. Now I have Ubuntu on a partition with a bit of space of either side. 

I would like to take Ubunto entirely off the hardrive so that I can redo my partitions. 

I have tried numerous methods. I cannot get the Ubuntu CD to boot Live despite setting that disk to boot in boot manager in OSX. I have also tried holding "C". 

I have downloaded a Paragon CD that is supposed to be bootable nothing seems to boot on this thing. HELP.

Jonathan

---

### Post by user12021 on 2008-11-27
try holding option at startup, and insert the cd then.

also, if you can't boot from a cd, you probably have the firmware password set.
go into the terminal (in OSX) and type "sudo nvram security-mode=none"

gparted is what you should be using for your partitioning.
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by jonawald on 2008-11-28
I discovered the "option" button. But the information on G-parted should be helpful. I will try it out ASAP.

Jonathan

---

### Post by cyberdork33 on 2008-11-30
> **jonawald said:**
> I cannot get the Ubuntu CD to boot Live despite setting that disk to boot in boot manager in OSX. 
You should not do this.

---

### Post by jonawald on 2008-11-30
> **cyberdork33 said:**
> You should not do this.

Wow great you are a lot of help.:)

---

### Post by cyberdork33 on 2008-11-30
> **jonawald said:**
> Wow great you are a lot of help.:)
for future reference. that tool is dangerous, I don't know why apple has it. The other poster has already told you how to proper boot from the CD. (Option key).

---

