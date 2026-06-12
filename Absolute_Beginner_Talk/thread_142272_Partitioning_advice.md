---
title: "Partitioning advice"
date: 2006-03-10
forum: Absolute Beginner Talk
---

### Post by nalmeth on 2006-03-10
Ok, so I'm not exactly an Ubuntu beginner, but I've never done any partitioning, I've been all or nothing with my computers, because that was the fastest easiest way to get where I wanted to go.. So that's why I post this here
Now, I want to play around a bit, and make some changes.
I want to dual-boot dapper and breezy, and have an extra partition to share media between the two, and to act as a life support for my media in case of unexpected problems..
I've backed up my important docs, and think I'll use a liveCD for the partitioning.
Should I shrink down breezy, create an extra ext3, and one more for dapper? Or should I just leave enough space for dapper, and let the install CD do the partitioning?
I would just go with an upgrade, but my house of cards is built up pretty high, and it would be a pain to screw up the upgrade, and have to start from scratch, even though my media is backed up.. A dapper upgrade has screwed up breezy a couple of times for me, and I do know that it is more stable now, nearing official release..

Just looking for some thoughts, making sure I haven't left out something important.. Shrinking ext3 is not as risking as say NTFS right?

---

### Post by Sutekh on 2006-03-10
Mmm I did *alot* of re-partitioning the other day on my old drive.   It was formatted ext3 and contained a fair amount of files.  I backed-up everything but it wasn't needed (not to say its not a good precaution to take!)

I resized the partition and added 4 others, for Dapper, Dapper64, Xubuntu and storage.  
[ATTACH]6895[/ATTACH]
In all cases I created the partitions in Gparted, just so I could be sure that the sizes I wanted would work.  Its a lot easier (IMO) to resize/change/delete partitions when its all there in front of you with a nice bar graph.

Then when it came time to install I let the partitioner re-format those partitions and install.

So I would shrink Breezy, and create the partitions you need, and then let the installer use those partitions.  LiveCD would be fine, [Disk Drake]("http://qa.mandriva.com/twiki/bin/view/Main/DiskDrake") is another option

[Ubuntu Forums - Howto Use Disk Drake]("http://www.ubuntuforums.org/showthread.php?t=114142")

Because ext3 doesn't get fragmented like NTFS does, shrinking it shouldn't be a problem.  Let's see what else people have to say on this.

---

### Post by nalmeth on 2006-03-10
perfect. thanks for confirming that for me.. Will go ahead with it today :-D

---

### Post by cotcot on 2006-03-10
You have to check if your breezy was not installed on an LVM file system. (that was the default selection of the installer by me; but I do not like it at the moment because I do not know enough about LVM yet). If you have LVM then read the LVM howto : [http://tldp.org/HOWTO/LVM-HOWTO/](http://tldp.org/HOWTO/LVM-HOWTO/) 

If you do not have LVM : install dapper. Select manual partioning during the install, shrink breezy, create a new partition for common files and let the partitioner partition the rest for dapper  automatically.

---

### Post by nalmeth on 2006-03-10
[QUOTE=cotcot]If you do not have LVM : install dapper. Select manual partioning during the install, shrink breezy, create a new partition for common files and let the partitioner partition the rest for dapper  automatically.[/QUOTE]

Yep, not LVM, just ext3.
I didn't know the installer partitioner was that able.. I mean I heard it could do all that, but since I have not experienced it myself, I am not all that confident with it. Probably social engineering etc, but I just feel more comfortable seeing all the partitions in bar's and graph's etc, as Sutekh says. Graphical effect. This coming from someone who prefers doing most things in the terminal :-k 

This will be good experience for me.. Thanks for advice guys

---

