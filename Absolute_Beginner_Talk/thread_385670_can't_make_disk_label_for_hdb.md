---
title: "can't make disk label for hdb"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by angelsneverdie on 2007-03-16
Hello hello.  It's your friendly resident noob here.  So I've got a second internal HD installed (it's 250gig, should that matter).  Problem is, when i look at it in gparted it says that it is unallocated.  when i try to set a disklabel i get this output in the terminal:

Unable to open /dev/hdb - unrecognised disk label.
Unable to open /dev/hdb - unrecognised disk label.
Input/output error during read on /dev/hdb
Input/output error during write on /dev/hdb
Unable to open /dev/hdb - unrecognised disk label.


i'm running edgy and the drive is a standard IDE drive.  anything i can do to get this drive working or is it busted beyond belief?

i'll emphasize here that I really have no idea what i'm doing when it comes to linux, so be gentle with me, i'm still learning.

thanks in advance!

-mitchell

---

### Post by yabbadabbadont on 2007-03-16
I think you can only label a **partition**, not the whole disk.  /dev/hdb refers to the entire disk.  /dev/hdb1 refers to the first partition of that disk (if any).  If there aren't any partitions, create one, then try labelling that.

---

