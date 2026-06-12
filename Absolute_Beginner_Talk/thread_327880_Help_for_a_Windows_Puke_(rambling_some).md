---
title: "Help for a Windows Puke (rambling some)"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by RHH on 2006-12-29
Reading this forum has truly humbled me - again!  I just registered and read the stickied posts for noobs.  This is my first time here.

My first computer was an IBM mainframe before S/360, before IC's.  DOS, VSA, OS/MVS etc. were the OS's I used but I had systems programmers who kept them fed and tamed.  My first personal computer was an 8086 running PC/DOS which has been replaced by a succession of PC's and OS's up to and including XP (Pro).  For a time, I managed a bunch of Unix platform developers and sys admins but never really learned the OS.

Now I want to install and learn Linux on my PC in a dual boot mode with XP-Pro.  I believe open source will eventually replace most proprietary software; so I want to get into the program. I read the ubuntu (should this word be capitalized?) Support basic documentation far enough to realize that my vocabulary needs work.  Do Linux people use 'partition' the same way windows people do?  I think of it as dividing up the physical space on a disk into many virtual spaces (as in C:, D:, E:, etc.)

Not being a terribly patient sort - or one who learns best by reading the doc, but one who seems to get there fastest by a combination of reading enough to act upon then acting - I want to get a basic installation up and running; but I need some very rudimentary help.  Can someone point me to a how-to that will tell a not-too-expert Windows type how to inventory his hardware and capture the information needed to make decisions about partitioning for Linux?  Does the question even make sense?

I have a P4 3Ghz CPU with 2 GB RAM, 2 IDE HD's (40 & 80 GB), an external IDE HD (80 GB), CD ROM, and and DVD   R/W with printers and scanners to boot (oops, also).  My ISP is RoadRunner with cable modem.  We have two PCs sharing this line using a wireless modem.  I use Firefox and Thunderbird for browsing and e-mail and have been an MS-Office user for as long as it's been around.  I do a little (very little) HTML, CSS, PHP work on a basic website but want to do more.

What specifics about the hardware should I have in hand to plan a dual boot Linux ubuntu 6.10 (Edgy Eft) install?  Should I use a different distribution?  (I just downloaded 6.10 based on googling and reading/skimming the ubuntu pages.)  I realize that I have to do some actual thinking to plan this step (as opposed to mounting a CD and following a wizard); but I need some hand holding to get started.

I promise to hold other hands when I've acquired a bit more of the necessary information to flatten the curve somewhat.

TIA
RHH

---

### Post by Frak on 2006-12-29
Just run a Live CD, and see if your hardware is supported that way, and if you have problems, ask in the Laptops & Hardware Section, and you should have responses, but from what I see the only problem you might have is a cable modem, make sure it goes through the Ethernet port if you can, USB is partially supported for Cable Modems.

---

### Post by srunni on 2006-12-29
Well, it shouldn't be too hard to install Ubuntu. I would recommend that you install it on the same hard drive as you've installed Windows, and keep the other two hard drives you have purely data hard drives. When installing Ubuntu, make sure that you defragment your hard drive, so that you have a continuous space at the end of that hard drive for Ubuntu. You can do this with the provided program in XP, but I prefer Diskeeper Professional for the job. Anyway, after that, just pop in the CD (make sure your bios is set to boot first from your CD drive), load up the live Ubuntu, and begin the install. When you get to the partitioning step, you will find it very easy - just select the automated option that will repartition your hard drive and install Ubuntu. That's all there is to it! Check out [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php) , [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/) , and [http://doc.gwos.org/index.php/Main_Page](http://doc.gwos.org/index.php/Main_Page) for more information.

---

### Post by d3v1ant_0n3 on 2006-12-29
I really should bookmark this page for handy posting:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

Contains *so* many useful articles and walkthroughs for newcomers. Saved my brain on many occassions. Well written, easy to follow, not patronising.

Welcome:cool:

---

### Post by bobpur on 2006-12-29
I believe you might have an easier time dualbooting to two different harddrives. PATA drives are my preference over SATA as they pretty much work right off the bat. SATA drives will dualboot with some tinkering. 
FYI-- Install Windows first then your linux distro second. If you install windows last, it will overwrite your bootloader (GRUB or LILO) rendering linux inaccessable.

                                                          Good Luck.

---

### Post by riven0 on 2006-12-30
Yeah, I agree; your best bet is to burn the liveCD iso, boot it up and make sure it detects all your hardware. Then you'll be good to go. If it doesn't detect all your hardware there are usually workarounds, but they may take some time.

---

### Post by seijuro on 2006-12-30
> **RHH said:**
> I read the ubuntu (should this word be capitalized?) Support basic documentation far enough to realize that my vocabulary needs work.  Do Linux people use 'partition' the same way windows people do?  I think of it as dividing up the physical space on a disk into many virtual spaces (as in C:, D:, E:, etc.)


When refering to the Ubuntu distro of Linux yes it should be capitalized as it's a name like John or James etc.

There are some new vocabulary you will need to learn but its not at all as complicated as it may seem at first. A partition is still a partition, a "slice" of your hard drive. Most things in Linux are self-evident following a stronger line of logic than windows. If you have more questions about lingo just ask or if you like looking stuff up yourself [whatis.com]("http://www.whatis.com") is a really good resource for getting definitions of new terms you run into.

---

### Post by smoker on 2006-12-30
> **RHH said:**
> Not being a terribly patient sort - or one who learns best by reading the doc, but one who seems to get there fastest by a combination of reading enough to act upon then acting - I want to get a basic installation up and running; but I need some very rudimentary help.  Can someone point me to a how-to that will tell a not-too-expert Windows type how to inventory his hardware and capture the information needed to make decisions about partitioning for Linux?  Does the question even make sense?


running the live-cd is the way to start, you can try open office, a great replacement for ms office, far superior imo. once you are confident, then go for the hard drive install,

cheers, and welcome to ubuntu:D

---

