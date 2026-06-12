---
title: "Installation stops at 94 percent?"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by nvurusic on 2007-01-05
Yesterday I downloaded Ubuntu 6.10 from the net, successfully booted from the liveCD and I decided to install it. The installation went well til exactly 94% followed by the message that said there were fatal errors installing grub...

Google says that a few other users experienced the same problem, bot I didn't find any answer (yet). 

Detail of my hard disks: seagate SATA 120GB (the only HD), connects to the SATA port, and the partitions are made as follows:
1. partition (primary) - 45 GB, ntfs  (in kparted sda1)
2. partition (extended): (sda2)
          - 40 gb - ntfs (sda5)
          - 20 gb - fat32 (sda6)
          - 14,5 gb - ext3 (sda7) - this is where I want to install ubuntu
          - 0,5 gb - linux swap (sda8)

The installation goes smooth until 94%. Any help is apreciated...
Forgot to mention, when the installer asks me where should grub be installed to, the I use the default location (hd0). And one more question, "hd0" is default typed in brackets (); is this OK??

Nenad

---

### Post by Jimmy_r on 2007-01-05
I had the same problem a while ago.
I solved it by using [Disc wizard starter edition]("http://www.seagate.com/www/en-us/support/downloads/discwizard") to zero-fill(quick option) my mbr.

Doing that, howewer, would wipe your partition table and make your data unaccessible...
So only do it if you plan to format the entire HD afterwards.

---

### Post by nvurusic on 2007-01-05
Could it be that this is the only sollution, i hope not...

Is hb0 the right place to install grub, or should I install it to sda or somewhere else? What for are the brackets in (hd0)?

---

