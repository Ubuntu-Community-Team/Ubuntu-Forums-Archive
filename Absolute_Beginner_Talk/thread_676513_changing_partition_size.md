---
title: "changing partition size"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by bigmahlman on 2008-01-23
so I am trying extend the Ubuntu partition to be a little larger, i want to try to use vmware, and need a bigger partition on the Ubuntu drive i guess.  


 (IF anyone reading this knows how i can use my current vista instillation in VMWare let me know.  If i can get Vista installed in vmware now iwill just get rid of my current isntallation.   )

anyways i used my windows disk tools to created an emty partiton thinking i could expend the ubuntu partition after that.    I cant figure out how to do that in widnows or ubuntu.   I installed gpared and its not letting me.   

This should be possible right.

---

### Post by nemilar on 2008-01-23
If you want to resize a partition that's currently in use (your ubuntu partition), you'll have to burn a gparted LiveCD and boot from it.

Here's a link:
[http://gparted-livecd.tuxfamily.org/]("http://gparted-livecd.tuxfamily.org/")

---

### Post by bigmahlman on 2008-01-23
thats sweet.   I can do that.

---

### Post by jaytek13 on 2008-01-23
Just of note, partitioning can be a dangerous endeavor. If you're just trying to extend, say, your home partition, then it shouldn't be a problem. But extending the swap and root partitions can risk a loss of system files.

---

