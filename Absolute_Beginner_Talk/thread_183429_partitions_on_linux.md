---
title: "partitions on linux"
date: 2006-05-28
forum: Absolute Beginner Talk
---

### Post by baalthazar on 2006-05-28
wasaaaa dudesss??!!

ive been wanting to install ubuntu on my pc cuz it seems a bit interesting and since i am studing informatics its almost a requirement to learn all i can from a pc...

anyways.. ive been looking through google on how to dualboot win xp and ubuntu.. and found out that to do that u need to partition the disk drives... is that really necesary? cant u install ubuntu in the same C: drive that winxp?

there is something else that made me think for a while, and is the fact that u have to partition a disk and that partitioned disk u have to split it up 3 times so one is for the system, the other for root and the other for i forgot... so that means u can install all things and have everything in one same DD like windows that u can install all programs and have files stored next to the OSWINXP?
can u see the files of the linux system while logged in the XP? 

i also have this idea for my setup... i have 2 DD, a sata of 250 gigs and an ide of 10gigs... i would like to install on the sata winxp and linux and another copy of winxp in the ide of ten gigs, so then, when i try stuff on the winxp of ten gigs and kill the system for some reason, i could still run winxp on the other drive... im sure thats posible.. but id like to hear some thoughts about this so i could be aware of maybe killing the sata along with the system on the IDE

---

### Post by Strangerdave on 2006-05-28
Well from what I gather, for the most part the answer to your questions is yes.  Let me explain.  

You can have two OS on one drive, but you need to make space for them, hence the partitioning.  If you install a linux flavor, such as ubuntu, you will install what is known as GRUB, which allows you to choose which OS you want to boot into.

You can have windows see the linux OS if the partition is Fat32 (I think), if you format the drive as NTFS, there may be a problem (although I am not exactly sure at this point - I know that if you have two drives and format them as Fat32 you can read/write with little problem, but if you format NTFS one and Fat32 the other, then you will run into trouble).

As for your two drive system, that is what I have and it works great!  [Here]("http://https://wiki.ubuntu.com/WindowsDualBootHowTo?highlight=%28how%29%7C%28to%29%7C%28dual%29%7C%28boot%29") is a page that will help you out with a dual boot system.

Hope that helps,

-SD-

---

### Post by halfvolle melk on 2006-05-28
[QUOTE=baalthazar]wasaaaa dudesss??!![/QUOTE]
Wazzaaaaaaaaaaa!

> is that really necesary? cant u install ubuntu in the same C: drive that winxp?
Not really, you won't need Windows afterwards anyway :p

Here's some good info on seting up dual booting.
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by RRS on 2006-05-28
To install Ubuntu with dual boot capability follow these guides:

[URL="http://users.bigpond.net.au/hermanzone/index.htm"]http://users.bigpond.net.au/hermanzone/index.htm
[/URL]
[http://www.psychocats.net/ubuntu/windowstoubuntu.html]("http://www.psychocats.net/ubuntu/windowstoubuntu.html")

As for your plans to run an additional Windows system I'm sure it's possible but can't help with the how, possibly a windows oriented forum such as PC Mechanic has something.

---

### Post by aysiu on 2006-05-28
Read this:
[http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)

---

