---
title: "partition help"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by frog3764 on 2007-02-07
Greetings to the Group - I am a newbie and am trying to install Ubunto 6.1?  My main partition is C with Windows XP on it.  I've added three more partitions for Linux.  I've chosen to manually do the partition so nothing will happen to my C.  I can't figure out the next screen where I'm selecting the three pariitions for the root etc.  The screen keeps wanting to add to my main hd C.  I would appreciate some help so I can get started.

Thanks in advance,
Jim in the PI

---

### Post by housam on 2007-02-07
What is the format of the new partitions ? Their sizes. What tool you used to create the new partitions.

---

### Post by frog3764 on 2007-02-07
I used Norton Partition Magic, used NTSF, and the sizes are about 10gb with the swap about 1gb

Jim

---

### Post by housam on 2007-02-07
Ubuntu can't be installed in ntfs format. it should be ext3 for the root and swap for the swap partition. 
Don't use partition magic for partitioning. Use Gparted instead ( it is on the live cd ).

---

### Post by frog3764 on 2007-02-07
I used the Gparted the first time, but was still confused with the three partition selections and the locations, so I went to Partition Magic thinking it might be easier to figure out.  W R O N G!  In that selection screen, If I remember right, the first selection to make is the primary, and according to the size listed, it's my C drive, and I don't want to mess that up.  Making those selections is what's confusing me

---

### Post by housam on 2007-02-07
How many partitions do you have in your pc. Remember that you permitted only to have 4 primary partitions on your HDD or 3 primary partitions and 1 extended partition. that extended partition can be devided to many logical partitions . ubuntu can be installed in primary or logical partition.

---

### Post by frog3764 on 2007-02-07
I only have 4 partitions, the main one for XP, and the 3 other I made with Partition Magic.  I will go back to XP and dump the partitions and try to start over. 

Later

---

### Post by frog3764 on 2007-02-07
I GOT IT!  Thanks for your help.  Getting rid of the Partition Magic helped me to understand what was going on.  Afterall, Partition Magic is for Windows - D U H !

Thanks again

---

### Post by housam on 2007-02-07
Glad that you did it.

---

