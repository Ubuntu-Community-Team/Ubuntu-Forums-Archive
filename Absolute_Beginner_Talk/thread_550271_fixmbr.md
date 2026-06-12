---
title: "?fixmbr?"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by klemperal on 2007-09-13
I'm currently running a dual boot of XP and Ubuntu 6.10 on my desktop.  I have decided I want to remove Ubuntu from my desktop entirely so it's XP only.  The guide I ran across for removing Ubuntu from XP mentions using the command FIXMBR from the boot disk--but its not that simple of course.  It asks me which drive I want to fix, and from there I get nervous because I'm not sure what to put or how to find out.  By the way, I'm not abandoning this great distro, I plan on making it the only OS on my laptop where it would be more useful to me.

---

### Post by oilchangeguy on 2007-09-13
see this:
[http://technet2.microsoft.com/windowsserver/en/library/769b5d71-686c-47bd-81c8-a4bdf7a8bcdd1033.mspx?mfr=true](http://technet2.microsoft.com/windowsserver/en/library/769b5d71-686c-47bd-81c8-a4bdf7a8bcdd1033.mspx?mfr=true)

scroll down until you find fixmbr.
also it's probably time for a fresh windows install. backup your data. and do a fresh install. you'll be suprised at the difference it makes.

---

### Post by klemperal on 2007-09-13
so after fixmbr, then type 0.  And if that is not the right one type map and it will show me?

Also, is there a way for me to partition the rest of the space back to NTFS through windows one the above is done?

---

### Post by benerivo on 2007-09-13
> **klemperal said:**
> Also, is there a way for me to partition the rest of the space back to NTFS through windows one the above is done?

Yes. Off the top of my head, it is Start>All Programs>Accessories>System Tools>Computer Management>Disk Management. Here you will have a graphical display of your drives, from which you can select partitions to add / delete / format.

---

