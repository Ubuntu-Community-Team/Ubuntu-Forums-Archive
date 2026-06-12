---
title: "Can't Create PArtitions when installing to MacBook Pro"
date: 2016-07-01
forum: Apple Hardware Users
---

### Post by CrusaderAD on 2016-07-01
When attempting an install on a MacBook Pro from a live usb drive, it fails when creating the partitions. I get:

errno=-32

It seems to delete any existing partitions just fine, but won't create them. I've installed Ubuntu on this hard disk using another machine, and it worked fine. It's like the MacBook has some kind of lock on writing partitions to the drive. Any ideas?

---

### Post by howefield on 2016-07-01
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by este.el.paz on 2016-07-10
> **CrusaderAD said:**
> When attempting an install on a MacBook Pro from a live usb drive, it fails when creating the partitions. I get:

errno=-32

It seems to delete any existing partitions just fine, but won't create them. I've installed Ubuntu on this hard disk using another machine, and it worked fine. It's like the MacBook has some kind of lock on writing partitions to the drive. Any ideas?

If you or someone else used Bootcamp to set up other partitions, then, yes, that seems to put a lock on adding partitions.  I found that out the "hard way" the first time I tried to set up a third partition after I had set up two using BC.  Best thing at that point is to clone the existing installs  to ext HD, then erase the whole drive, and then just use DU to create your partitions . . . .

Sound like that's what happened?
e..

---

