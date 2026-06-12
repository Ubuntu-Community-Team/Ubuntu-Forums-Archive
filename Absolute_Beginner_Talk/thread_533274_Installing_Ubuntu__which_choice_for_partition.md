---
title: "Installing Ubuntu : which choice for partition?"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by sdim on 2007-08-23
Dear friends,
newbie on the block,and literally,indeed,I've been using Ubuntu for 10 days now.
Earlier today,while in Ubuntu,something happened and I lost the APPLICATIONS drop-down menu,meaning that I couldn't open it at all.I tried various things and advice,but nothing worked,so here I am,re-installing the whole thing.
There is an important question:
When installing,after the first general questions,we come to the point of deciding where to install the OS.
Well,the thing is I have a hard disc of 120 GB,and when installing WinXP some hours ago,I formatted 70 GB as NTFS(WinXP),and left almost 40 GB of space unformatted (free) so that I could re-install Ubuntu later.

**Which of the three choices is for me?**
1)_I suppose not the first one (install on the whole disc)._
2)_Should I choose resizing the HD (second choice)? _     
3)_Should I do it manually (third choice)? _

I could really use the experts' knowledge on this one.
Also,the more details you can provide,the better for a rookie Ubuntu user... 

Thank you in advance.

---

### Post by kidcharles on 2007-08-23
Doesn't it give an option to install on the free space remaining on the drive? Otherwise from those options I'd go with the manual route, we'll help you with that.

---

### Post by wolfen69 on 2007-08-23
manual would be the way to go.

---

### Post by bjarneh on 2007-08-23
3) manually 

use the free space, create two partitions on it atleast (one for / ie. root file system), and 
one for swap, if you wan't to go fancy


15 Gb - /
1 Gb - swap (no mount point)
24 Gb - /home

then if everything screwes up agian, you don't have to loose all your own documents since /home is a seperate partition, it's always nice to mount you old home on a new install anyways to keep your old configurations and settings...

---

### Post by pgar23 on 2007-08-23
GO TO MY SIG...EXPLAINS ALL!!!

  |
  |
  |
  v

---

### Post by nitro_n2o on 2007-08-23
giving you a plain answer on such a topic wont be as helpful as you wish... 
so i'd say have a look at this [http://www.traduc.org/docs/guides/lecture/Linux-Filesystem-Hierarchy/html/](http://www.traduc.org/docs/guides/lecture/Linux-Filesystem-Hierarchy/html/)
and [http://tldp.org/HOWTO/Partition/index.html](http://tldp.org/HOWTO/Partition/index.html) 
You can always find great info in the linux documentation project (TLDP) [http://tldp.org](http://tldp.org) 
have fun

---

### Post by sdim on 2007-08-24
Thank you all for the answers.I'll try it and hope I manage (as I did the first time,not really knowing the procedure).So I guess I don't have to format the free space of the disc as NTFS.

---

