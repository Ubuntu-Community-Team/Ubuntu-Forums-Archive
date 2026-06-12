---
title: "Switching to 32bit"
date: 2006-07-29
forum: Absolute Beginner Talk
---

### Post by calvinthomas on 2006-07-29
By any chance is there an easy way of switching to 32bit version of ubuntu when I have already installed 64bit, I don't mind reinstalling over the top of this one if I can do this reasonably simply, i.e. put in the cd and click overwrite. What I don't want is for it to repartition my harddrive again, I just simply want it to overwrite, how do I do this?

Calv

---

### Post by ovimunt on 2006-07-29
You don't need to repartition. 

If you reinstall, when you reach the patitioning bit, choose the option to manually manage the partitions. In there, go to your linux partition and choose the option to format it. You may also need to change te mount point of that partition to ***/*** (root). Once you've done this, save the partition changes to the disk and carry on with the installation. At the next step you'll be asked to confirm the formating of the two linux partitions, the ***ext2/ext3*** one and the ***swap*** one.

*EDIT:* May I remind you that formating the partition will wipe ALL the data so take care and make sure you don't touch your Windows partitions.

---

### Post by Kilz on 2006-07-29
> **calvinthomas said:**
> By any chance is there an easy way of switching to 32bit version of ubuntu when I have already installed 64bit, I don't mind reinstalling over the top of this one if I can do this reasonably simply, i.e. put in the cd and click overwrite. What I don't want is for it to repartition my harddrive again, I just simply want it to overwrite, how do I do this?

Calv

Why are you interested in moving to 32bit? I just posted a link to a solution for maple. No matter what version you use, if the software isnt in synaptic/apt you may have problems.

---

### Post by calvinthomas on 2006-07-29
That is why I was thinking about switching as the other person seemed to have it working in 32bit, basically without Maple I may as well not have anything, its the most important package for me because i'm a Uni maths student and its basically the only package we use.

I can't see the solution in the thread you sent, am I missing something

Calv

---

