---
title: "Recommendations... Partitioning"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by HarshReality on 2007-09-13
OK, so I built a new box and popped a 500G SATA2 drive in got just about all the kinks worked out. Ive been doing alot of crying about the forums as some may have seen lol.

Initially I popped windows on (160G partition) and made a ghost image on a hidden partition incase of emergency and installed Ubuntu setup as dual boot so I could get aquainted... after a month or so of "Doh! and Opps" I think Im ready to do away with the windows partition and set the whole of it linux and then maybe run XP in VMWare (for those oddities I cant get n linux VS.Net etc.). So here is what I wouldlike to do... of course proposed alterations are always welcome....

My current Ghost partition is Fat32 so I plan on making it a bit larger (dunno how large as I plan to add a linux backup to it for home... unfamiliar with if it needs to be the same size etc.) so figure on @ 420G linux. Obviously I want my home directory seperate for crash/upgrade reasons but can you guys offer some recommendations for partitions. I do want root large enough for expansion but Im not really familiar with nominal vs excessive here. Incidentally I have 2G of memory here and plan on upping it to 4G and found a neat tutorial on Ubuntu Studio I plan on using for the install.

Actually a bit excited about this... planned it for a long time just never been in a minimal install position to do it.

---

### Post by notwen on 2007-09-13
500GB
---
|--  / (20gb) this should be way more than sufficient, 10 would be enough
|-- /home (200gb) 
|-- /media/backup (278gb)  backup partition
|-- /swap (2gb) although with as much ram as you have you could probably go with a much smaller swap


You could size the /home and /media/backup partitions differently, depending on what you plan on putting on this /media/backup partition.  I try not to access my backup partitions unless I'm copying over new data, so if you would be storing files other than backup data(mp3s, movies, etc) I would make a separate partition for those as well.  I personally keep my system very clean and have never had a /home that large as I don't keep files that would consume alot of space in my /home partition.   Good luck w/ whatever partition table you decide on.

---

### Post by Nulifier on 2007-09-13
A 500 gig hard drive is huge for linux so I would recommend a ~20-25 gig root (you seem to have space to spare). Give yourself a huge swap file (like 2-4 gigs) because you have room to spare and since I assume you are not going to be running a server you should not need to make partitions for /var and whatnot.

I remember reading something about booting a vmware image off of a partition which allows you to run XP both in vmware and on its own, but I remember trying to do this and I remember I was foiled by it being a SATA drive. They may have changed this or I may remember wrong, but if you have a extra IDE drive It should work. If you do not do this and run XP out of a image file then you will probably want a fat32 partition to map to both linux and XP so you can share files between the two.

As to ghosting I do not believe that they need to be the same size, just that the ghost needs to be > the backup. I do not usually use ghosting so I really dont know.

As to the size of / (not including home) I have Linux running entirely in a 20 gig partition and I am only used 3 gigs of it (I don't really have any large multimedia files but that holds alot of packages)

I hope this answers your questions and if you have any other problems dont hesitate to ask.

---

### Post by HarshReality on 2007-09-13
Thanks for the input this really helps me out alot.

---

### Post by newman on 2007-09-14
20GB for /
4GB for /swap
and the rest for /home

I like it simple, and a separate /home partition lets you reinstall the OS without losing your data

---

### Post by hyper_ch on 2007-09-14
if you want to hibernate you should have the SWAP at least the size of your ram...

---

### Post by dptxp on 2007-09-14
10-15 GB for /. Maybe 20 but 10-15 is large enough.
10-15 GB in ext3 for any other OS you may try. You can use this as data partition too.
20 GB OR more for /home.
Rest excluding space for SWAP for DATA. 
Well 2 to 4 GB SWAP.

More data partition help you keeping the disk clean. You can move the data to another and back to
prevent defragmentation. You can resize partitions by moving data to other. You can keep different
types of data in different partitions. You can set different r/w options.

---

### Post by newman on 2007-09-14
> **hyper_ch said:**
> if you want to hibernate you should have the SWAP at least the size of your ram...

Good luck with that. I haven't been able to get hibernate to work in ubuntu 32 or 64 on any of my PC's...

---

