---
title: "Dual Boot hard drive space"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by qozmiq on 2007-09-18
I successfully installed Ubuntu and XP, and during the hard drives space allocation/partitioning, I gave far too much space to the Ubuntu partition.  What would be the best way to resize, with Ubuntu, or XP?  Ubuntu sees the windows partition, XP does not see the Ubuntu partition.  I am assuming this would be best done in Ubuntu, but not sure what software would be responsible for this.  I gave Ubuntu 60 gigs, and want to bring that down to about 20.  Has been a stellar OS, if only Adobe would port Photoshop to it...I would dump XP all together!

Any assistance anyone can provide would be extremely beneficial!

Qozmiq:confused:

---

### Post by justleen on 2007-09-18
Xp can't handle the EXT3 filesystem, thats why you dont see the drives in XP 
(if you want to see the disks, install the ext3 driver for windows)

To resize the partition, your best of to use Gparted. This is included on the live cd (AFAIK, if not, ,just sudo apt-get install gparted while booted from the live cd)

PS: Photoshop runs under wine!

---

### Post by qozmiq on 2007-09-18
Thank you so much for your help...one more question...how well does Photoshop work under wine?  I use it roughly 8 hours a day, it is vital to my business...

Qozmiq

---

### Post by justleen on 2007-09-18
have a look at winehq.org.. though i must add that the later the version the trickier to get it to works ;)

---

