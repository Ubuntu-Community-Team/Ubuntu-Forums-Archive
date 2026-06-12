---
title: "installing slave drive"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by alvid on 2007-01-05
I am dual booting ubuntu edgy and windows xp. my computer is a pen 3 750 and it is around
6 yrs old. I am running 80 gig now and plan on installing another 80 as a slave to the master.
What will happen when i install the slave drive????  Will it go to the windows xp partition or
the linux partition???.

---

### Post by taurus on 2007-01-05
Well, XP will probably call it D: or whatever the next letter is.  And for Ubuntu, you have to mount it before you can access it...

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Patrick K on 2007-01-05
It depends on the how you format it. If you format it as EXT3 it is a Linux drive. NTFS, it is XP's. Fat32, both can use it. For XP, if you partition the whole drive as Extended, it will take the next available drive letter. If you partition it, or any part of it, as primary, it will take the D drive name, unless you have other primary partitions on the first drive. Then it will take the next available primary drive letter. Confused, yet? 

The best bet is to partition it as extended. That will keep the existing drive letters as they are. Within the extended partition, you can make other partitions. Any that are readable by XP will take the next available drive letter. Any EXT3 partitions will be ignored. Adding a drive can push up you optical drive (CD-ROM, DVD) letters. This can create problems with software that needs to read the optical. I don't use XP, never have, but I understand it is possible to rename the drives. If so, you can assign them any drive letter you want. This would a solve these problems. Hope this answered your question.

---

