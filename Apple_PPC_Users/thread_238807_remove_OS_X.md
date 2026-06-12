---
title: "remove OS X"
date: 2006-08-18
forum: Apple PPC Users
---

### Post by N8K99 on 2006-08-18
I would like to remove my OS X partition in order to gain an additional 20 Gig of space on my hard drive. I never boot into it anymore not even with Mac on Linux. So, how do I go about removing this partition without losing the data in my home directory?

---

### Post by stmiller on 2006-08-18
You would have to boot up a live cd like this one:

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Which lets you non-destructively resize linux filesystems.

Have to use a live cd, b/c you cannot be booted inside the hard drive you want to change.

I'm not sure if this gparted live cd boots on a mac, but you'd have to use something like this, or hook your computer hard drive up to another computer, and do the formatting from there.

---

### Post by N8K99 on 2006-08-18
the gparted website states that it works on i86 machines, which my powerbook is not. 

Is it possible to use the partition tool on the ubuntu install cd? or am i going to lose my data using that method?

---

### Post by bluenova on 2006-08-18
Yes you can use the Ubuntu live CD as it contains Gparted, just make sure the disk you want to change is un-mounted. As to whether it still works on a mac I do not know.

---

### Post by ubuntubrian on 2006-08-18
I have used iPartition to create the Linux partition in the first place so I would imagine that it would work fine in resizing a Linux partition. It created and sized my partitions inthe first place and no OS X data was lost. It is not free however but is worth the $25.

---

### Post by N8K99 on 2006-08-18
i am not sure that $25 to use something once is really a great value - i mean if i really have to, i will just backup all my data and wipe the whole HD to reinstall. that is my normal method of making any changes to the OS, however this time i was looking to be a little more crafty.

---

