---
title: "Need help reformating/partitioning"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by richiewrt on 2006-11-22
Well, I think I really screwed up. I was trying to delete my windows partition and go completly with linux, but now i cant boot either, so my question is how do I from the ubuntu live disk go in and format my hard drive and then just install 1 partiton for ubuntu?

---

### Post by taurus on 2006-11-22
You can use gparted from the LiveCD and erase/delete all the partitions.  Then, tell the installer to use the whole disk...

---

### Post by az on 2006-11-22
> **richiewrt said:**
> Well, I think I really screwed up. I was trying to delete my windows partition and go completly with linux, but now i cant boot either, so my question is how do I from the ubuntu live disk go in and format my hard drive and then just install 1 partiton for ubuntu?

what did you do exactly?  If you renamed or moved some partitions, grub may no longer be able to find it's other half.

Grub gets loaded into memory as the boot loader because its' first half is on the very beginning of the disk.  That piece tells the computer where to find the rest of it to properly go on with loading the OS of your choice.

If you did something that changed what your BIOS things was partition number two into partition number one, well, Grub is still looking for partition two.

You need to boot the live cd and edit your grub parameters and reinstall grub - there is a wiki page describing how to do that.

As well, you will need to edit you /etc/fstab to reflect those changes as well.

Is this the problem?

---

### Post by richiewrt on 2006-11-22
Well, the problem started off at I couldnt mount the windows partition, when i tried to do that the comp couldnt even find the fstab file and since i'm pretty much just using this computer as a print server and extra storage I decided just to redo the install and completly delete the windows partition completly to simplify things. Hopefully I can get it working after i get done installing ubuntu.

---

