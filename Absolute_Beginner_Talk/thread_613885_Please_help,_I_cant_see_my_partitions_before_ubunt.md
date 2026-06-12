---
title: "Please help, I cant see my partitions before ubuntu installation"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by ale2283 on 2007-11-15
Hi,  im a new user, please I need some help
I tried to install ubuntu dual boot in a couple ways but none of them worked for me 

I have a DELL XPS 600
Chipset 	nVIDIA nForce4 SLI X16 Intel Edition
Pentium dual core 830  3ghz
2048 MB  (DDR2-667 DDR2 SDRAM)
Graphic  card 	NVIDIA GeForce 6800  (256 MB)
Hard drive 	NVIDIA  STRIPE   298.02G  (298 GB)  Raid 0   (2  x 160 gb drives )

This is the problem :

I used live cd to install ubuntu, on the screen where I have to decide the partition I want to use just appears the  2  160 gb hard drives  (I have a  70 gb unallocated partition that I made with partition magic).

I tried different types of partitions as the ubuntu manual indicates but none of them appear on the installation screen.  

Also I tried to install it with [COLOR="Red"]WUBI[/COLOR] but after the installation, when I restart the pc and choose ubuntu it appears a black screen that says :  [COLOR="Red"]CANT ACCES TTY; JOB CONTROL TURNED OFF.[/COLOR]
Please if someone can help me, I really want to install ubunu without erasing windows.

---

### Post by Inxsible on 2007-11-15
you can choose manual adn then partition the drive yourself in GParted

Here's a great link to help you dual boot. Its illustrated, so you can't go wrong :)

[www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing")

---

### Post by ale2283 on 2007-11-16
Ok thanks for your help, but how do i know in which disk is windos installed if i have a raid 0 with 298 gb and in ubuntu installation appears the 2 160 gb disks, if i pick one of the 2 disks to install ubuntu i will probably demage windows.
i think that if u have a raid it just puts the information or the programs that you install randomly anywere on the disks.

---

### Post by Ruuud on 2007-11-18
I can answer part of your question, even though I have not yet set up my very first Linux installation yet (working on that). The reason you see two disks is because by itself linux/ubuntu does not understand the raid configuration you have because (as it appears to me) you have a software raid chipset. So Linux simply sees the hardware and reports to you that you have two hard drives (which you do). You need to install dmraid (search for it on this website) to see the partitions that you already have!

Raid 0 means that the drives work together by each storing half of the data of a file, frst disk a stores a piece, then disk b, then disk a gain and so on, this is called striping. So if you install linux without dmraid just on one disk you will overwrite half of the files you had and windows will most definately not work anymore (there are even more reasons why this would be bad, but the one I named is very obvious...

---

### Post by Pumalite on 2007-11-18
Be aware of this:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by ale2283 on 2007-11-18
ok thanks goys for your help i found on the forum that to install dmraid i have to do this 
Install dmraid

    *

      Boot the Ubuntu CD and select Start or Install Ubuntu
    *

      Go to System > Administration > Software Sources and add the universe software repository.
    *

      Go to System > Administration > Synaptic Package Manager and install the dmraid package.
    *

      Go to Applications > Accessories > Terminal and run

the thing is i cant find dmraid this way, it doestn find the package i tried to to intall it with the terminal and it dosnt work.
If any one knows how to install dmraid it will be very helpful

---

