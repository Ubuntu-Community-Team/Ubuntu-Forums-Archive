---
title: "Running scared!"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by Strasher on 2007-12-29
Hi everybody!,
Well I am new to Linux. I don't really have that much information about setting up partitions or resizing them. So am turning to the helpful minds of the Ubuntu forums! ^_^
Ok on the the issue
Am trying to install Ubuntu onto a rather new acer laptop.
But windows has taken up all my hard drive space! So I try to resize the partition and i got 
file system is reporting the free space as 397213 clusters, not 397227.
What does that mean? Is it going to kill windows?

---

### Post by pavel989 on 2007-12-29
numbers.

what are you using to change the partition?
i suggest gparted, you can get an iso cd of it and use it, which is pretty safe to use, but always backup everything.

the numbers is just saying, from my understand, is a specific number. so when you try to get an approximate partition, itll round to the closest possible. look at these sites:
[http://web.ukonline.co.uk/cook/Clustsize.htm]("http://web.ukonline.co.uk/cook/Clustsize.htm")
[http://kb.iu.edu/data/ahim.html]("http://kb.iu.edu/data/ahim.html")

so the fact that the numbers changed doesnt mean that your windows will break, nor does it mean that the resize will definitely go unproblematic.

---

### Post by CatKiller on 2007-12-29
I did a Gutsy install the other day, and  the partition part of the installer is now hideous. It used to be much more user-friendly. On the live cd there is a tool that I believe is referred to as "Partition Editor", but that is gparted. I would use that to resize the partitions in a nice graphical interface, and then pick "largest free space" when you go to install.

---

### Post by Sef on 2007-12-29
Read [Psychocat's Installing]("http://www.psychocats.net/ubuntu/installing").

---

