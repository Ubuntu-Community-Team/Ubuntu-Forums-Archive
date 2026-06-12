---
title: "How does this setup sound?"
date: 2005-10-25
forum: Absolute Beginner Talk
---

### Post by inovermyheadd on 2005-10-25
I plan on dual-booting like I've said a couple times and I just wanted to run this set-up by you guys.

I want a 15 gig xp pro partition...a 15 gig breezy partition(with swap)  and a 30 gig FAT32 partition to trade files b/n the two(jpg/mp3, AAC files only)


I am 2 lazy to start another thread...so I thought I'd ask this question...anyone know how long it takes for ship-it to send cds?  I'm not impatient I am just curious.

I appreciate it!

---

### Post by matthew on 2005-10-25
[quote=inovermyheadd]I plan on dual-booting like I've said a couple times and I just wanted to run this set-up by you guys.

I want a 15 gig xp pro partition...a 15 gig breezy partition(with swap) and a 30 gig FAT32 partition to trade files b/n the two(jpg/mp3, AAC files only)


I am 2 lazy to start another thread...so I thought I'd ask this question...anyone know how long it takes for ship-it to send cds? I'm not impatient I am just curious.

I appreciate it![/quote]

Setup sounds good. 

Shipit times vary widely depending on where you are in the queue and what the weather is like...I'm being a bit facetious, but there is an unpredictable delay for some people at customs or somewhere else and others seem to receive their orders in two or three weeks. I suggest you plan on waiting at least 6-8 weeks and be thrilled if they get there sooner.

---

### Post by jasmuz on 2005-10-25
Sounds nice, although....why make a separate Windows partition and an FAT32 one if you can have Windows in a FAT32 partition?

Shipit takes time depending where you live.

---

### Post by heimo on 2005-10-25
[quote=inovermyheadd]
I want a 15 gig xp pro partition...a 15 gig breezy partition(with swap) and a 30 gig FAT32 partition to trade files b/n the two(jpg/mp3, AAC files only)
[/quote] 
Sounds pretty good. On top of this, I recommend dividing the breezy partition into 7-8GB / and another 7-8GB /home (512MB-1GB for swap). This will make reinstalling a lot easier if that's ever neccessary. (EDIT: / stands for "root partition" which is the "main partition" of Linux, /home stands for the mount point or partition where home directories are, this separation of system data and user data makes life a bit easier and is suggested method for partitioning by many people on these forums)

[quote=inovermyheadd]
I am 2 lazy to start another thread...so I thought I'd ask this question...anyone know how long it takes for ship-it to send cds?  I'm not impatient I am just curious.
[/quote] From what I've heard, from 4 weeks to several months - some people complain never receiving CDs they ordered (I can imagine the volumes shipit must handle!). Maybe you can get a copy faster from a friend / school / co-worker? Also copies of Ubuntu are sold in various places and some people on these forums send CDs if asked (but understandable can't advertise this openly...)

---

### Post by inovermyheadd on 2005-10-26
[QUOTE=jasmuz]Sounds nice, although....why make a separate Windows partition and an FAT32 one if you can have Windows in a FAT32 partition?[/QUOTE]


I planned on making my windows partition NTFS in hopes of keeping the windows and linux partitions more separate...That might not make any sense but it does to me in my mind at this current moment in time, hehe. :)

---

### Post by inovermyheadd on 2005-10-26
[QUOTE=heimo]Sounds pretty good. On top of this, I recommend dividing the breezy partition into 7-8GB / and another 7-8GB /home (512MB-1GB for swap). This will make reinstalling a lot easier if that's ever neccessary. (EDIT: / stands for "root partition" which is the "main partition" of Linux, /home stands for the mount point or partition where home directories are, this separation of system data and user data makes life a bit easier and is suggested method for partitioning by many people on these forums)

 From what I've heard, from 4 weeks to several months - some people complain never receiving CDs they ordered (I can imagine the volumes shipit must handle!). Maybe you can get a copy faster from a friend / school / co-worker? Also copies of Ubuntu are sold in various places and some people on these forums send CDs if asked (but understandable can't advertise this openly...)[/QUOTE]


I like that suggestion a lot!  Thanks.  And if anyone has any info on the bottom half of this post please feel free to email me;)

---

### Post by matthew on 2005-10-26
[quote=inovermyheadd]I planned on making my windows partition NTFS in hopes of keeping the windows and linux partitions more separate...That might not make any sense but it does to me in my mind at this current moment in time, hehe. :)[/quote]
It does make sense and will work well for you.

---

### Post by Htr88888 on 2005-10-27
As far as the shipit cd's go, I ordered 500 about a month ago. I will hope to see them before the second semester of school starts. I would like my students to have them, as well as the linux club. If you guys have any idea if this version works on the i925xe chipset it would be gratly appreciated.

Asus P5AD2-E Premium
P4 EE 3.73
Asus 7800 GT Gamer Edition
Asus Star Ice Heatsink
Asus Vento 3600 Case
4 gigs Crucial DDR2 667 RAM
PurePower 680W PSU
2 Plextor SATA DVD Burners
4 Raptors
Dual NEC 19" LCD's
(BTW i had to take out a second mortage on my house for this system)


"Those who live for fame never amount any wisdom, yet those who live for wisdom amount all the fame they hope to attain." - Htr88888

---

### Post by MRCuadra on 2005-11-30
I thought I would post a reply since I just received my disks... Here's my experience:

I ordered them (through ShipIt) October 14th;
ShipIt sent the order to the shipping company October 19th;
I just got them this last weekend, November 26.

So, five weeks from (Ubuntu) to northern California, USA... probably average ;) 

I know how you feel, though. I was really beginning to wonder by the fourth week, but then I was really excited too! :p 

As far as your install goes, I'll be doing a similar thing to one of my machines. I'm reinstalling Win2K, with the minimum things I need (yes, all you Linux zealots :rolleyes: , I have no choice because my business is based on AutoCAD, otherwise, I'd be right there with ya!) Sorry, I digress... Anyway, I've formatted in NTFS to make "talking" with my main machine(s) easier. I'll use the extra space (actually, a whole other drive) to partition for Ubuntu.

I can't wait to really start messing around with it!  :D

MRC
A Space In Time
----
"Any sufficiently advanced technology is indistinguishable from magic." — Arthur C. Clark

---

### Post by akniss on 2005-11-30
Your setup sounds similar to mine (only for a smaller drive).  I have an 80GB laptop HDD setup as:
25GB Windows NTFS
30GB FileStore Fat32
24GB Ubuntu Ext3
1GB Swap

I like having the Windows installation on NTFS to help in restoring when (not if) it crashes.  Recovering from FAT32 can be a lot more difficult, since it is not a journaled file system.

---

### Post by akniss on 2005-11-30
[QUOTE=Htr88888]
Asus P5AD2-E Premium
P4 EE 3.73
Asus 7800 GT Gamer Edition
Asus Star Ice Heatsink
Asus Vento 3600 Case
4 gigs Crucial DDR2 667 RAM
PurePower 680W PSU
2 Plextor SATA DVD Burners
4 Raptors
Dual NEC 19" LCD's
(BTW i had to take out a second mortage on my house for this system)
[/QUOTE]


Good God!!!  Maybe you should be helping with the human genome project with that thing!!!!

---

### Post by yeahyeahyeah on 2005-11-30
I kept XP on it's own NTFS partition, for the same reason.

NTFS has some advantages over FAT32, like much larger filesizes, and I'm pretty sure it's more reliable. If I'm wrong, let me know. I would love to do the same thing with a "share" partition as FAT32, but I'm concerned about data integrity.

[QUOTE=inovermyheadd]I planned on making my windows partition NTFS in hopes of keeping the windows and linux partitions more separate...That might not make any sense but it does to me in my mind at this current moment in time, hehe. :)[/QUOTE]

---

### Post by firenurse4 on 2005-11-30
[QUOTE=akniss]Your setup sounds similar to mine (only for a smaller drive).  I have an 80GB laptop HDD setup as:
25GB Windows NTFS
30GB FileStore Fat32
24GB Ubuntu Ext3
1GB Swap

I like having the Windows installation on NTFS to help in restoring when (not if) it crashes.  Recovering from FAT32 can be a lot more difficult, since it is not a journaled file system.[/QUOTE]

Boy does this look famaliar. The only thing I did different, was I shrunk my Windoze patition down to I think 15GB.  If I ever reinstall XP, I will shrink that partition down even further.

---

### Post by az on 2005-12-01
Some forum people are more than happy to mail you a home-burned cd in time for the hollidays:

[http://ubuntuforums.org/showthread.php?t=90650&highlight=giveaway](http://ubuntuforums.org/showthread.php?t=90650&highlight=giveaway)


Also:

fridge.ubuntu.com


And:

[https://wiki.ubuntu.com/forum/GiveAway](https://wiki.ubuntu.com/forum/GiveAway)

---

