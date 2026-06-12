---
title: "Install freezes at partition"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by viergeame on 2007-03-22
I am installing ubuntu on my sister's computer with a dual boot.  I prefer to not do the partitioning on my own so I just select the option to have the computer do it.  It says the new partition will be about 27g.  I clicked continue and left it sit for 2 hours and it was still at that screen with the cursor still having the active symbol.  When I did the install on my own computer it didn't take anywhere near this long for the partitioning.  The only difference between my computer  and my sisters is the hard drive size.  Mine is only 5g, but I did a complete format.  Am I doing something wrong here or is it supposed to take this long?

---

### Post by mouseboyx on 2007-03-22
I like to do it better myself just change everything you need in gpart when you choose to do it yourself and then click next or whatever then it will do exactly what you want it to do and it will show you what it is doing.  I've never just let it do it itself so i don't know what happens but i know that when I chose the parts it worked.

make 2 parts one that is ext3 for the system root and one that is 1gig to 1.5 gigs that is a Linux swap.

to answer your question it usually only takes a couple of seconds to part it unless you have a really old HD

---

### Post by viergeame on 2007-03-22
I did end up trying to partition it myself but it wont make the partitions.  I tried to do it with gparted, i think, the one that comes with the installer.  I don't remember the exact error but it said something about not being able to resize the old partition.  I can't post the error message though because my sister took over her computer again, and I am going to retry the install in the morning.

---

