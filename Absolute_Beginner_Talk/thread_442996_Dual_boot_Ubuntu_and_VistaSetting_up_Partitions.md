---
title: "Dual boot Ubuntu and Vista:Setting up Partitions"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by stuffour on 2007-05-14
I want to dual boot Ubuntu and Vista on my laptop and the following setup is what I plan on using can anyone please help me as to how to go about it.
I want to set up my hard disk as follows
1. Vista System
2.Second Partition for my documents and other files
3./ for Kubuntu
4. Swap
and
5. /Home

According to my research a harddisk can have only four primary partitions so which ones do I make primary, extended or logical and how do I go about the whole thing

---

### Post by steve-shinn on 2007-05-14
Try this link :-

[http://apcmag.com/node/5162/](http://apcmag.com/node/5162/)

---

### Post by stuffour on 2007-05-14
The method posted on that site is what I am using but I dont want to use the largest continuous free space as specified there i want to manually edit my partition table and I know that an OS will only boot from a primary partition that is why i want to know which ones to use as primary or logical partitions

---

### Post by Big_Croc7 on 2007-05-14
That's not quite right - Windows will generally boot only from a primary partition, but Ubuntu (and Linux in general) don't care.  They can boot from a logical partition as well.

Extended partitions are a special type of partition - they can contain other partitions, but no data.  Logical partitions go inside an extended partition.  A disk can have one or zero extended partitions, up to 4 (primary plus extended) partitions and any number of logical partitions.

There's no other practical difference between a logical or primary partition, as regards speed etc.

So in your case I'd recommend the following:

Vista - primary partition

then an extended partition, with logical partitions inside it, for everything else

---

