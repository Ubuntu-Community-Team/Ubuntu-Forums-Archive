---
title: "Install partitions question"
date: 2006-06-11
forum: Absolute Beginner Talk
---

### Post by pvale on 2006-06-11
I've now got the Sager notebook machine that I posted earlier about in my hands, and have booted it from a Dapper CD. Everything works from the live session except wireless. So, I'm ready to shrink the WinXP partition and do a install of Dapper. My question concerns the partitioning options within Dapper. 

The machine has a 40Gig drive, and, after defragging WinXP, it looks like there is some data in the middle of the drive that WinXP's defragger won't move. So, I may only get the WinXP partition down to 20Gig or so. I want a small Fat32 partition so that I can share files between WinXP and Dapper. Will the partitioner in Dapper's install do this, or do I need to do something else to make sure that I end up with a 1-2Gig Fat32 partition? I seem to remember seeing a page, maybe in the how-to's or the Wiki about how to do this, but I can't find it now. Silly me forgot to bookmark it. Can anybody pass me that link again, please? Or have other input about how to do this?

BTW, where is everyody getting these small Tux avatars?

Cheers,
Perry Vale

---

### Post by JanVH on 2006-06-11
I have the exact configuration you want.

To be sure, I first partioned my disk with Partition Magic Pro, in Windows XP. I left the part to install Ubuntu to as empty space. I created the FAT32-partition in Windows, thus.

This way it works for sure...

---

### Post by richbarna on 2006-06-11
[QUOTE=pvale]I seem to remember seeing a page, maybe in the how-to's or the Wiki about how to do this, but I can't find it now. Silly me forgot to bookmark it. Can anybody pass me that link again, please? Or have other input about how to do this?

BTW, where is everyody getting these small Tux avatars?

Cheers,
Perry Vale[/QUOTE]
Here's your link :- [http://www.psychocats.net/ubuntu/partitioning.html]("http://www.psychocats.net/ubuntu/partitioning.html")

And you can Google Tux, that's what I did :) :-
[http://images.google.es/images?q=TUX+Avatar&hl=en&btnG=Search+Images]("http://images.google.es/images?q=TUX+Avatar&hl=en&btnG=Search+Images")

---

### Post by pvale on 2006-06-11
I don't have Partition Magic, at least a new enough one that will work with big partitions, so I'm going to have to do it with gparted on the live install.

---

