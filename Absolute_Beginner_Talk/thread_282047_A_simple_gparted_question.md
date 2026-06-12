---
title: "A simple gparted question"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by crimesaucer on 2006-10-22
I have 4 partitions. 3 are primary. 1 is an extended swap of 1GB. 

The 1st is my ntfs /media/hda1 Windows Xp, the 2nd is the ext3  /media/hda2 ubuntu/xubuntu 6.06 which I'm having problems logging into, and the 3rd is an ext3 / xubuntu 6.10 which I want to keep.

Can I erase the ext3 /media/hda2 partition and add the 13.04GB to my 9.32GB ext3 / partition that I want to keep?

I am new to ubuntu/xubuntu and g parted, so I want to ask before I try something risky.

Thanks,
-c.

---

### Post by dmizer on 2006-10-22
yes you can do this.  i've actually even done the same thing with ntfs partitions using knoppix.

remember, both partitions you will be modifying will need to be unmounted, so doing this from inside xubuntu will not be possible.

also, after you are done, your partition layout will be different, so you will have to edit grub.

finally (but most importantly), you are doing dangerous things to your hard drive, and if this is your first time playing with your partition table, expect to potentially loose everything.  ie: backups will be necessary for you to keep your sanity.

edit: you also might want to consider setting up a test platform ... so you can play with the software and figure out how to make it work.  and perhaps even more ... learn what not to do.

---

### Post by crimesaucer on 2006-10-22
How would I "not" be in xubuntu 6.10 and do this?

Would I have to use an install disk or a live disk to adjust the current partitions and how would I do that exactly? Or is there a different way.

Thanks,
-c.

---

### Post by bulldog on 2006-10-22
The live disk will do nicely.

---

### Post by crimesaucer on 2006-10-22
can I use a breezy 5.10 live disk?

---

### Post by CatKiller on 2006-10-22
> **crimesaucer said:**
> can I use a breezy 5.10 live disk?

You should be able to, although I'd recommend the [GParted live cd]("http://gparted.sourceforge.net/livecd.php"), since that will have the latest version of GParted that might do some things that the GParted on the 5.10 cd can't. Like move an ext3 partition.

---

### Post by crimesaucer on 2006-10-22
damn. I read this a bit too late. It's do over time.

---

