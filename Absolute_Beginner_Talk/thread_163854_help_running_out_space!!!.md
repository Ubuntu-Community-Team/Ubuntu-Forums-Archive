---
title: "help running out space!!!"
date: 2006-04-21
forum: Absolute Beginner Talk
---

### Post by abu-fatu on 2006-04-21
i am runnning out of hard drive space as you can see i have too many partitions.
i would like to turn my /dev/hdc10 partition merge it with /dev/hdc/8 and get rid of some of my swap partitions to give me more space. please post instructions in the form of 
a.do this 
b. then do this 
c. etc....
thank you.

---

### Post by Sef on 2006-04-21
I would try either ultimate boot cd or system rescue cd.

[http://www.ultimatebootcd.com]("http://www.ultimatebootcd.com")

[http://www.sysresccd.org/]("http://www.sysresccd.org/")

---

### Post by catlett on 2006-04-21
You have plenty of space. You don't have to rearrange things if you don't want to. You have almost 7gb on your first ext3.
Do you have that partition mounted so you can use that space?

---

### Post by BoyOfDestiny on 2006-04-21
[QUOTE=catlett]You have plenty of space. You don't have to rearrange things if you don't want to. You have almost 7gb on your first ext3.
Do you have that partition mounted so you can use that space?[/QUOTE]

Only thing is to merge those swaps. Also that 792mb of unallocated space...
It's been a while since I've messed with paritions outside the installer... Just delete the swaps... Make 1... Not sure about merging the empty space with ext3...

It'd be nice to know how these partitions are mounted, can you show Devices tab from system monitor?

I have 3 partitions,

/
/home
swap

If you can get your /home data on a partition, make one for root like 6-7 gig, I'd do a fresh install personally... Ubuntu Dapper Beta is out...

Either way, gparted lets you play with the partitions before applying the changes (I believe)... I wouldn't recommend really changing anything if it's not backed up...

Good luck

---

