---
title: "Intell 4965 wireless help"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by wissemeier05 on 2008-03-02
Newbie intro: I am a complete Newbie to Ubuntu and I have had exactly 1 week of experience with fiesty Ubuntu before upgraded to Gutsey.  The reason I upgraded to gutsy was that I read that the Intell wireless card work seamlessly with the upgraded version.  (cant find the link now).  

Hardware:
Sager 5793 (set up for XP)
Intel wireless 4905AGN

I am running:
Ubuntu
7.10 (gutsey)
Kernel Linux 2.6.22-14-386
GNOME 2.20.1
-and still have XP running on a partition of the hard drive


I have the wired connection working, i blacklisted the ipv6.  what do I need to do to get my wireless working?


Thanks in Advance
Dan

---

### Post by anewguy on 2008-03-02
Do you have either a disk with the Windows drivers on it or can you download them?

---

### Post by Josh1 on 2008-03-02
I also have Intel for WiFi, and with 7.10 they worked out of the box.
Have you checked out: [http://intellinuxwireless.org/](http://intellinuxwireless.org/) ?

---

### Post by anewguy on 2008-03-02
I think you may also need to just enable the restricted drivers.

---

### Post by wissemeier05 on 2008-03-03
Yes i do have a CD with the drivers on it for XP

> **Josh1 said:**
> I also have Intel for WiFi, and with 7.10 they worked out of the box.
Have you checked out: [http://intellinuxwireless.org/](http://intellinuxwireless.org/) ?

-honestly i get lost on that page i do not know what to do.  i tried to compile the mac20811  and i must be doing something wrong case i get a bunch of errors..


-it does not appear on my restricted drivers list, My graphics card was on the list and i enabled it and it works fine now





:edit:
-is there a way to nuke ubuntu, and reinstall it and see if it will find  the wireless card?

---

### Post by OhioYJ on 2008-03-03
Yeah, you might try and download the 7.10 and install it just as you did before with the 7.04 disc I sent you. Just delete the current Linux partitions and create new ones, like we did before.

Perhaps that is the issue. Download the 7.10 ISO in Ubuntu, you can't mess up burning ISOs in Ubuntu.

---

### Post by wissemeier05 on 2008-03-05
I installed Ubuntu 7.10 and it all works!!

only problems i now have:
-bluetooth is not connecting i have the icon i can see my devices but it will not connect
-power management on the wireless card needs to be adjusted any time i get bellow 50% my wireless drops..allot...i have been searching for a power management feature but i can't seem to locate one..

-I am having trouble installing AutoMatix "Dependency is not satisfiable: tango-icon-theme-common"

~any ideas? 

other than that this is working great!!

---

### Post by wissemeier05 on 2008-03-05
I followed the steps in this post [here]("http://ubuntuforums.org/showthread.php?t=596850") so i do not need automatix any more :D

---

