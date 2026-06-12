---
title: "Questions about repartitioning"
date: 2005-11-06
forum: Absolute Beginner Talk
---

### Post by Riot5 on 2005-11-06
Hello,

Firstly, thanks for taking the time to view this.

Secondly, on to the questions:

I have a Windows XP machine running off an 80 GB hard drive using NTFS, of which about 65 GB are full of just stuff (Windows, Games, Music, Photos, etc.).

I just downloaded and burned the Ubuntu 5.10 Live CD and ran it for the first time, and I was very impressed with it, and I decided I had to have it installed.

My plan is to have a partition for Windows, a partition for Ubuntu, and the rest of the disk will be a partition for the games, music, photos, and other stuff that can be shared between both OS'es.

So, I was wondering, when I repartition the disk, what kind of stuff stays on the disk and what kind of stuff will i need to back up?

Also, what sizes should I make the respective operating system partitions?

Thanks again for at least looking at this.
-D

---

### Post by earobinson on 2005-11-06
when you partition a disk everything should stay there, it is always a good idea to backup anything important, an I would leave at least 5 (including 1 gig ish for swap) gig for ubuntu but it only needs 1.8 gig (at least 5.04 did so 5.10 should be around the same).

Note: if you every are fealing adventures you could make a partition just for data that was fat32 that way both linux and windows could read at write to it.

---

### Post by aysiu on 2005-11-06
If 65 GB of it is files to share, you can't repartition without backing up the stuff. Resizing the NTFS partition will definitely destroy that information if the new size is less than 65 GB (think about it).

I'd back it all up (external hard drive, burned DVDs, burned CDs, whatever). Then, delete your files. Resize your NTFS partition, create a new FAT32 partition and a Ubuntu partition and swap. Ultimately, it should look something like this:

8 GB NTFS
65 GB FAT32
6.5 GB Ext3
.5 GB swap (assumes 256 MB of RAM at least)

It's going to be tight...

I'd highly recommend following these instructions for repartitioning:
[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

---

### Post by manicka on 2005-11-06
I'd suggest the following

20 GB NTFS (Windows)
10 GB Linux (ext3) for /
10 GB linux (ext3) for /home
512 MB SWAP
rest (FAT32) Shared

If you want to share data with windows it needs to be in the fat32 partition as Ubuntu can't write to ntfs, only read.

Apart from that my advice on what to backup, would be 'everything you don't want to lose'.

HTH

---

### Post by Riot5 on 2005-11-06
Awesome, thank you for the timely replies :D 

I'll take all this into consideration and get to burning those CD's!

-D

---

### Post by aysiu on 2005-11-06
[QUOTE=manicka]I'd suggest the following

20 GB NTFS (Windows)
10 GB Linux (ext3) for /
10 GB linux (ext3) for /home
512 MB SWAP
rest (FAT32) Shared[/QUOTE] Except that leaves only 39 GB left for the files to share between OSes. Isn't there 65 GB worth of that data? That's why I said it would be tight...

---

### Post by Riot5 on 2005-11-06
The 65 GB of data included everything currently on my hard drive, which leaves me currently with 15 GB of free space, so if at all possible, I want to separate out the "Windows only" kind of stuff and leave that on the NTFS partition, while putting the music, photos, games, and things of that nature on the FAT32 partition for use by both Windows and Ubuntu... Can I do that?

---

### Post by aysiu on 2005-11-06
[QUOTE=Riot5]if at all possible, I want to separate out the "Windows only" kind of stuff and leave that on the NTFS partition, while putting the music, photos, games, and things of that nature on the FAT32 partition for use by both Windows and Ubuntu... Can I do that?[/QUOTE] Yes, it's possible--if you have a way to back up the data. With the kind of rearranging we're talking about (where you're shrinking the NTFS partition to be smaller than the data it holds) you *have* to back up your data, not just for safety reasons, but for *functional* reasons.

---

### Post by Riot5 on 2005-11-06
Okay, I see your logic now.  So let's say I've backed up all the data I want to, then I delete all the stuff from the hard drive that I just put onto the backup media and get the remaining used space down to the target partition size and defrag the hard disk.  Then I follow the instructions that you posted and resize the NTFS to the size it needs to be, make the ext3 partition, the swap partition, and the FAT32 partition, then when all the installation is said and done, stick the backed up data in the FAT32 partition.  That sound okay?

---

### Post by aysiu on 2005-11-06
Perfect, except that I'd defragment the NTFS drive *before* shrinking it.

---

### Post by Riot5 on 2005-11-06
Excellent!  Thank you very much for helping me out with this! :D  I can't wait to get started.

---

