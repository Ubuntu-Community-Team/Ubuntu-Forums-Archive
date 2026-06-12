---
title: "The fine mess I made of my partitions"
date: 2006-04-23
forum: Absolute Beginner Talk
---

### Post by morganpatrick on 2006-04-23
Hello all,

In repartitioning my ntfs drive to run ubuntu, I mistakenly clipped my data.

I defragmented my drive in windows. I had about 100 gigs of data on a 200 gig hard drive. I clipped this partition to 80 gigs.

I created a new partition for ubuntu, 80gigs. In the end i have:

sda1: windows recovery partition, 5.8 gib.
sda2: my clipped windows parition, 80.0 gib
sda4: what is apparently my ubuntu partition, reading 24.90 gib, 20.98 gib free
sda6: swap partition, 1.09 gib
sda5: what i thought was my new ubuntu partition, 74.50 gib, free space not available

Now: I backed up some of my most crucial data, but I really would like to locate and migrate my video, mp3s and things before i try to sort out my partition mess. I installed testdisk with the synaptic package manager.

sda1 is FAT.
sda2 is unformatted. This is because i busted the ntfs format when i resized.
sda3 id ext3.
sda5 is FAT as well.

NOW:
I think the ideal situation for me would be to have most of my data on a fat volume, so i can have all my music, movies, writings and what-have-you on a partition that I can access from windows and from ubuntu. in this scenario, the ubuntu partition would only need to be big enough to run apps. the windows partition would only need to run a few things like photoshop and dreamweaver, stuff i need for work. and my documents can be in the middle somewhere.

What would you reccommend as a sensible, delicate way of handling this situation? I have my music, a large part of the data, backed up on my iriver but I'm worried that if i take another step in the wrong direction I'm going to lose even more data than I already have. suggestions are much appreciated. Thanks in advance.

---

### Post by uzi09 on 2006-04-23
wow, seems really messy :S then again, it was kinda long and i skimmed it ;D

anyway -- when i went to dual boot my machine, i was trying to decide how to break up the partitions. please see this thread:

[http://ubuntuforums.org/showthread.php?t=151722](http://ubuntuforums.org/showthread.php?t=151722)

in summary:
1) QtParted to resize partitions (ntfs too!) - read thread for link. it is identical to Partition Magic and 100% FREE!
2) usually a good way to partition is xp(ntfs), ubuntu(ext3), /home partition(ext3). then just get a ext3 driver for xp so u can read/write data to/from linux partitions. (link for this is also in that thread some where and there is also a REALLY REALLY GOOD site that teaches u how to dual boot in lots of different ways with LOTS AND LOTS OF PICS! (see Princey's post).

good luck,
uzi

---

### Post by morganpatrick on 2006-04-23
yeah, I'm just afraid to do any more repartitioning until i can assess what data currently lays dormant but salvagable on the machine. Windows boots straight into the recovery disk, so the os is toast for sure -- indeed the filesystem is'nt even recognized anymore.

---

### Post by catlett on 2006-04-23
Do you have the partitions mounted in Ubuntu so you can access the data on them?

Skip that I didn't read closely enough. Your windows partition is unformatted and I assume that's hwere the data is. Can't mount it the way I know. Maybe someione knows a data recovery app for Ubuntu.

---

### Post by morganpatrick on 2006-04-23
well like i said I have testdisk. I dont see it in my apps though, maybe it's command-line only? hmmm

---

### Post by uzi09 on 2006-04-23
u may want to try System Rescue CD:
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

usually, u can use any linux live cd to be able to do this - including Ubuntu.
As bad as things seem with Windows, whenever I've ran into this problem, I've always been able to get my data off that partition by this method. Maybe u should just copy ur important files and reinstall xp on that partition.

let us know how things work out

---

### Post by Sef on 2006-04-23
Another rescue cd is trinity, which can write to NTFS files using captive-ntfs.

[http://trinityhome.org/trk/]("http://trinityhome.org/trk/")

---

### Post by morganpatrick on 2006-04-24
Should I try to put the non-ubuntu partitions back together first?

--uzi, thanks for the lead

---

