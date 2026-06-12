---
title: "boot to ubuntu partition on ext. fw drive"
date: 2011-02-24
forum: Apple Hardware Users
---

### Post by edgeit on 2011-02-24
I installed ubuntu 10.10 onto an external fw800 drive partitioned through the ubuntu installer to ext4. i set up the 4gb swap space, and set the mount point to /

how do i get the macbook pro to boot to this install? 

selecting OPTION does not pull up the ubuntu partition.

---

### Post by thundaboom on 2011-02-24
Boot on to your Mac O s x partition.

After that go on System preferences > startup disk > then choose your external partition from there.

---

### Post by edgeit on 2011-02-24
If the partition isnt coming up as a possible boot device what does that mean? The install was done inproperly? Should ext4 partiointed drives be at least visible by the mac os ? I have to imagine so, though mine is not, start up disk, or just in general.


UPD: in Disk Utility the linux partitions are labeled disk2s & Linux Swap

---

### Post by thundaboom on 2011-02-24
If you have partitioned the ext4 filesystem correctly, it would have showed up in the bootable disks menu.

This may have to do with the way it is recognizing the external hard drive.

---

### Post by edgeit on 2011-02-24
then i guess its safe to say i DID NOT partition it correctly. hmmm im going to look for a guide

---

### Post by pindar on 2011-02-25
Sorry, but I have never heard that the steps outlined by thundaboom make this possible. As far as I know (and I've experimented quite a bit), it is **much** more complex. You can search this and other forums for "EFI boot," and you'll see there are tutorials, but it's difficult.

---

### Post by edgeit on 2011-02-25
Damn. Thanks for the info. 

The only reason i started this whole project was when a friend of mine that is much less tech savvy then I dual booted his MBP, and I thought doing the same, except with an external partition would be just as simple. I guess I am in for something special.

---

