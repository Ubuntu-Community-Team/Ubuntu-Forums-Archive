---
title: "Installing XP on a separate HDD"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by BarFly on 2006-07-16
Ok, I thought it would be as easy as swapping out my HDD that is configured for Linux with a small one with NTFS and booting with the recovery disk (don't have a real install disk, just the Gateway crap recovery version).  Just to be safe, I disconnected my Linux HDD and put the new drive on the first position of the cable.  I thought Win would install, but I got this:
> STOP: c0000221 Unknown Hard Error\System32\ntdll.dll

I downloaded ntdll.dll on my Ubuntu HDD from [http://www.dll-files.com/](http://www.dll-files.com/) , but haven't done anything with it yet, and do not know what to do with it.  Do I boot with my working HDD (Ubuntu) as master and the NTFS drive as slave?  But how would I transfer from ext. 3 to NTFS?  Do I have to make the new, Win drive FAT32 first, and then convert to NTFS?

I know that Windows likes to be first, so I thought I would swap the "new," smaller HDD on the string with the Linux HDD and switch the main one to slave.  However, I cannot get Windows to install from a CD.  I figured I would research on how to install GRUB onto the Win HDD and have it work after I got Win working.  That is another problem I might encounter.

I know, I should have kept my XP install while installing Ubuntu, but I did not.  Yes, I am only somewhat computer savvy (meaning more than most people).  I cannot simply start anew as I have no place to dump all of my files.  Plus, I do not know how to reinstall Win!

There has to be a "slap me in the face answer" to this!

Thanks.

---

### Post by jason.b.c on 2006-07-16
> **BarFly said:**
> Ok, I thought it would be as easy as swapping out my HDD that is configured for Linux with a small one with NTFS and booting with the recovery disk (don't have a real install disk, just the Gateway crap recovery version).  Just to be safe, I disconnected my Linux HDD and put the new drive on the first position of the cable.  I thought Win would install, but I got this:


 > Do I boot with my working HDD (Ubuntu) as master and the NTFS drive as slave? 
Yes..:-D 

> I know that Windows likes to be first, 

No thats wrong..!   Ubuntu likes to be first..:D    Master hdd ( ubuntu ) , Slave hdd ( windows )

> I know, I should have kept my XP install while installing Ubuntu, but I did not.  Yes, I am only somewhat computer savvy (meaning more than most people).  I cannot simply start anew as I have no place to dump all of my files.  Plus, I do not know how to reinstall Win!

There has to be a "slap me in the face answer" to this!

Thanks.

So you don't have **any** windows installed at all..?? on either/any hard drive..???   Uh-Oh..!!  And you don't have an install disk.?  ](*,)

---

### Post by jason.b.c on 2006-07-16
> I figured I would research on how to install GRUB onto the Win HDD and have it work after I got Win working. That is another problem I might encounter.

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

[http://ubuntuforums.org/showthread.php?t=159384](http://ubuntuforums.org/showthread.php?t=159384)

[http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html)

[http://ubuntuforums.org/showthread.php?t=124989](http://ubuntuforums.org/showthread.php?t=124989)

[https://help.ubuntu.com/community/CategoryDocumentation](https://help.ubuntu.com/community/CategoryDocumentation)

Grub installs on to the master ( ubuntu ) hdd...:D    If i'm not mistaken..:confused:

---

### Post by BarFly on 2006-07-16
I only have the Gateway recovery disk which has XP Home on it.  Whenever I insert it, it is looking for Windows DLL's as mentioned above.  If need be, I can get a bootleg copy of XP (should not be a problem as I have a license for a legit. copy, but, a hassle, and illegal).

I would rather not go the shady route, though.  If this helps, I reformatted the small disk I want to use using GPart.  I guess my first step is figuring out how to install the DLL's onto the new HDD to accept a reinstall of XP from CD.

Okay, let me put the "new" drive as slave and the Ubuntu drive as master and let me see if it recognizes it.  Don't wait up!

Thanks for your help.

---

### Post by jason.b.c on 2006-07-16
> I guess my first step is figuring out how to install the DLL's onto the new HDD to accept a reinstall of XP from CD.


They would be on the windows install CD..Don't worry...:D

---

### Post by catlett on 2006-07-16
> **BarFly said:**
> I only have the Gateway recovery disk which has XP Home on it.  Whenever I insert it, it is looking for Windows DLL's as mentioned above.  If need be, I can get a bootleg copy of XP (should not be a problem as I have a license for a legit. copy, but, a hassle, and illegal).

I would rather not go the shady route, though.  If this helps, I reformatted the small disk I want to use using GPart.  I guess my first step is figuring out how to install the DLL's onto the new HDD to accept a reinstall of XP from CD.

Okay, let me put the "new" drive as slave and the Ubuntu drive as master and let me see if it recognizes it.  Don't wait up!

Thanks for your help.I think it is a bigger issue than that.
This thread mentions 2 things it can be but they are not definates. [http://www.qdigrp.com/qdisite/bbs_eng/showtopic.asp?TOPIC_ID=23947&Forum_ID=1](http://www.qdigrp.com/qdisite/bbs_eng/showtopic.asp?TOPIC_ID=23947&Forum_ID=1)

---

