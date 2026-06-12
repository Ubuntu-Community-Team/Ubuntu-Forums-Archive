---
title: "&quot;Prepare Disk Space&quot; Issues"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by c-breakdown on 2007-03-29
I'm totally new to all of this and am finding myself quite overwhelmed.  I don't want you to think that the first thing I did was come to the forums and ask for help.  I have read a ton of different information and none of it has helped me so far.

So to my problem, when I get to Step 5 of the installation, Prepare Disk Space, I choose "Resize IDE1 master, partition #1 (hda1) and us freed space" and select Forward.  Nothing happens, ever.

I tried to understand how to "manually edit partition table" but I'm afraid my ignorance has me totally confused when it comes to that method, and the threads explaining it are way over my head.

Does anyone have any idea why I can't choose the option for it to partition itself?  I have already defragged a few times and tried various things.  Please help me free myself from the chains of Microsoft and capitalism!  I'm beginning to lose hope. -_-

---

### Post by zvacet on 2007-03-29
If you decide to go manualy you will see all patitions you have installed before(in case you are dual-booting with windows) adn they will be ntfs or fat32.You will use rest of drive(free space).depends of how much free space you have you can choose between automaticly create partition(if you have 10GB or less) and create new partition.Let´s say you have enough free space.choose create new partition and following is how willl be good way to do it.
1. root =10(maybe less but not lss than 5)GB  mountpoint /
2. home = rest of free space exept                   mountpoit /home
3.swap =512-1024Mb(depends of your RAM)

---

### Post by c-breakdown on 2007-03-29
The option to Create New Partition is disabled for me.   It is grayed out in right click and under file.  So what can I do?  I also have over 100 gigs of free space.

---

### Post by Staff Monkey on 2007-03-29
You may be having the same problem I did.  

When you use the "create new partition automatically" option (not a direct quote), and click the Next/Continue button, does it just "hang"?  When I would select this option, I would not get any response and ended up closing the program.  Apparently, gparted (which Ubuntu uses in its setup) is very careful when handling partition tables (this is a good thing!).  As such, if it detects any sort of error or disparity between table data and what it's seeing on the disk, it won't create a new partition.  In my case, I had a bad sector entry in the partition table.  Even after fixing the table, gparted wouldn't create the linux partition.

I finally had to use a commercial partition editor (though there are free ones out there that will work) working from a live cd to shrink my XP partition enough to fit the linux partitions.  Once I did *that* gparted was happy to use the new "free space" to create the necessary partitions. 

Hope this helps.

---

