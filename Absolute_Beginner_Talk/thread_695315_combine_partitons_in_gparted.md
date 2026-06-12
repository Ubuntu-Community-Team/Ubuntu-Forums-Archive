---
title: "combine partitons in gparted"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by AlexLinuxUser101 on 2008-02-12
Is it possible to combine three partitions which I have just deleted the contents of in gparted?

---

### Post by overdrank on 2008-02-12
> **AlexLinuxUser101 said:**
> Is it possible to combine three partitions which I have just deleted the contents of in gparted?

HI and if you have deleted the partition then they should have been combined to free space. Could you post a screen shot?

---

### Post by oedha on 2008-02-12
merge ?
of course you can.....but if you delete them one by one....it will be merge automatically as free space

---

### Post by louieb on 2008-02-12
Maybe.
If they are next to each other on the disk
and they are all primary partitions or all logical partitions.

If two of them are empty
Then you could delete the two empty  partitions and grow the last partition into the now unallocated space.

or if all three are empty  delete all three - then create a new partition in the now unallocated space.

[GParted Documentation - general]("http://gparted.sourceforge.net/larry/generalities/gparted.htm")

---

### Post by AlexLinuxUser101 on 2008-02-12
Ah, the two deleted partitions wouldn't combine because one had a weird "extended" thing associated with it.  Anyways, I deleted that and it combined.  How do I get two of the empty spaces to combine on either side of my main ubuntu partition (or is it unnecessary to combine them because it's free space anyways?)?

Thanks for the help by the way.

---

