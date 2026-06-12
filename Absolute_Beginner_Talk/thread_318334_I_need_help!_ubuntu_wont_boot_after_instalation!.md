---
title: "I need help! ubuntu wont boot after instalation!"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by scooterboi on 2006-12-13
hi, all i have just nstalled ubuntu (from the alternate installer cd) im using the dual boot method were u remove windows ect. but i am at the stage were i have installed ubunu and i am booting for the first time but all goes well untill i get a screen with a black bacground and  the ubutul logo at the top and a progress bar in the middle with a little bit of yellow at the left of the bar  and iff i wait for a minute ot two at the bottom i get text that says loading drivers or something  then an ok appears on the left but then nothing happens ? can any one help  me i would apreatiate it heaps if you could ? im a windows nerd but i am a newbee to linux!8) :confused: :confused: :confused:

---

### Post by Fully216 on 2006-12-13
What version of ubuntu did you install?  6.06 (Dapper Drake) is more stable compared to 6.10 (Edgy Eft) which as the name implies is cutting edge.  

It could be many things that are causing the problems.  It would help if you could see exactly where it froze (what driver was loading).  My hunch is that it was a video card driver, but I have no basis to stay why I think so.

Did you try running the live CD?  This will give you an indication of a possible hard drive problem (as the live CD does not use the hard drive at all).  This will allow you to mess around and see if something is not working, and might be the cause of your problem.  It will more importantly indicate you if all of your hardware is supported.

You can try to run the command line version (does not start x).  There should be an option in your GRUB (boot menu) that came up before the ubuntu splash screen for command line only.  If you can run without any GUI, that would indicate a graphic card problem.  If that is the case, you can edit /etc/X11/xorg.conf to use a different driver, or install a new driver from the command line interface (CLI)

---

### Post by pay on 2006-12-13
I have always had a problem with my Ati card (x800 pro) and xorg 7.1. It seems the opensource driver doesn't agree and I have to install the properitery driver instead.

---

### Post by scooterboi on 2006-12-13
thanx for helping guys umm well ill try ur first suggestion trying the live cd i dont have it yet its comming in the mail  i sent for it lastnight umm my pc specs are pentium 5 processor 2.6  umm 512 meg ram 3 hdrives 2 for windows and a 40gig 4  ubuntu, 1 dvd burner and i have an asus mother board p5vdc-mx   with built in graphics it originaly was an hp computer but it has had a total upgrade of everything now ! :D

---

### Post by scooterboi on 2006-12-13
btw i installed v 6.06 :cool:

---

