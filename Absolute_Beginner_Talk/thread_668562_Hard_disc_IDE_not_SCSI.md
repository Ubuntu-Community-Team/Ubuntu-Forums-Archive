---
title: "Hard disc IDE not SCSI"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by dougmoffatt on 2008-01-15
Hi
I'm trying to load Ubuntu 7.10 from the live CD and after examining my system the hard discs are reported as sda and sdb which means they have been identified as either SCSI or SATA discs, whereas I believe them to be IDE which should be hda and hdb.  They are 80 GB IDE Maxtor 6Y080L0 controlled by IDE ATA/ATAPI controllers.  I'm loath to go ahead at this stage for fear of wrongly partitioning my C drive which contains Windows XP and various programs.  All data is on the D drive so is safe, but it would take a long time to restore XP and progs to C.  Any advice?

---

### Post by Whiffle on 2008-01-15
Its due to a change in the kernel, hd* designations are being phased out, and everything is being called sd*

---

### Post by philinux on 2008-01-15
This is normal Gutsy calls them sdx. It's just nomencalture.

I think it means **S**torage **D**evice

---

