---
title: "Help need in installation"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by vboyz on 2006-12-02
i am now running my PC with windows XP sp3.i have 40Gb hard disk.It has now three parts,one is 7.5Gb,12.5Gb,16.7Gb.It has AMD Athlon(tm)XP 1.25 GHz processor and 384 MB ram.And also i install PowerQuest PartitionMagic 8.0 software in my PC

I got ubuntu CD and run it users live mode.I like ubuntu very much in that mode.And i tried to install ubuntu unfortunaitly i lost my all Datas in hard disk.I wish to install both ubuntu and XP in my system.Please give me the good advice how i can do that.And also need the OS selestion menu at the time of booting.Please help me any one.
Thanx in advance

---

### Post by smile_sunshine on 2006-12-02
Hi,

probably easiest is to install windows first then follow instructions [here]("http://psychocats.net/ubuntu/installing") to install ubuntu. 
When installing ubuntu it should automatically set up the grub boot loader which will give you the choice of what OS you want to run when you start the computer 

hope that helps, 
if you have more questions or get stuck just ask here, its a very friendly forum :)

---

### Post by CaveRat on 2006-12-02
Sunshine is right on. Split the 40gigs in half. 20 for Windows and leave the other half alone. Install Windows to your liking, then toss in the Ubuntu Live CD. I set up a friends 40 gig this way. The remaining space will be used for Linux. 10 to 15 gig for / root, twice your Ram total for Swap, and the rest for Home. Creating a seperate partition for Home will allow you to save any downloaded stuff there. If you mess up your Linux and have to reinstall, you can simply reformat / root and leave Home be. It's the same as creating a separate Storage partition D: in Windows. You can reformat C: and D: will stay intact.

---

### Post by Sef on 2006-12-02
Read the [Illustrated Dual Boot]("http://www.users.bigpond.net.au/hermanzone/").

---

