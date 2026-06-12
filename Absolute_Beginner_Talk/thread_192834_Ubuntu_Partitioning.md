---
title: "Ubuntu Partitioning"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by FuzZy2006 on 2006-06-09
I have just downloaded Ubuntu 6.06 LST and I think it's gr8 but i have problems at partitioning. I have 3 NTFS partitions and the 3rd has 20 gb free space. I tried to resize the partition and create a 10 gb ext3 partition and a 1 gb linux-swap partition but i can't because on an error: can't create new partition #1 or #2.
Pls hwlp

---

### Post by FuzZy2006 on 2006-06-09
anybody pls answer, c'mon i know you know how i should do it.

---

### Post by u.b.u.n.t.u on 2006-06-09
You waited 29 miniutes. Sometimes the person that knows an answer isn't online. If someone knows they will tell you. People look and see if they can help. Sometimes the question is more complicated and people don't want to give the wrong advice.

I have used gparted a lot, but mainly wiping NTFS and installing ext3. So sorry, but I don't know the answer to your question.

---

### Post by richbarna on 2006-06-09
I just completely borked my system with a partition resize !
I would however recommend going to aysiu's website [www.psychocats.net](www.psychocats.net)
He has excellent guides (which I will be using after my fresh reinstall).

---

### Post by FuzZy2006 on 2006-06-09
thx a lot ... but those tutorials say that the best way to do that would be making a FAT32 partition that would share files between the 2 OS's. Though I would like to make a Ubuntu stand alone, i'm not interesting in writing things on the NTFS win partition.

---

### Post by FuzZy2006 on 2006-06-09
my pb is that when i try to resize a ntfs partition and make one ext3 and linux-swap partition it gives me an error

---

### Post by xrchris on 2006-06-09
I suspect that error is telling you that you cannot have more than 4 primary partitions. 

Is this correct? If not what is the error message saying.

---

### Post by richbarna on 2006-06-09
Use partition magic  from xp to shrink the ntfs, then boot the ubuntu cd and tell it to install on the largest possible freespace.

---

