---
title: "Copy Ubuntu Partition?"
date: 2007-01-12
forum: Apple PPC Users
---

### Post by gamgee911 on 2007-01-12
I dual boot Mac OS X 10.4 and Ubuntu 6.10.  I wish to copy just my Ubuntu partition to an external drive, is there a way to do this from either my Mac or my Ubuntu partition so that i can boot from my external hard drive?  I doubt it, but is it just as simple as dragging all the files from my Ubuntu partition to my harddrive? :-?

---

### Post by rccharles on 2007-02-09
> **gamgee911 said:**
> I dual boot Mac OS X 10.4 and Ubuntu 6.10.  I wish to copy just my Ubuntu partition to an external drive, is there a way to do this from either my Mac or my Ubuntu partition so that i can boot from my external hard drive?  I doubt it, but is it just as simple as dragging all the files from my Ubuntu partition to my harddrive? :-?

You may want to ask this in one of the regular Ubuntu forums like Absolute Beginner.  

You could use the unix dd command.  The partition on the external drive would have to be the same size or larger.  You would waste space in a larger partition.

In the macos terminal:

sudo bash
fdisk -l
  to see a list of partitions

umount /dev/...

dd if=/dev/... of=/dev/...  bs=1024b

the of is the output  partition.  You may have to umount it.  

 man dd for more info.

.......

Here is one tutorial on cloning.  Seems complicated.

[http://freshmeat.net/articles/view/1375/](http://freshmeat.net/articles/view/1375/)

Here is another one:

[http://inferno.slug.org/cgi-bin/wiki?Drive_Backup_And_Cloning](http://inferno.slug.org/cgi-bin/wiki?Drive_Backup_And_Cloning)

Robert

---

### Post by grazie on 2007-02-10
dd is a great tool for cloning, but has one major drawback. If you clone a 2G partition to 4G paprtition, the 4G partition will been seen as a 2G partition by the system. Hence you waste 2G! I think it's often better to use cp -a or tar myself.

---

