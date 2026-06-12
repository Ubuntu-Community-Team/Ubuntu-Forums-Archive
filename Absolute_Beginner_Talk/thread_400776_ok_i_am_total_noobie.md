---
title: "ok i am total noobie"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by metzy85 on 2007-04-03
ok so i am total noobie and i want to know how to install linux along with running xp
 
i have a dell inspiron b130 512 ram and 1.8ghz processor i am not very computer oriented i am running linux right now off disk but sometimes there is a bit of delay rather put it on hear and run two os please help i would much apreciate it

---

### Post by kidders on 2007-04-03
Hi there and welcome,

Is there a particular aspect of the installation you're having trouble with?

---

### Post by freebird54 on 2007-04-03
OK - and welcome.  I think we can give you better answers with a little more information.  What kind of system do you have now?  Type / memory / size of hard drive / type of graphic card are all factors in how best to proceed!  Anything else you can tell - such as how you want to use the sytem can also make a difference..

Again- welcome to Ubuntu!

---

### Post by metzy85 on 2007-04-03
first off i love the look and feel of linux  and i have used it for hour now 

i have it running of disk and i want to know how to dual boot it off my computer with windows xp and i am most confused with my partions on my current configuration 
i have 60gb and it is configured to a back up and then there is another like 3gb on for my windows restore and thee rest is my primary HD and the back up is like 13gb so i want to know how to install linux to that drive and then leave the primary as my boot and the windows recovery one alone how do i do this though

Have dell b130 inspirion notebook with 1.8ghz petium with centrino mobile technology i have 128 mb graphics card intel integrated

---

### Post by freebird54 on 2007-04-03
Not entirely clear yet! :)

It sounds like yolu have 2 drives - one of them all Windows, and the other mostly a backup?  If so - any space you wish to use can be made usable for Ubuntu.  Unlike Windows - it does not care if it is on the first drive, the first partition of whatever drive, or even in a primary partition!

I would want about 15 Gb for a start - but it can be squeezed much tighter than that if need be. How much free space (even if currently in a partition) do you have?  And is it a 2 HD system?  Everything else looks fine - though I didn't catch a RAM total?

---

### Post by metzy85 on 2007-04-03
ok i have 512 ram for starters and i am a ONE hard drive system but in windows xp i have a primary and a backup drive wut do u think i should do har drive wise i want to try to get it on back up which has 12 gb free i am going to use for basic web browsing no gaming and just general stuff

---

### Post by freebird54 on 2007-04-03
All right. SO the current 'backup drive' will become the LInus system?  Does this mean you are willing to take a chance on losing what you have on XP.  It is UNLIKELY - but the same rule applies as when you take an umbrella with you - THEN it won't rain :)

Essentially what you are going to do is remove the partition you now have that you are willing to lose, then install Ubuntu to that now freed space.  It will, by default, use free space and make its own 2 partitions in that space.  13 Gb is plenty for this - 512Mb for swap (like Windows Page file, but on its own) and a working partition.

Here is a link to LOTSA neat information and HowTos.
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
that should get you going.

Specifically, take a look at Plan your partitions, and Installing.  there are a LOT of good HowTos on here - you could also try a Forum Search (right top of page) for Dual boot how to - it will give you some alternatives...

---

### Post by metzy85 on 2007-04-03
ok so can i just have the linux install to that drive and not have to remove the partion and wut will happen if i just hit install when i put in the cd

---

### Post by freebird54 on 2007-04-04
Unless you have currently UNUSED SPACE - it will have to clear some room somehow.  If you have a partition you are not using, the install process will include a partitioning program, in which you can delete the 13Gb partition (creating empty space) and then create the 2 (or 3 your choice) partitions in that space that Ubuntu will need.  There are lots of Howto's on here - and you can keep hooked up the web while installing - which should make it easy to follow along... :)

---

### Post by metzy85 on 2007-04-04
WUT is a root system file i do not know how to do this wutr should i put in for root file system

---

### Post by freebird54 on 2007-04-05
Hoo boy!  Well - I will have to find some links for you to explain the differences between Windows and Linux file systems.  I know I saw a good one recently (on TechRepublic I think) which had diagrams of where things go on the 2 systems.  For now - if you think of 'My Computer' on Windows - below that are all the different drives, C drive, maybe D drive as hard drives, a DVD drive, maybe an USB drive.  Well - on Linux, the root ( shown as / ) is the same as 'My Computer'.  EVERYTHING is attached 'below' this point.  So - if you have a DVD drive - it shows up as a directory (folder) on the / filesystem  (usually as /dev/dvd )  Does this help your mental picture of things?

First you make empty space on the your hard drive - then the install process will make a partition in which to create 'My Computer' - or in our terms, mount the root.

I will try to find you some links, or some Googling might help as well - there is almost more information about these systems than anything else!  Enjoy...

---

### Post by metzy85 on 2007-04-05
this is wut i have in gparted and i can not write to any drives i can only read and i have d to fix this but i can't get it to work if  ask for my password in the terminal i can't type it in and if it does do something it says i don't the permission i have searched the forums to find out how to do this but it does not seem to work

wut is fuse it says i need to have that can't install it and is ntfs-3g 
an install cause i can't get that either i


Hears wut i need i need aim msn or yahoo of a guy who knows wut he is doing and has a few hours to help me individually cause i can not ype all the q\uestions i have hear that would waste everyones time and more and more questions keep coming up and if this does not seem to work soon i am going to ask how to uninstall and make partitions back so that i can run windows and i do not want to do that seems how i HAte windows and its stability so please help me

[http://i149.photobucket.com/albums/s43/metzy85/Screenshot-GParted.png](http://i149.photobucket.com/albums/s43/metzy85/Screenshot-GParted.png)

---

### Post by kidders on 2007-04-05
Your last post is difficult to understand. I *think* you said you're having trouble writing out partition table changes. If that's true, try running the partition editor as root. (It would be a little daft of Linux to let normal users modify your partition table!)

---

### Post by metzy85 on 2007-04-06
i can not write to my primary harddrive it is a ntfs and i can not figure out how to get it turn to a ntfs-3g drive so i can read/write

---

### Post by kidders on 2007-04-06
Ah. If I were you, I would take a look around the web a little before doing that. I never use NTFS myself, but from what I gather, using the ntfs-3g driver can cause some odd behaviour, and is _not_ considered stable (although it is gathering confidence). You should perhaps take a look at the developers' website, in case there are some filesystem features that remain unimplemented, or specific things you should avoid doing.

There is a good deal of discussion here about ntfs-3g ... searching for "ntfs-3g" and "howto" seems to turn up some promising results. You should make sure you have a good understanding of what you're doing though, before actually trying it.

---

