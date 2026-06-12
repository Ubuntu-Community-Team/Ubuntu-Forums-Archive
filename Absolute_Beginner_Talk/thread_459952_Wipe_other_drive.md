---
title: "Wipe other drive"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by Drakkor on 2007-05-31
Yeah, I want to free up my other drive completely, I have tried GParted, and deleted all the partitions,but I still have 2 ualocated partitions, and I can't seem to expand it all to just 1 big partition !  Any help ? Thanks :p

---

### Post by plcdfa on 2007-05-31
What are you trying to do exactly? One large partition on the whole drive? And what is the problem? If you could provide a screenshot perhaps it would be easier to help. :)

---

### Post by LaRoza on 2007-05-31
I have noticed the same thing with GParted, it will delete swap, but won't expand other partitions to fill the area.

I am assuming the unallocated space used to be swap partitions.

---

### Post by plcdfa on 2007-05-31
Well that sux. In cases like this I just open the partition table in a hex editor a zero out everything, that alway fixes the problem. (Only if I want to clear the whole drive anyway, of course. I don't recommend this to anyone not completely familiar with the part table and hex editing tough.)

---

### Post by Nessa on 2007-09-24
What's the fastest way to wipe out all data in a hard drive?

---

### Post by Nessa on 2007-09-24
Any ideas?

---

### Post by vanadium on 2007-09-24
Just load gparted and delete all partitions? fdisk should also work for that matter.

---

### Post by psusi on 2007-09-24
Yea... just delete all the partitions... swap partitions are partitions used for swap... unallocated space is space that is not allocated to any partition... delete all the partitions and the whole thing is unallocated.

---

