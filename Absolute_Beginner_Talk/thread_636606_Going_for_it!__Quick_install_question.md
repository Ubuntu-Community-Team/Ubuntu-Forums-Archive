---
title: "Going for it!  Quick install question"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by Satummoo on 2007-12-10
I decided on making a 20gig partition space on my harddrive to learn how to use ubuntu/linux.  I tried using it before but I need a lot more time learning everything about it and previously gave up.  Now I have my x64 edition and when I went to go to install, it gave me the slider opetion of how much space I wanted to use.  When I installed ubuntu 7.04, I was able to move the slider all the way from 2-250 (size of my HD).  However, the minimum it will let me do is 100gigs which is more then the amount of free space I have.  Currently I have XPx64 and don't want it erasing or messing with my current partition.  All I want to do is have a 20 gig partition.  Do I go manually and enter a number?  And is 20,000mb the same as 20gigs?

I know this sounds stupid but I just want to make sure before I really screw something up

---

### Post by mikewhatever on 2007-12-10
Hi, I really don't know why the minimum you get is 100 GB, never used that particular option. A good way around would be to use gparted live cd to resize and partition. 1 BG = 1024 MB.

---

### Post by FuturePilot on 2007-12-10
> **mikewhatever said:**
> Hi, I really don't know why the minimum you get is 100 GB, never used that particular option. A good way around would be to use gparted live cd to resize and partition. 1 BG = 1024 MB.

Yeah, that's what I would do. You could even do it from the live CD if you wanted to. It's under System>Administration>Partition Editor. Just scoot your Windows partition over so that you have about a 20GB partition at the end. Don't format anything though. Run the installer and when it comes to the partitioning part tell it to use the "Largest Continuous Free Space" and it will install onto the 20GB partition.

---

### Post by Sef on 2007-12-10
> However, the minimum it will let me do is 100gigs which is more then the amount of free space I have.

I wold say you have a bad disk.  Redownload, and reburn.

---

### Post by hyper_ch on 2007-12-10
if you are on VISTA, use the VISTA partitioning tool to create unpartitioned space (and before you do that, don't forget to defragment your drive 2-3 times).

---

### Post by CatKiller on 2007-12-10
> **Satummoo said:**
> However, the minimum it will let me do is 100gigs which is more then the amount of free space I have.

How much space has Windows used? It's possible that you're reading the slider the wrong way, and that's as small as it can make your existing partition.

---

### Post by Satummoo on 2007-12-10
> **CatKiller said:**
> How much space has Windows used? It's possible that you're reading the slider the wrong way, and that's as small as it can make your existing partition.

Just an update, I did read the slider wrong but had hell installing.  I burned ubuntu on a DVD and burned it 16x and had countless errors installing.  I then couldn't boot into windowsxp64 and ended up re-installing windows (still had all my data)

Now i'm going to try burning it on a CD at 4x and hopefully it will work.

---

### Post by Sef on 2007-12-10
> Now i'm going to try burning it on a CD at 4x and hopefully it will work.

Burning faster than 4x can corrupt the download, so that should take care of your problem.

---

