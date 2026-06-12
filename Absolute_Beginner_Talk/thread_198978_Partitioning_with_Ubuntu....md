---
title: "Partitioning with Ubuntu..."
date: 2006-06-18
forum: Absolute Beginner Talk
---

### Post by ZeusABJ on 2006-06-18
I recently purchased a nice new 320GB Seagate perpendicular drive for my Ubuntu Install. I'd like to partition it off a little (for organizational purposes). I'd like a 5GB Swap, and 40GB for the OS partition and use what’s left as a massive data partition. I already installed Ubuntu once and chose the option “Erase entire disc”. I found with this option I can’t resize my partitions because (once it allocates my swap) it uses all the remainder of the drive as an OS partition. I re-ran the install and tried to edit my partitions manually, but while I can create a 40GB partition I’m not really sure how to go about making it my “OS Drive”. Anyone know of any good partitioning guides out there that can help me get this figured out?

---

### Post by confused57 on 2006-06-18
Here's a couple:
[http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

There's excellent screenshots in the links, the 1st link is for the GUI desktop install and the 2nd link is for a text install.  Read over them, get some ideas; and post any questions you have concerning how you'd like to partition...nice HD.  If you have 1 Gb of ram, you shouldn't even need a swap partition..."/" is the root partition that the OS goes on, usually no more than 10 Gb would be required...you might want to set up a separate "/home" partition for your data, etc.  I'm just giving you some ideas for partitioning...once you have an idea of how you'd like to set up your HD, post back what you've decided on, or if you have questions...before you actually do the installation.

---

### Post by aysiu on 2006-06-18
[http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html) actually outlines the GUI desktop install.

The Psychocats link you linked to is not a bad thing to look at, though, as it talks about partition planning.

---

### Post by confused57 on 2006-06-18
[QUOTE=aysiu][http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html) actually outlines the GUI desktop install.

The Psychocats link you linked to is not a bad thing to look at, though, as it talks about partition planning.[/QUOTE]

Thanks for pointing that out...I can't keep up with all your HowTo's, which are excellent, by the way,...I think I'll just start referring people to the psychocat's homepage(probably all the information anybody would ever need).

---

### Post by ZeusABJ on 2006-06-18
[QUOTE=aysiu][http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html) actually outlines the GUI desktop install.

The Psychocats link you linked to is not a bad thing to look at, though, as it talks about partition planning.[/QUOTE]

Appreciate all the swift replies. I looked at all the links and it looks like aysiu's had what I was looking for. Thanks so much to everyone for being so helpful. I'm really coming along with Ubuntu and loving every minute of it!!!

---

### Post by ZeusABJ on 2006-06-18
Yep! Aysiu&#8217;s guide did the trick. However in my haste to deploy my partitioning scheme I neglected to tap the minds of more experienced Linux users than I on one matter. What do you guys think of my partitioning scheme? 

-6GB SWAP
-40GB Filesystem
-232GB Data

Anyone see any glaring flaws in my logic here? Also (out of curiosity) what sort of partitioning methods do some of you more seasoned Linux vets like to use? Also I'm a little dumbfounded. I reinstalled Ubuntu and purposely left 232GB of unpartitioned space (for my Data drive or any other partitioning schemes I might come up with). I was under the impression I could just go to System --> Administration --> Disks and partition away but it is telling me "Free space unavailable"?! So I don't use "Disks" for partitioning? Where do I go for that then?

---

### Post by aysiu on 2006-06-18
6 GB swap is way too much. Swap never needs to be bigger than 1 GB. Otherwise, it should be fine.

---

### Post by ZeusABJ on 2006-06-18
Thanks Aysiu, now about the partitioning. Am I supposed to install another application for that purpose?

*UPDATE* I found QParted under "Add/Remove" but everytime I try to use it I get an error message telling me I'm not logged in as root. Anyone know how I can fix this?

---

### Post by ZeusABJ on 2006-06-18
Well great, I got GParted installed and tried using it, but somehow managed to hose my install (again). Does anyone know of a good guide for dealing with partitions in Linux? I thought this would have just been as simple as creating a partition in my unallocated space, formatting it to EXT3 and then mounting it, but clearly I was wrong. Everythign was going so well, I suppose I was due for another problem.

---

