---
title: "How do I do this"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by playme123 on 2007-07-08
Right currently have ubuntu installed on my main pc in a partition on my hard drive, and use it no problems.
Now here comes what I want to do.
My dad had a packard bell 552 tower which he has absolutely buggerred up ie ntldr is missing comes up on the screen when its started up.  The pc did not come with recovery disks as you have to go into a partition in the hard drive and then make them yourself.
Right this is what I want to do
I want to load ubuntu on to this hard drive and leave the recovery partition in tack but wipe everything else of the hard drive and install ubuntu on the remainder.
How do I do this, what file system does ubuntu use ie ntfs or fat 32, whats the easiest way to make a bootable ubuntu disk.
Basically want to use this tower as a media based pc as this will be linked up to a lcd tv
It did have win xp media centre on it until me dad buggered it up

---

### Post by playme123 on 2007-07-08
anyone

---

### Post by koshari on 2007-07-08
boot the live cd and check what partitions are on the machine with grarted, 

post back the relevent info here, 

i would imagine you would simply be able to wipe all the partitions other than the recovery one on the computer and add the linux partitions in the resultant free space.

linux doesnt use neither fat32 or ntfs. your best bet is to make a swap partiion approx the size of your ram at the end of the drive and use the reast of the space to make a ext3 partion however there is a wizard in the install process that will let you do this,

btw its usually a good idea to put the content of your post in the thread title , then people who are knowledgable about the subject can see it and render assistance .

---

### Post by monkey707 on 2007-07-08
Go And JumpHere : [http://www.myfreegamespot.com/game/22303/Monkey-Jumps.html](http://www.myfreegamespot.com/game/22303/Monkey-Jumps.html)


lol,

sorry i dont know the answer !



:guitar:

---

### Post by playme123 on 2007-07-08
ok cheers

---

### Post by monkey707 on 2007-07-08
are you using two Operating systems in same pc ?

---

### Post by playme123 on 2007-07-08
In my current pc yes, in the one I want to put ubuntu onto it only has xp on it which is innaccesable due to the ntldr issue

---

### Post by bigken on 2007-07-08
use the gparted liveCD to see the partition table also if you can borrow a win xp disc you can fix the nt loader issue in recovery console


edit also your recovery partitions for winxp will proablys show as fat32

---

### Post by playme123 on 2007-07-08
yes the recovery partition does show up as fat 32, no one I know has the xp media edition cd, have tried an ordinary xp pro disc to try and recover it but after its formatted the pard of the hard drive that I want to put the xp on its restarts and then end up back at the begiing

---

### Post by bigken on 2007-07-08
if you reach the recovery console type chkdsk /p /r

---

### Post by playme123 on 2007-07-08
ok will try that will bookmark this page as reference thanks for all your help

---

### Post by playme123 on 2007-07-13
I couldnt be bothered in the end resolving the ntldr issue in windows, so installed ubuntu on it and everything is working fine, have resolved the issue of playing dvds and so forth just waiting for lcd tv to link it up to and Ill be firing along, loving ubuntu just have to learn a bit more.

---

