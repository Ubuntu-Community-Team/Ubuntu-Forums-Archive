---
title: "Help With Partioning"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by cerealtx on 2007-09-15
hey guys, ive had 7.04 before but due some complications got uninstalled and now im installing a dual boot 4 the first time xp/unbuntu, i have xp already installed and already have 3 partitions setup, one for windows, one for linux and one for my files, im stuck on the install on the partioners i don't want to undo work ive already done i just need help pointing to the right directory or partition anyone help?

---

### Post by psusi on 2007-09-15
Just choose manual partitioning and point it to the correct partitions for / and /home.  You also might want to make a swap partition.

---

### Post by cerealtx on 2007-09-15
i was under the impression that i could use my largest partition as a swap
so i edit the already exsisting partition and set the mount point to /home but what do i set the use as to?
edit: i think i got the mout point, i just set it to / correct? i still not sure what i should set the use as 2 and am clueless about swap, sorry for the idiot questions im 100% new to partitioning

---

### Post by psusi on 2007-09-15
Why would you want to use your largest partition for swap?  You only need about as much swap as you have physical ram, and there isn't much reason to have a separate /home partition.  Simplest just to have one for / and one for swap.

---

### Post by cerealtx on 2007-09-15
okay i got my swap setup and the / i set them to fat32 is that correct? and should i set my largest parition up as fat32 aswell? and what do i set the mount point 2? ty vey much for the help

---

### Post by psusi on 2007-09-15
No, fat32 is a windows filesystem.  The default filesystem for Ubuntu is ext3, so you should leave it there.  The mount point for / is, of course, /.  swap should just say swap, as it has no actual mount point because it is not a filesystem.

---

### Post by cerealtx on 2007-09-15
thank u  very much i think i got everything squared away, sorry for the bother but thank u kindly just the same

---

