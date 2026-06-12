---
title: "wipe out harddrive"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by nashphyl on 2007-12-30
Hi im trying to completely wipe out my harddrive and delete the partitions that are on it. I want a completely fresh install of ubuntu (no dual boot). How can i do this? And after the harddrive is wiped clean,  can i just install ubuntu from the live CD i downloaded from ubuntu.com? Thanks!

---

### Post by nick_h on 2007-12-30
Yes, just do a new install.  It will give you an option to wipe the hard drive.

---

### Post by nashphyl on 2007-12-30
Hmm are you sure? I installed ubuntu with the live cd with the intention of allocating all of my harddrive to Ubuntu (120 gigs) but when i installed it only allowed me the option of working within one of the existing partitions (40 gigs), so i am running ubuntu within a 40 gig partition on a 120 gig harddrive. I want to dedicate all 120 gigs to ubuntu. Do you still think running the ubuntu cd again will allow me to do this?

---

### Post by shuttleworthwannabe on 2007-12-30
Why don't you download a [GParted Live CD]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828") and boot off it, delete the partitions and create a 2 new partitions 1. Linux root (Ext3) 2. swap (n or 2n RAM).

Then use the Ubuntu Live CD and install on the ext3 and use the swap ( you may choose to format it again.

Good luck,
S

---

### Post by nick_h on 2007-12-30
> I want to dedicate all 120 gigs to ubuntu. Do you still think running the ubuntu cd again will allow me to do this?
Yes - you can delete partitions.

Here is a useful link - [http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)

Having said that, I have always partitioned my drive first.  The above post suggesting the GParted Live CD is a good one.

---

