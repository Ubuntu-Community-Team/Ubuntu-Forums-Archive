---
title: "why can't I partition an HP laptop, even with automatic partition"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by patricio.ivan on 2007-11-24
I have a laptop HP tx 1215 nr, 160 hard disc, 1 Gb RAM and AMD turion64 x2.
the computer has two partition , 160 Gb windows vista and 9 Gb to recovey

I tried to install ubuntu 6.06.  But in the step 5, when I  configured  partition my computer report an error. it doesn't follow with the partition process.

I tried with automatic partitioning to install ubuntu  automatically.   But it doesn't work, neither  

Why can't I install Ubuntu in my computer =(.  And I already read the documentation

I appreciate any help to resolve this issue!!!!, thanks

---

### Post by ijason on 2007-11-24
are you trying to install ubuntu over everything? or are you trying to keep windows as well as running ubuntu?

if you're only wanting ubuntu, you'll need to boot off the install cd, and then run the >system>admin>partition editor. and you can use it to delete all the old partitions and create a new ext3 one that takes up the ENTIRE drive. after you finish that you should be able to install with no problems

ONLY DO THIS IF YOU WANT TO DELETE ALL WINDOWS OFF YOUR LAPTOP

---

### Post by Pumalite on 2007-11-24
With Vista, you have to allocate space for ubuntu with it's own partitioner first, then install Ubuntu.

---

### Post by patricio.ivan on 2007-11-24
I am trying to install ubuntu with my vista.  I tried to parititioner first from live CD with Gparted. But I can't ( even Gparted has the picture of a lock next to the windows partition)

Additionally, I can't acccess to my window partition, I mounted but I don't have permiss to access inside!!Is it related?

thanks

---

### Post by ijason on 2007-11-25
it sounds like what **pumalite** said, you'll have to use the windows vista partition editor first to free up some space. then you'll want to choose the option "install in the largest FREE contiguous space" on the ubuntu installation guide. that'll put ubuntu in the unpartitioned space you just cleared up.

---

