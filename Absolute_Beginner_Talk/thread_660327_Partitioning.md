---
title: "Partitioning"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by Truck449 on 2008-01-06
I know there have been many posts on this subject but i have not come across any for this particular model computer and was hoping for some suggestions on how exactly to partition for my upcoming linux install

Dell XPS M1730, Mobile Intel 2.8GHz,EX, 4MB, 800 FSB Merom
2GB, DDR2, 667MHz 2 Dimm for XPS M1730
200G 7200RPM SATA Hard Drive Free Fall Sensor

Any suggestions on partition sizing and what not im still fairly new to ubuntu and any help would be greatly appreciated

---

### Post by PeterJS on 2008-01-06
The system specs (aside from hard drive size) really don't have any effect on how partitioning should be set up. The real question is how much time do you plan on using each OS, and how much free space do you have and of that how much can you afford to give up to install linux on.

---

### Post by Truck449 on 2008-01-06
Im trying to spend as little time on windows as possible, i will be running windows vista for gaming and programs dependent on windows, for browsing, chatting and daily use i will be running ubuntu

---

### Post by PeterJS on 2008-01-06
Games generally take up a bit of space, I'd suggest leaving the vista partition on the large side. 30 gigs for ubuntu would be huge, 5 is the absolute bare minimum, and 10 is the smallest I would suggest for a system. The advantage of this is that ubuntu is much better about reading files from ntfs than vista is about reading ext3. So you could keep all your games, media, and other big stuff on the vista partition.

Vista is picky about letting 3rd party apps resize it. So you'll  want to use the vista disk manager to shrink it. And when you install ubuntu select use largest free space and it will install it self in to the free space left over from shrinking vista.

---

### Post by Truck449 on 2008-01-06
I was considering going for half and half in order to store music and other media in linux, On my current computer i have a 30gb partition set aside for ubuntu and have run out of space quickly is there a way for windows and ubuntu to share save files such as games and music.

---

### Post by PeterJS on 2008-01-06
Save files for games would be tricky. For the music just leave it on the windows partition in an easy to find location like C:\Music and you can just point media players in ubuntu at it, no sense in keeping to copies of the same media on the same machine.

---

### Post by jken146 on 2008-01-06
I would recommend 10-15 GB for / and a maximum of 1 GB swap (you'd be *very* hard pressed to use more).

---

### Post by Truck449 on 2008-01-06
thanks for all the info guys im curious ive heard of people going with partitions as large as 100gb for their linux is there a reason to keep the partition smaller

---

### Post by Truck449 on 2008-01-06
is it just pointless to have that much space for your linux? Do most people just access their save files on the windows partition?

---

### Post by PeterJS on 2008-01-06
Disks are finite in size, the more space you give linux the less there is for window. Given that reading windows from linux is easier than the other way around, leaving free space on windows makes sharing stuff that can go anywhere (like media) easier, and windows has larger stuff that expects to be in a specific location (like games).

---

### Post by Truck449 on 2008-01-06
thanks for all the help guys sorry to be such a noob but i was also wondering about swap partitions are they just an extension of ram space in essence? What makes them so important when partitioning?

---

### Post by louieb on 2008-01-06
> **Truck449 said:**
> ... wondering about swap partitions are they just an extension of ram space in essence? What makes them so important when partitioning?
Its size is important only if you plan to hibernate the computer. If so I recommend 1.5 x ram.  Otherwise half a gig is plenty.

---

### Post by PeterJS on 2008-01-07
> **Truck449 said:**
> thanks for all the help guys sorry to be such a noob but i was also wondering about swap partitions are they just an extension of ram space in essence?
That's exactly it.
>  What makes them so important when partitioning?Nothing, above and beyond the fact that it's generally uses a dedicated partition that needs to have space made for it. It's mostly a matter of you're setting up disk space for other things, so it make sense to set up disk space for swap at the same time.

---

### Post by allforcarrie on 2008-01-07
if you dont feel like partioning you could try WUBI.

---

