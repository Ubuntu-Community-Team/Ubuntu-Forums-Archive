---
title: "Linux, drives and access points"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by jrgibb on 2007-06-15
Having just moved over the Linux (day 3 now) I'm still trying to get my head around the way Linux manages files / folders / disks etc. 

As I understand it Linux ignores c: e: f: etc and uses a file system to just say there's some more storage space here, where so you want to have it available in the hierarchy (the acces point), is this correct ? 

Having just sorted a probelm with authorities on a new drive I want to add a 3rd drive and want to know if I can use the same access point as the other drive I installed? 

Thanks,

J

---

### Post by Happy_Man on 2007-06-15
A basic overview of how Linux handles mounted stuff filesystem-wise:

Everything is under / . eg:
 
/
|
|----/bin
|----/boot
etc. 

Mounted external stuff (like CD, DVDs, external HDDs, and so on) are under /media. The files on said external media are under a folder, like /media/my_stuff. Only one media is allowed to be mounted per folder. So no, you can't have the contents of three different HDD's stored under one folder (unless it's RAID, but that's different). With me so far?

So i guess to answer the question, no you can't.

---

### Post by ryanVickers on 2007-06-15
If you want to change the mount point from /media/disk-#, I would recommend "Storage Device Manager".  You can pick new mount points and call them different things!

---

### Post by jrgibb on 2007-06-15
Thanks mate! 

So my basic understanding of the file system hierarchy is correct? 

I've created an access point for an internal drive to a folder I've created in my Home folder, is there a more logical place to have the access point or is it simply you can do it where you like?? 

Thanks I understand you can't access a second device at the same point, you mentioned RAID that was going to be my next question "therefore does Linux spread / manage data like a RAID device?" . . . . clearly no, it's good but not that good ;).

Thanks,

J

---

### Post by jrgibb on 2007-06-15
"Storage Device Manager" is that a std app or via Add/Remove Apps ?

---

### Post by ryanVickers on 2007-06-15
Yes, it seems to be correct.  Drive letters are stupid anyways, because you can only have 26 devices minus C, and floppy (A and B).  But in linux, "C:\" is / and everythng else that would be a letter simply has a mount folder, insted of a letter!

You can put the mount point where ever you like, I would have it right off og / if it was me, easy to type/find/etc. but it doesn't matter where.

I have absolutely no experience with RAID, but I think the easies way would be to plug your drives into a raid controler and then into linux, and just mount the controller as something.  Maybe this sounds totally rediculous, but like I said, no experience.

---

### Post by ryanVickers on 2007-06-15
> "Storage Device Manager" is that a std app or via Add/Remove Apps ?
yes, Add/Remove and install from there

---

