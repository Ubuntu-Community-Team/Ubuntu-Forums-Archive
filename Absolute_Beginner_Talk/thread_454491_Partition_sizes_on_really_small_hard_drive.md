---
title: "Partition sizes on really small hard drive"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by hummingbird59 on 2007-05-25
This weekend I plan to install Feisty Ubuntu on a compaq presario with only a 40gb hard drive.  I want to retain WinXP and dual boot because after trying WUBI, I still have a few minor issues that keeps me from going straight Ubuntu (ie, cd drive problem only in Feisty, printing photos(new Canon printer) and file backup onto external HD issue - all minor I know but really important to me.:().  Anyway, can anyone give me some specific info regarding partition sizes. I plan to manually partition using alternate CD.  I want to make windoz as small as possible (is 12gb too small) and then have the rest for ubuntu.  HOW do I accomplish this?  I really am intimidated by the partitioning thing having never done it before and having only one computer.  Can someone walk me through?  My specs are: 

Compaq Presario 40 GB HD
Pentium 4 1.5 GHz
1GB SDRAM

I know this is challenging with limited specs, but I'd really like to try it.  Anyone?

P.S. I have a similar post in the installation/upgrades forum.  That's why I decided to go the route of alternate install cd.  Just thought I might get really specific info in this forum since I am such a newbie:).  THANKS in advance!

EDIT:  Or post a review of a new dell desktop and make my weekend project disappear?  But whre's the fun in that?:lolflag:

---

### Post by apunc1 on 2007-05-25
This is definitely doable, but you're going to have to think a bit more about partition sizes. I suggest to best utilize your hard drive space to use the ntfs-3g so Ubuntu can read/write to nfts. Here is a guide.
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

It might you save some space if all your data files are on the nfts partiton. That way you won't need a huge /home or shared data partition. just a smaller /home partition for your settings.

Remember to defragment windows before you begin partitioning.

If you don't want to go that route, a partitioning scheme that might work would be

15gb windows -nfts
10gb for / (Ubuntu install)- ext3
15 /shared data- fat32
1gb /swap

good luck

---

### Post by apunc1 on 2007-05-25
or you could use fs-drive that allows Windows to read from and write to Ext3 partitions and have something like this

15gb windows -nfts
10gb for / (Ubuntu install)- ext3
15 /shared data and /home -ext3
1gb /swap

---

### Post by johnny4north on 2007-05-25
he is right on the money.. im to slow..:)
Illustrated Dual Boot Site -http://users.bigpond.net.au/hermanzone/
the link above will be a very good guide to partitioning you drive.  note - clean up windows[delete temp files] and defrag you windows first, then make a back-up of xp os.  find out if you drive is ntfs or fat32[which yours might be] then follow directions of the link above.  i would strongly consider getting another harddrive[40 or 80 gig]  to put ubuntu on it.  my ubuntu is filling up this 80gig drive at 15 gigs :D.  good luck..

---

### Post by hummingbird59 on 2007-05-25
Thank you apunc1 and johnny4north for the replies!  I have read big pond Herman's guide and have a copy waiting by my side for when I do this.  I'm just superparanoid about the sizing aspect being so cramped and all.  I think I will see if apunc1's partition sizes might work.  WUBI created a 10 GB folder and so far  I barely use 40% of it even though I have installed everything I want (so far).  I know this might change and might be different with a live install? , but I can live with it for now. Anyway, this is my preferred way of dealing.  I'll read the forum link too and see if its better.  BTW johnny4north, I have a C drive which is NTFS and a D drive which is fat 32.  I think c is 33GB and D is 7 GB, but I am not sure.  I'll have to log out and go back into windoz to see (from wubi won't I have to?).  Does this change either of your recommendations?  ALso, I have an external MAxtor60Gb hd that I considered booting from but I am serously new to doing this kind of stuff so I haven't tried it.  The howto guides seemed way over me head.  Plus, my external hd has all my music pix  and data on it.  Anyway,  any more suggestions based on the added info?  In the meantime, I'll go read some more.  Thanks again!:D


Edit:  c is ntfs 33.4 gb; d is 3.9 fat32 according to file browser view in ubuntu.  Does this change anything?

---

### Post by apunc1 on 2007-05-25
> **hummingbird59 said:**
>  WUBI created a 10 GB folder and so far  I barely use 40% of it even though I have installed everything I want (so far).  I know this might change and might be different with a live install? , 

remember that if you make a separate /home or shared data partition your / root ubuntu partiton doest have to be huge because all your personal files such as pictures, music, and video will be in /home or /shared, **always back up all data before partitioning.**

---

### Post by hummingbird59 on 2007-05-25
Hey apunc1.  Thanks for responding!  Everything is backed up three times over;).  This may be a dumb question -if so forgive me, but do I need a separate or home partition.  In other words, can I have:

15G  windoz ntfs
25G  ubuntu ext3
2G    swap ext3

or is that not possible?

Thanks again!:D

---

### Post by apunc1 on 2007-05-25
have you read some beginner guides?
here would be a good place to start
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

> /home partitions are wonderful things. It would be the equivalent of Windows of having a partition that was the C:\Documents and Settings folder. That would include My Documents, My Pictures, My Music, and all your hidden settings, too. Likewise, a /home partition in Ubuntu has all your settings.

if you do not have a /shared partiton, the /home partition would also have your files. read the links i have posted for more partitioning possibilities.

remember if you want to share files between windows and ubuntu such as music you're going to need a fat32 partition or use fs-drive or the nfts tool i've already suggested. 
so you have some choices to make, but there are suitable guides to fit your needs, as well as people here who can help.

edit: i forgot to add that since with a home folder your data and files will be on a separate partition than the rest of the installation so if you need to reinstall ubuntu or upgrade then you don't have to format your /home partiton so you can keep all your data intact.

---

### Post by hummingbird59 on 2007-05-25
Ahh yes, now I'm starting to put it together. :idea: Yes, belive it or not I have read everything on psychocats page.  It just really is alot to absorb being new to linux:).  I have even read and played around a little with NTFS3 with my WUBI install - I did have some issues but none insurmountable.  Anyway, I think I will go with your original numbers.  Thanks so much for holding my hand - sorry):P

---

### Post by gn2 on 2007-05-25
There's a tool available through Automatix that automatically mounts and makes NTFS partitions writeable.

With that in mind you could set it up thus:

Windoze 10Gb

My Documents (NTFS) 20Gb

Ubuntu 6Gb

Swap 1Gb

You wouldn't need a /home partition, because you can just use "My Documents" to keep your files in.

A shared Fat32 partition used to be recomended, but writing to NTFS from Ubuntu isn't as unreliable as it used to be.

[www.getautomatix.com](www.getautomatix.com) 
NTFS Read/Write Auto-mounter is in Miscellaneous

---

### Post by hummingbird59 on 2007-05-25
Hello gn2!  Now that is interesting!  The OS numbers seem small and I don't have that much need for document space (I store externally and via DVD) ie, my docs but that set up is definately worth thinking about!  Thanks!:popcorn:

---

