---
title: "can't resize hardrive partition in Ubuntu install or gparted"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by newb10 on 2007-12-04
im trying to dual boot with xp and ubuntu. but i cant resize my partition for the install. gparted says my drive is unmounted so that isnt the prob. But for some reason neither gparted or ubuntu install will let me resize my partition to make room for ubuntu. I defraged my hardrive 3 times ...so thats not the prob.

i have a 120gig hardrive and i erased some music and video files for room ubuntu..around 25 gig. I noticed that in gparted it doesnt say how much space is free on my windows partition? it just lists the size of the partition. no used space or anything like that.

thanks in advanced for any help.

---

### Post by crjackson on 2007-12-04
> **newb10 said:**
> im trying to dual boot with xp and ubuntu. but i cant resize my partition for the install. gparted says my drive is unmounted so that isnt the prob. But for some reason neither gparted or ubuntu install will let me resize my partition to make room for ubuntu. I defraged my hardrive 3 times ...so thats not the prob.
thanks in advanced for any help.

The windows defrag tool isn't all that great.  The fact that you ran it 3 times does not mean it has moved all the data to the front of the drive (where you want it) and consolidated the free space at the end.  I use a 3rd party defrag tool to get the job done.

Also you shoud run an offline file system check to ensure you have no errors on your current partition.  I've had this problem myself on more than one system.

Be sure you back up all your data before trying to edit the partition.

Usually what's happening is that you have a small fragment left near the end of the drive, or somewhere near the desired partition break.  You HAVE to get that data moved before gparted or ubuntu will allow a change.  It's for your own protection.

---

### Post by lgambett on 2007-12-04
Try also (very important !) chkdsk with error checking on the Windows machine.
Ciao,
Luca

---

### Post by forestpixie on 2007-12-04
in the past I've turned off the pagefile and degragged then - it always seemed to be the pagefile that caused my problems

---

### Post by r4wr on 2007-12-04
i am having the same problem. I have been trying to dual boot my brothers machine also XP/Ubuntu.  Is there any third party defrag program you could suggest to use. gonna try the chdsk here soon.

oh yea also. On his computer it shows his recovery partition and his window partition.Then there is 8MB just doing nothing not assigned any where. Is this normal for there to be just a little bit of floating space. its a 200 gig drive.

---

### Post by louieb on 2007-12-04
A couple of things you might find helpful.
[See the prep Win partition Section here]("http://www.linuxdevcenter.com/lpt/a/6554") 
[JKDefrag: A better windows defragmenter.]("http://kessels.com/JkDefrag/index.html") I use this,  never had a problem.

---

### Post by Paqman on 2007-12-04
[Auslogics Disk Defrag](http://www.auslogics.com/disk-defrag/) is really good, too.

---

### Post by newb10 on 2007-12-04
> **r4wr said:**
> i am having the same problem. I have been trying to dual boot my brothers machine also XP/Ubuntu.  Is there any third party defrag program you could suggest to use. gonna try the chdsk here soon.

oh yea also. On his computer it shows his recovery partition and his window partition.Then there is 8MB just doing nothing not assigned any where. Is this normal for there to be just a little bit of floating space. its a 200 gig drive.

i have that same thing with the "8mb". if you get passed the problem post back and let me know. we probably have the same problem.

everyone-Thanks for the advice. I was running diskeeper for defrag. I'll try a different defrag program and everything else thats been recommended.

---

### Post by crjackson on 2007-12-04
> **newb10 said:**
> i have that same thing with the "8mb". if you get passed the problem post back and let me know. we probably have the same problem.

everyone-Thanks for the advice. I was running diskeeper for defrag. I'll try a different defrag program and everything else thats been recommended.

The 8MB thing is normal.  Leave it alone.

---

