---
title: "Setup for Windows on External and Ubuntu on Internal?"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by quicksilver1024 on 2007-06-11
Hi there,

I have decided to take the plunge into the world of Linux! I have already read several pages and threads regarding the transition from Windows XP to Ubuntu 7.04, but I still have a few concerns and questions for my particular case.

I have an internal HD of 80 gigs and an external HD of 250 gigs. I wish to run Ubuntu on the internal HD and Windows XP on the external. The problem is the partitioning and keeping my Windows XP exactly the same.

My questions are:

1. Can I use Acronis Trueimage to clone my Windows XP (with settings intact etc..) to the external HD?
2. Can I even boot Windows XP from the external?
3. How should I plan my partitioning and what software should I use?

I am thinking of completely using the internal HD (80 gigs) for one partition, that is, for Ubuntu and split the external HD into two partitions - one for Windows XP and the other for /home.

Any ideas on yet another noobie situation? :D

---

### Post by trent dillman on 2007-06-11
...

---

### Post by reidms on 2007-06-11
> **quicksilver1024 said:**
> 
2. Can I even boot Windows XP from the external?

Does your bios support booting from USB? (if that is the type it is)

---

### Post by quicksilver1024 on 2007-06-11
My external is already formatted as NTFS which I heard somewhere that it is fine to keep it that way. There is a repository (am I using the word correctly? lol) that will allow Ubuntu to access a NTFS partition.

Can you please be more specific about how much disk space required for each of the 4 partitions? Also, are you saying I should put all those 4 partitions onto the internal HD while using the external HD for my miscellaneous files? I have a LOT of documents (such as spreadsheets and music) that I will need access to from either Linux or Windows, should I put those documents into the external HD?

Thanks!

---

### Post by lazyart on 2007-06-11
Linux would fare better on an external than WIndows will.  Can you even install windows on an external drive?  That is, without jumping through serious hoops?

---

### Post by Inxsible on 2007-06-11
I have a 160GB internal partitioned as follows:
C: 25 GB Windows -- NTFS
D: 25 GB Windows Data -- NTFS

/ : 9 GB root -- EXT3
/home: 20 GB - EXT3
swap: 1GB -- EXT3

/shared: ~ 70 GB -  used by both Linux and Windows --EXT3

/shared is where I keep my music.

I also have a 500GB external formatted in EXT3 which i use as backup. I use [FS-Driver]("http://www.fs-driver.org") to access EXT3 partitions from Windows

The above is something that suits me. You can probably get an idea of how things look like and do it the way you want.

---

### Post by quicksilver1024 on 2007-06-12
Why do you need a 500GB HD for backups? Isn't that a bit too excessive?

My problem is that I have a lot of multimedia on my computer right now. Will I use the /shared to store most of my multimedia? And do you recommend me putting all of my multimedia (plus music) on the external? An obvious problem with that is that I will need to have my laptop connected to my external to listen to music.

I am just worried that by having 2 OS's on the internal HD, I won't get enough space to put my files on the internal.

Also, what is the swap and windows data partitions for?

THANKS AGAIN

---

### Post by Inxsible on 2007-06-12
> **quicksilver1024 said:**
> Why do you need a 500GB HD for backups? Isn't that a bit too excessive?

My problem is that I have a lot of multimedia on my computer right now. Will I use the /shared to store most of my multimedia? And do you recommend me putting all of my multimedia (plus music) on the external? An obvious problem with that is that I will need to have my laptop connected to my external to listen to music.

I am just worried that by having 2 OS's on the internal HD, I won't get enough space to put my files on the internal.

Also, what is the swap and windows data partitions for?

THANKS AGAIN

Like i said, what i told you before was something that suits me for my needs. Maybe 500 GB is too much for you. I have my music on the /shared -- which is an internal partition. I also have the same music and a bunch of other stuff on my external as backup.

Swap is something that is used when you run out of RAM -- kind of like a page file in windows. (in extremely generic terms)
windows data is where I store anything i install in Windows -- like games or TurboTax and other such stuff that i cannot use in Linux. You dont necessarily need windows data partition if you dont want. 

I re-iterate, what i listed before is what I have, not something that everyone should have. Tastes differ and people have different systems. I gave you my system hdd specs, so you could get an idea of how things are and then decide what you want to keep and what you dont.

---

### Post by quicksilver1024 on 2007-06-12
Oh - I see. 
Thanks for clearing those questions for me :p

---

### Post by Inxsible on 2007-06-12
No problem at all. Hope all goes well with your install. Good luck !

---

