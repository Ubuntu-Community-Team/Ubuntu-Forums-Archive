---
title: "Known Issues on Feisty Fawn 7.04 and 12&quot; G4 1.5 Mhz PB + non-destructive partitioning"
date: 2007-04-24
forum: Apple PPC Users
---

### Post by MuchoMungo on 2007-04-24
I've installed Feisty on a new Dell D420 we have at the office and I'm so impressed I'm thinking of switching my dearly belowed 12" G4 PB over to Ubuntu since 
a) I need to start eating my own dogfood in terms of global strategy, and 
b) She's getting on a bit and running Ubuntu ought to make her snappier

So, my questions are :  
**1) Are there any known issues with the Feisty PowerPPC version I need to know about that are currently not solved**
ie. suspend not working, I know about fwcutter for the Broadcom wlan cards, but other "gotchas" that are going to upset me coming from "it just works" land

**2. Does the partitioning tool included that works for Windows work non-destructively for my HFS+ partitions as well ?**
(ie. Can I free up some gigs at the end of my drive and install ubuntu while I move things over and just dual boot ?)

thanks in advance !
Daryl.

---

### Post by SycloneMedia on 2007-05-03
1. Suspend works fine on my machine. Airport Extreme works fine. The only things I haven't gotten to is the backlighted keyboard. I know there's a solution though. However, some things like Flash and Java, which is needed for youtube, etc... are not that helpful at this time (at least on my Powerbook.) And Feisty has some glitch with the screensaver (it's not working at all, just a blank screen.) Other than that, it's great!

2. I don't think it will defragment your blocks, or optimize your system for you... it will however install on the largest available free space on your hard drive. BACK UP, BACK UP, BACK UP first no matter what. If you decide to go ahead and wipe clean and dual-boot, I wrote detailed instructions in one of my previous posts... I don't have too many yet so it won't be hard to find.

---

### Post by jiminy on 2007-05-06
> **SycloneMedia said:**
> 1. Suspend works fine on my machine. Airport Extreme works fine. The only things I haven't gotten to is the backlighted keyboard. I know there's a solution though. However, some things like Flash and Java, which is needed for youtube, etc... are not that helpful at this time (at least on my Powerbook.) And Feisty has some glitch with the screensaver (it's not working at all, just a blank screen.) Other than that, it's great!

Have you previously installed 6.10? I ask because I'm running it on a G4 12" 1.33GHz, and suspend has never worked. If it started working for you *after* you installed Feisty, I might just upgrade after all . . .

Cheers,
jiminy

---

### Post by stmiller on 2007-05-06
Sleep / suspend does not work on PPC Linux for machines with Nvidia video chips. Only ATI works.  I made a note in the PPC FAQs. Hopefully the open source nvidia driver project will have drivers soon and there will be a fix.

And I used a proprietary OS X app called 'Drive Genius' to first defragment my drive, then non-destructively shrink the OS X partition to make room for Linux. Gparted the Linux program supports resizing HFS+ partitions I believe. But I haven't tried it. There's a gparted livecd.

Check out this link:

[http://ubuntuforums.org/showthread.php?t=89960](http://ubuntuforums.org/showthread.php?t=89960)

---

