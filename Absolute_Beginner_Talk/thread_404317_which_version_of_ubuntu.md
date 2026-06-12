---
title: "which version of ubuntu"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by snobby500 on 2007-04-08
Hi

    I have an amd athlon 64 bit processor, but I am wondering if I should download the 64 bit version of ubuntu or if I should save myself the time and use the 32 bit version I have here on cd. I dont know how much better 64 bit is and if its worth it or not, are all the programs still compatible with the 64 bit version, and all the drivers too? If it doesnt have the same amount of software then ill just chuck the 32 bit version on to it. 

    Also I am a newbie when it comes to ubuntu, so I was wondering which ubuntu to puton my pc, I have dapper drake on a cd, but im pretty sure I want to  use beryl, so that means (*as far as I under4stand it) I have to upgrade to at least edgy (unless I want to filddle around, which wouldnt be a good idea I think bercause im new to ubuntu), so my question is, should I get edgy? or should I install dapper drake onto my pc and upgrade though that? and when fiesty comes out should I upgrade again? *(is it already out? :))

     Also, I have 120 gb hard drive, I am pretty certain im gonna put in an extra 320 gigs soon, but im wondering, I have 30 gb left on my current hd and I want to share filoes between my winxp (32bit) and my ubuntu, so how much would you say I should partition? When i get new hd I have to format it into fat32, is that correct for me to share files between the other os (xp)?

     thanks, srry 4 the long post

---

### Post by arron on 2007-04-08
This hoarse has been kicked :-)  Have a look here:

[http://ubuntuforums.org/forumdisplay.php?f=134](http://ubuntuforums.org/forumdisplay.php?f=134)

Many people have asked the same question.  If your a newbie, I would recommend the standard I386, less problems to learn Ubuntu.

Welcome to the Ubuntu Community!

---

### Post by Ender Black on 2007-04-08
I don't have all the answers (or none really...but) I also have a 64-bit processor (Intel Core Duo) and I am using the 32-bit Edgy Eft with Beryl.  I haven't had any stability issues that can not be traced to something that I did tinkering with configuration files.  If I were in your shoes, I would install Edgy Eft and upgrade to Feisty Fawn when it releases after beta.  

BTW... drooling over your storage capacity... wow.... My little laptop with 2 x 60 GB harddrives feels bad now.... lol

---

### Post by freebird54 on 2007-04-08
A few things there.  First off 64 vs 32.  I would choose 32 unless you have a particular use for the extra speed (ie much graphic processing/rendering or heavy music encoding) as there are still some issues with drivers - and even a few programs I understand.  Hopefully somene using the 64 will enlighten you further.

Next: version.  I have found Edgy to be very stable, so I wouldn't hesitate to recommend it.  Feisty will have some improvements though, so if you don't mind some more frequent updates it can be worth it.  More auto-configuration for one thing, and less command line tweaking necessary.  Dapper I would leave to the commercial users, and those running web sites etc...

AS for the hard drive - if you have 30 Gb left on the current drive, I would install to 20 Gb of it for now.  1Gb for swap, 7Gb for / (root) and 12Gb for /home.  When you add more drive, you could move /home to a bigger area at that time if desired.  As for file systems - you can run almost anything anywhere now.  The ntfs-3g driver from Ubuntu can read and write NTFS pretty well now (if not compressed!) and explore3fs (?) is an explorer that can access ext3 LInux partitions from Windows.  It comes down mainly to which side you will use it from more!  I find that using ext3 is a good bet, because i rarely go back to Windows now that I've had Ubuntu a few months, an the journaling means a more reliable FS than NTFS or VFAT.  I wouldn't use VFAT by choice any more - it is unnecessary.

Hope that gives you something to get on with!

---

### Post by snobby500 on 2007-04-08
lol, and thx

alrite, thx 4 all the hlp :) ill go with 32 bit 4 the mo.
btw, can i share folders with my winxp somehow? or only when i get my new hd?

ps, ender black it aint fair, easier to get cheap capacity on desktop :P plus u got cor2duo ;)

---

### Post by snobby500 on 2007-04-08
thx freebird54
ok, ill do it now lol :), 20 gigs/upgrade to edgy after installed and (i think ntfs, see whats available). 

btw, i  have never got replies so fast from any other forum, thanks :)

---

### Post by arron on 2007-04-08
You can share over the network with windows using samba.  To use the windows drive, ntfs you can look at, to write you will need ntfs-3g.  I think you will be a lot better off with the 32 bit imho.

---

