---
title: "[SOLVED] Linux os to improve comp efficiency??"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by N1N31NCHN41L5 on 2008-03-20
I am running a Dell Lattitude C400 with a 1.2g cpu and 256mb ram memory. I'm running xubuunu 7.10 Gutsy Gibbon it it. It runs OK but bogs down pretty bad sometimes, the little display on the bottom of my task bar shows 220 of 248 mb of memory used continuously . What can i do to take the memory usage down and make xubuntu faster or do i need a different Linux OS. If i switch I want one that can run what xubuntu can, including Wine.

Please help

---

### Post by bwang on 2008-03-20
When you first log on, how much RAM does Linux use?

---

### Post by billgoldberg on 2008-03-20
You can try these:

[http://damnsmalllinux.org/](http://damnsmalllinux.org/)

[http://www.puppylinux.org/user/index.php](http://www.puppylinux.org/user/index.php) (their site seems to be down at the moment (mysql error))

---

### Post by (HRl5 on 2008-03-20
I'm pretty new to Linux but here's my experience so far, I hope it helps:
I have installed Ubuntu 7.10 on two PC's. 
1-Dell 2.5 ghx Celeron, 512 GB RAM, Nvidia 5500 (although, I've had trouble getting this card to work).
2- 3.0 Ghz AMD Athlon 62 X@ 2 6000, 2GB RAM, Nvidia 8600 GTS OC

Both machines run great. The Dell even runs Beryl and Compiz-Fusion smoothly without the help of the video card! If I were you, I'd stick with Ubuntu, but upgrade the RAM. RAM is very cheap now-a-days. 
Just my two cents....

---

### Post by wolfen69 on 2008-03-20
i have installed xubuntu feisty alternate cd on a pc with 256ram, and it was pretty quick. you might try that.

---

### Post by (HRl5 on 2008-03-20
> **billgoldberg said:**
> You can try these:

[http://damnsmalllinux.org/](http://damnsmalllinux.org/)

[http://www.puppylinux.org/user/index.php](http://www.puppylinux.org/user/index.php) (their site seems to be down at the moment (mysql error))

I hear that you can run Puppy on a USB flash stick!

---

### Post by handydan918 on 2008-03-20
Xubuntu is about the lightest *buntu there is. If you can't cough up for a little more ram (another 128- 256 would make a noticeable difference) then maybe you should consider running a different distro. 
I've used [this one]("http://antix.mepis.org/index.php/Main_Page#Mirrors.2FDownload") on a PII with less than 100 MB of ram...

---

### Post by ad_267 on 2008-03-20
Also have a look at this:
[http://gentoo-wiki.com/Linux_Memory_Management](http://gentoo-wiki.com/Linux_Memory_Management)

You're probably not using as much RAM as you think

---

### Post by N1N31NCHN41L5 on 2008-03-20
oh but it really is using that much - here we go:

josh@xubuntu:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           248        245          3          0          0         29
-/+ buffers/cache:        215         32
Swap:          729        240        488

---

