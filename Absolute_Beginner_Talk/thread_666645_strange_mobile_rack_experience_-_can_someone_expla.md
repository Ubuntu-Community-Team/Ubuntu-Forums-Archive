---
title: "strange mobile rack experience - can someone explain for me?"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by paker on 2008-01-13
2 IDE hard drives in 2 mobile rack trays. Mobile rack has IDE connection. Only one is used at a time. One (7.04 installed) worked okay but the other wouldn't work no matter what.  Always Grub error 17. (don't know what it means) Posted here but no reply. Finally found the sweet spot: make it the only primary IDE. 

Can someone explain?

---

### Post by SOULRiDER on 2008-01-13
From [http://www.gentoo.org/doc/en/grub-error-guide.xml](http://www.gentoo.org/doc/en/grub-error-guide.xml)
> This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.

Its possible that if a drive was removed or added or nay conenctions change, the number of the partitions change so youre trying to boot from a wrong partition.

---

### Post by paker on 2008-01-13
Thanks for the reply. It explains why one drive didn't work after I moved it to a mobile rack. Two things that I don't understand:
1) I fresh installed ubuntu after moving it to a mobile rack. Still wouldn't work. This is Western Digital 200 GB.
2) But the other hard drive was taken out from another computer, put in a mobile rack on my machine. It worked right away. This is Maxtor 100 GB, older hard drive.

---

