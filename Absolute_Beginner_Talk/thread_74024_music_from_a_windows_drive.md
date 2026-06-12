---
title: "music from a windows drive"
date: 2005-10-10
forum: Absolute Beginner Talk
---

### Post by jeriziosantos on 2005-10-10
how can i get my music from my c drive (running windows xp) to load on my unbutu drive? windows cannot see the drive and unbutu cannot see the windows drive.

any ideas?

---

### Post by Eldon on 2005-10-10
> windows cannot see the drive
What drive can't windows see, its own c: drive?  I take it you have one hard drive in your system, its got both windows and linux dual booting, and linux can't read the windows partition?
Go into windows, right click the c: drive, choose properties and find out what type of file system is being used, it should be Fat32 or NTFS, then you'll need to do one of these:
[http://ubuntuguide.org/#windows]("http://ubuntuguide.org/#windows")

---

### Post by jeriziosantos on 2005-10-11
i am rinning 2 harddrives, an 80 gig c drive for windows and a 6 gig one for ubuntu, the 6 gig was formatted and partition as part of the install process, i shall have a look at the link

---

### Post by jaysanghera on 2005-10-12
SORRY IF I AM POSTING A REPLY THAT TAKES THIS ON A TANGENT, I AM ASSUMING THE SOLUTION IS SAME TO THE ABOVE REQUEST

i have essentially the same situation
I am dual-botting with 2 hard drives

C:\ NTFS file system with windows

D:\ Ubuntu

So i boot up this morning, select windows as my operating system and get an error that is along the lines of

"cannot find C:\windows\system"
"Insert Windows XP CD and repair"

so i try that, and it doesn't work
anyways, the point is, MY TRUSTY UBUNTU drive is working perfectly fine (go ubuntu go). I want to copy over music & documents to my Ubuntu drive from my windows drive, but yah, i am not entirely sure how this relates to the concept of "mounting" and so forth.

thanks in advance for any help :)

---

### Post by casper_2095 on 2005-10-13
[http://ubuntuguide.org/#mountunmountntfs](http://ubuntuguide.org/#mountunmountntfs)

---

### Post by jaysanghera on 2005-10-14
hah, thanks (sorry for even bothering to ask that question)

One more general question, it seems to be very slow when trying to read from the windows drive, why? Shouldn't it be fairly quick?

---

