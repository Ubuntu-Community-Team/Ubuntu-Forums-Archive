---
title: "pls help me"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by arai on 2006-12-16
is there a way to delete the linux partitions and the boot loader which asks me linux or winxp.

i want to delete the linux partitions and use the drives for windows. i also do not want the booter to ask winxp or linux. instead i want the booter to load winxp automatically.

pls help me.


thanx a lot.

---

### Post by xyz on 2006-12-16
I like:
[GParted]("http://gparted.sourceforge.net/livecd.php")
Download it - Burn the .iso - Boot on it - Get_rid_of_whatever_you_want
Good luck. Too bad you're leaving...

---

### Post by Regel on 2006-12-16
> is there a way to delete the linux partitions and the boot loader which asks me linux or winxp.Yes.
Use XP-CD and it's recovery console: fixmbr, then reboot and use XP's partitioning tool to get rid of Linux-partitions.

---

### Post by xpod on 2006-12-16
You can go into you "disk management" in xp and quite easily delete the Linux partitions..

And then you can use your xp cd to "fixmbr" or if you dont have one of those you could use a 98 bootdisk with "fdisk.exe" on it and run "fdisk /mbr"

Or of course you can use stuff like the gparted cd etc etc

---

### Post by arai on 2006-12-16
xyz is that Gparted used in windows ? i don't have access to linux. it somehow got corrupted. and i can access only winxp now.

regel can you tell it more clearly. i have the winxp cd. but how to use the recovery console? and when and where shoould i type fixmbr.

thanx.

---

### Post by arai on 2006-12-16
xpod how to go to "disk management" in winxp. i use classic interface in winxp.

thanx.

---

### Post by xyz on 2006-12-16
Hi,
> xyz is that Gparted used in windows ? i don't have access to linux. it somehow got corrupted. and i can access only winxp now.
Gparted needs no operational OS. You download it, burn it, then stick it in your cd-rom and press on the power on buttom of your computer.
The other solutions are quite good too.
Let me know...

---

### Post by xpod on 2006-12-16
[http://www.theeldergeek.com/disk_management.htm](http://www.theeldergeek.com/disk_management.htm)

That might help:D

EDIT:...good site for all your installing and un-installing requirements
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by LDRoamer on 2006-12-16
Some information on windows recovery console here:

[http://support.microsoft.com/kb/314058](http://support.microsoft.com/kb/314058)

> **xyz said:**
> Hi,

Gparted needs no operational OS. You download it, burn it, then stick it in your cd-rom and press on the power on buttom of your computer.
The other solutions are quite good too.
Let me know...

---

### Post by arai on 2006-12-16
I want to install Ubuntu 5.10 now. Is there anybody using it now? I cannot download new version as I have slow internet and also i cannot order free cds as i am moving to a new place. so if i install ubuntu 5.10 can i install additional softwares? is there anybody who knows ubuntu 5.10 who would help.

---

### Post by xpod on 2006-12-16
> i want to delete the linux partitions and use the drives for windows. i also do not want the booter to ask winxp or linux. instead i want the booter to load

[-( 

> I want to install Ubuntu 5.10 now. Is there anybody using it now? I cannot download new version as I have slow internet and also i cannot order free cds as i am moving to a new place. so if i install ubuntu 5.10 can i install additional softwares? is there anybody who knows ubuntu 5.10 who would help.

:mrgreen: 

You`ve lost me a bit though:-k 
What did you delete in the first place??

If you want to now install Ubuntu then would`nt Dapper be the best bet??or even Edgy??
Mabey you could list all your hardware and how to would like to set Ubuntu up and people more knowlagable than me can guide you through things a bit easier??

This is a great site for your dualbooting needs if thats what your after
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

And this is just a great site all round for grasping the basics
[http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)

Glad you came to your senses;) .........

EDIT...sorry,just read your post properly....doh
EDIT2...dont suppose your in the uk?....your best bet is getting a Dapper cd off someone or getting a shot of someones broadband me thinks.

---

### Post by pmasiar on 2006-12-16
Ubuntu LiveCD has Gparted - partition manager. You can start it and reformat any partitions to ntfs.

When you have time and feel you are ready to learn something new and fully understand how your PC works (and works for *you* not for musical industry lawyers), you can come back to Linux again. In the meantime, we will work on it to be even easier and more fun to use. :-)

---

### Post by xyz on 2006-12-17
> **pmasiar said:**
> Ubuntu LiveCD has Gparted - partition manager. You can start it and reformat any partitions to ntfs.

When you have time and feel you are ready to learn something new and fully understand how your PC works (and works for *you* not for musical industry lawyers), you can come back to Linux again. In the meantime, we will work on it to be even easier and more fun to use. :-)
May I ask what "musical industry lawyers" have to do with this?

---

### Post by chrisfay on 2006-12-17
> May I ask what "musical industry lawyers" have to do with this?

:-k   .....I second that

---

