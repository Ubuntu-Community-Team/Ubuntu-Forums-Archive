---
title: "Editing my already made partitions"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by Mjo890 on 2007-05-12
Im trying to fix my partitions right now, im running Ubuntu; and not XP.  Can I fix my partitions INSIDE Ubuntu without having to reinstall?

That was my main question, but now ill go alittle more in depth;
I want Dual booting in the near future, I want it set up like so:

Partition 1 - 8GB - Ubuntu
Partition 2 - 8GB - Windows XP
Partition 3 - 90GB - All of the programs and games and multimedia things I download and whatnot.


Whats the best way to set up the partitions? I mean like, SWAP NTFS FAT32, etc; it all dosent make sense to me.

Thanks in advance!

---

### Post by FuturePast on 2007-05-12
You can resize filesystems and partitions but only if they are not being used.
The best way to do this is to use a live cd.

---

### Post by Mjo890 on 2007-05-12
Partition 1 - 8GB - Ubuntu
Partition 2 - 8GB - Windows XP
Partition 3 - 90GB - All of the programs and games and multimedia things I download and whatnot.


How should I set up these paritions? What kind of partition type??? mad confused

---

### Post by FuturePast on 2007-05-12
> **Mjo890 said:**
> Partition 1 - 8GB - Ubuntu [COLOR="Red"]Reiserfs or ext3[/COLOR]
Partition 2 - 8GB - Windows XP [COLOR="Red"]NTFS[/COLOR]
Partition 3 - 90GB - All of the programs and games and multimedia things I download and whatnot. [COLOR="Red"]NTFS
Partition 4 - Swap (roughly) RAM x2  [/COLOR]


How should I set up these paritions? What kind of partition type??? mad confused

Something like this?

---

