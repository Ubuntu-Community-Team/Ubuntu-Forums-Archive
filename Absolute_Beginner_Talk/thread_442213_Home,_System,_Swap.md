---
title: "Home, System, Swap"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by JMV290 on 2007-05-13
Right now I don't feel like creating a new partition.   I will use Wubi for now(until I get around until get creating a partition)


[IMG]http://www.cutlersoftware.com/ubuntusetup/wubi/en-US/screenshots/wubi-advanced.jpg[/IMG] 



What do each of those do?



System, Home, and Swap?



I'm sure system files is all of the files required to run the OS.  What about the other 2?

---

### Post by oilchangeguy on 2007-05-13
are you trying to set up a dual boot on a computer with a 4gb hard drive???????

---

### Post by JMV290 on 2007-05-13
> **oilchangeguy said:**
> are you trying to set up a dual boot on a computer with a 4gb hard drive???????

No, that's a screenshot from Wubi's website.


I have a 55 GB harddrive with 33 GB free.

---

### Post by mikewhatever on 2007-05-13
Home contains you personal files and settings, as well as programs you install.
System is probably the same as root. It contains the OS.
Swap is similar to the page.sys in Windows. It extends you RAM and is normally about 1.5-2 times the size of RAM.

After you are done, can you tell us how it went. I am interested to hear if that wubi thing works or not. thanks.

---

### Post by freebird54 on 2007-05-13
Give it 8 Gb for system (root, we hope)
Give it 1 Gb for swap - should be lots
Give it the rest of what you want to commit to for /home - it gets most of the programs and settings.

Hope that helps :)

---

### Post by JMV290 on 2007-05-13
> **mikewhatever said:**
> Home contains you personal files and settings, as well as programs you install.
System is probably the same as root. It contains the OS.
Swap is similar to the page.sys in Windows. It extends you RAM and is normally about 1.5-2 times the size of RAM.

After you are done, can you tell us how it went. I am interested to hear if that wubi thing works or not. thanks.

Okay thanks.

What are some suggested sizes I use for each one?



I want to screw around with Beryl or Compiz.  

Are the programs included with Ubuntu included in the "system" or home?   


I don't want to go over 10gigs(not until I get a new harddive)

---

### Post by JMV290 on 2007-05-13
> **freebird54 said:**
> Give it 8 Gb for system (root, we hope)
Give it 1 Gb for swap - should be lots
Give it the rest of what you want to commit to for /home - it gets most of the programs and settings.

Hope that helps :)

1gig swap? Everyone else has been saying 500mb is more than enough.  Do you really think I should go with 1 gig?

---

### Post by oilchangeguy on 2007-05-13
> **JMV290 said:**
> 1gig swap? Everyone else has been saying 500mb is more than enough.  Do you really think I should go with 1 gig?
500mb is plenty. if you've got a computer that has to use swap/virtual memory, you've got a computer with problems.

---

### Post by Wiebelhaus on 2007-05-13
a buddy of mine wanted to try wubi , only thing i saw that was cool is if you are committed to windows it will add ubuntu to windows boot loader , I personally would rather let a boot loader i know is capable handle my OS's..


Aka.....GRUB.

Would be nice to see a GUI version plugged into Ubuntu such as OPENSuse has..

---

### Post by Rab22 on 2007-05-13
> **JMV290 said:**
> Right now I don't feel like creating a new partition.   I will use Wubi for now(until I get around until get creating a partition)


[IMG]http://www.cutlersoftware.com/ubuntusetup/wubi/en-US/screenshots/wubi-advanced.jpg[/IMG] 



What do each of those do?



System, Home, and Swap?



I'm sure system files is all of the files required to run the OS.  What about the other 2?

With Linux, it's common to set up the operating system using multiple partitions.  

Back in the old days you would create a '/' (root/System), '/boot' (what boots the OS), and 'swap' (holding area). People made the boot partition to get around the 1024 cylinder block problem with the boot manager (LILO). And the SWAP partition greatly increased system performance. Additionally, many experienced Linux users would create a '/home' partition as well to hold their personal data.

Today, the need for a '/boot' partition is pretty much gone.  In fact, you could simply create a '/' and be fine if you have a large amount of system memory.  Nevertheless, it is still a good idea, and often heavily recommended, that you create a 'swap' partition and a '/home'  partition. 

Personally, I use a '/home' partition so that I can reinstall Ubuntu or another linux distro and when I boot up, it appears like nothing has changed =)

---

### Post by freebird54 on 2007-05-13
With the size and cost of hard drives these days, while 512 might be plenty (and probably will be) using a 1Gb swap will mean you never have to think about it again.  If you ever gety to the point where it isn't enough - it is time for a total rethink of what you're trying to do!

People are alway saying 1.5 times RAM or 2 times RAM - and I have 512 -so I went with 1 Gb - and no problems (it doesn't even hit the swap very often unless I'm getting carried away with Gimping)

---

