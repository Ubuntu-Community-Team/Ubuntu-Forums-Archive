---
title: "Is Lubun 12.10 too advanced for G4 iBook?"
date: 2013-01-13
forum: Apple Hardware Users
---

### Post by este.el.paz on 2013-01-13
Folks:

I've got a dual boot OSX & straight Deb Wheezy running on my G4 iBook and I originally set the partition at 6GB for the Debian side--I keep getting "not enough disc space to do upgrade" error windows.  So, I've been thinking about getting set up to erase the whole disc and expand the partition to perhaps 10 GB and dual boot OSX & Lubuntu--which I also did on my old iMac (iMac is kernel panicing itself into the big sleep and is more or less out of service).  So, I have the 12.04 ppc .iso already but I thought since 12.10 is "newer" to try it out so I burned it today and tried to boot the iBook with it, I get to the splash window and when the dmesg?? stuff runs it ends with "fixing recursive fault but reboot is needed" . . . .  I restarted several times and tried a few boot commands . . . but basically could not get into the desktop.  Yesterday I had no problem booting the 12.04 Live DVD, and usually in the past the iBook could boot most of the various Debian systems I've tried, but the iMac was a real problem to get anything to run on.  Is 12.10 too advanced to use on the 933MHz 656 MB RAM G4 iBook (dualUSB)????  And, could the 12.04 Lubuntu system be squeezed into the 6GB or would I need to expand it?

Many thanks,

e.e.p.

---

### Post by vinibali on 2013-01-14
> **este.el.paz said:**
> Folks:

I've got a dual boot OSX & straight Deb Wheezy running on my G4 iBook and I originally set the partition at 6GB for the Debian side--I keep getting "not enough disc space to do upgrade" error windows.  So, I've been thinking about getting set up to erase the whole disc and expand the partition to perhaps 10 GB and dual boot OSX & Lubuntu--which I also did on my old iMac (iMac is kernel panicing itself into the big sleep and is more or less out of service).  So, I have the 12.04 ppc .iso already but I thought since 12.10 is "newer" to try it out so I burned it today and tried to boot the iBook with it, I get to the splash window and when the dmesg?? stuff runs it ends with "fixing recursive fault but reboot is needed" . . . .  I restarted several times and tried a few boot commands . . . but basically could not get into the desktop.  Yesterday I had no problem booting the 12.04 Live DVD, and usually in the past the iBook could boot most of the various Debian systems I've tried, but the iMac was a real problem to get anything to run on.  Is 12.10 too advanced to use on the 933MHz 656 MB RAM G4 iBook (dualUSB)????  And, could the 12.04 Lubuntu system be squeezed into the 6GB or would I need to expand it?

Many thanks,

e.e.p.


at yaboot, try to start with the following command:
Linux snd-powermac.blacklist=yes
if you got over the "fixing recursive fault but reboot is needed" than that common issue is maybe fixed. i got a 12" 1,33 Powerbook with FX5200, i stuck with the desktop now. i hope this works for your, to get over the processor kernel panic.
if works, you can set it defaultly to the bootparameter, i wrote you if works :)
[https://wiki.ubuntu.com/PowerPCKnownIssues]("https://wiki.ubuntu.com/PowerPCKnownIssues")

---

### Post by este.el.paz on 2013-01-14
> at yaboot, try to start with the following command:
Linux snd-powermac.blacklist=yes
if you got over the "fixing recursive fault but reboot is needed" than that common issue is maybe fixed. i got a 12" 1,33 Powerbook with FX5200, i stuck with the desktop now. i hope this works for your, to get over the processor kernel panic.
if works, you can set it defaultly to the bootparameter, i wrote you if works 
[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

@vinibali:

Thanks for the reply, much appreciated . . . I did see a list of modules along with the "snd-powermac" being repeated several times, so thanks for that I'll try it out maybe tomorrow.  Funny that the problem is listed on the PPC FAQ, I've been looking at so many pages I think I might have even been there and missed that item . . . .

On the size of partition, I noted that on the Lubuntu install page they ask for "at least 4 GB" and so I might be able to fit it into the space I have now-- 5GB for home, 1 GB for swao, and 1 MB for Yaboot.  So I might try it w/o erasing the OSX side and see how it goes . . . now, question is 12.04 or 12.10 . . . if I can boot the 12.10 maybe . . . but 12.04 is LTS.

e.e.p.

---

### Post by este.el.paz on 2013-01-15
Gents:

Just to follow up on my struggle, my Linux struggle  . . . I am typing this using the 12.10 LiveDVD but the suggested modifiers "Linux snd-powermac.blacklist=yes"  did not work.  I got a "linux: -1, /vm linux: Unable to open file, invalid device"  error report.  I changed it to "linux snd-powermac.blacklist=yes" and got the same reply.

I hit the Tab key and selected a combo of the terms using "live driverupdates powerpc" got me into a slightly low resolution GUI, but it is readable and use-able unlike some of the iMac issues I've had.  It mentioned something about "b43 failed to load" which was something that required work for the iMac, but previously the iBook did not.  I checked out the PowrPC Known issues page again and then read thru some of "ojordan's" bug reports from last year . . . .  I believe this iBook does have the radeon driver, which previously did not need all the fiddling that the iMac did with the Nvidia card . . . over there I did use the fbdev driver for awhile until an update took it out and then I had to go thru a process to retro use, what? the "nv" driver.

What I seem to notice is that the straight Wheezy "Firefox" browser seems to be very slow, whereas the Lubun 12.04 & now this 12.10 seem to be reasonably fast . . . .   As a dual-boot type person and used to the low maintenance aspects of Apple, I would like to choose the path of least resistance . . . to install with the least extra steps . . . seems like 12.10 has made it a tad more complicated for the PPC user?  And I thought that Chrome was part of 12.10, but it still seems like it's FF for the browser?  Anyway, that's the latest in my Linux struggle(s) . . . .  Got the 12.10 Live show working . . . but looks like I'd need to come up with an Xorg file for the iBook to improve the resolution????, whereas in the past the radeon card was set to go right out of the box, etc.

e.ep.

---

### Post by este.el.paz on 2013-01-19
> What I seem to notice is that the straight Wheezy "Firefox" browser seems to be very slow, whereas the Lubun 12.04 & now this 12.10 seem to be reasonably fast . . . . As a dual-boot type person and used to the low maintenance aspects of Apple, I would like to choose the path of least resistance . . . to install with the least extra steps . . . seems like 12.10 has made it a tad more complicated for the PPC user? And I thought that Chrome was part of 12.10, but it still seems like it's FF for the browser? Anyway, that's the latest in my Linux struggle(s) . . . . Got the 12.10 Live show working . . . but looks like I'd need to come up with an Xorg file for the iBook to improve the resolution????, whereas in the past the radeon card was set to go right out of the box, etc.

Folks:

So far no follow up comments on the question about whether 12.04 is "plug n play" as far as drivers goes on iBook . . . not needing an xorg.conf file; whereas it looks like 12.10 needs some driver adjustment or needs an xorg.conf file??? to get basic stuff like "suspend" working??  Any thoughts?

e.e.p.

---

### Post by este.el.paz on 2013-02-17
> **este.el.paz said:**
> Folks:

So far no follow up comments on the question about whether 12.04 is "plug n play" as far as drivers goes on iBook . . . not needing an xorg.conf file; whereas it looks like 12.10 needs some driver adjustment or needs an xorg.conf file??? to get basic stuff like "suspend" working??  Any thoughts?

e.e.p.

Gents, etc:

I see I posted this about 4 weeks ago, still no thoughts provided for it or similar questions posted in the "testers wanted for 12.04" thread . . . .  I'd still like to know if "suspend" is something that works in 12.04 for iBook, testing the LiveDVD there was no suspend button???

e.e.p.

---

### Post by imacg3ppc on 2013-02-20
i'm having graphics issues with a g3 imac, almost impossible to get live dvd to work with r128 for me. still working on getting xorg.conf configured but i imaging using the suspend function would not work that well if working from the live iso cd? do you have an install of 12.04 or 12.10? i'm using 12.04 because there is so much more documentation and users that have dealt with most important issues for ppc.

come to think about it... i couldn't even find an install iso for ppc for 12.10??? definitely not on the ubuntu site.

---

### Post by este.el.paz on 2013-02-20
> **imacg3ppc said:**
> i'm having graphics issues with a g3 imac, almost impossible to get live dvd to work with r128 for me. still working on getting xorg.conf configured but i imaging using the suspend function would not work that well if working from the live iso cd? do you have an install of 12.04 or 12.10? i'm using 12.04 because there is so much more documentation and users that have dealt with most important issues for ppc.

come to think about it... i couldn't even find an install iso for ppc for 12.10??? definitely not on the ubuntu site.

@imacg3ppc:

Thanks for the post, I do appreciate the reply.  I have both 12.04 and 12.10 LiveDVD, but I also have the "Lubuntu 12.10 alternate PPC.iso"  installer only, which I did find by following links, probably from the Lubuntu site, because there was a recommendation that ppc users would be better to use the alternate installer . . . .  I probably have the link if you can't find it--busy right now.  But, agreed, if and when I get the time to change the system on the iBook, it looks like it's easier to go to 12.04 rather than 12.10 . . . .

e.e.p.

---

### Post by gordintoronto on 2013-02-21
This might be worth reading:
[http://powerpcliberation.blogspot.ca/2012/10/lubuntu-install-guide.html](http://powerpcliberation.blogspot.ca/2012/10/lubuntu-install-guide.html) 

Are you aware of this command to free up disk space:
sudo apt-get clean

Even so, I think being tight on disk space is painfully annoying. Could you pop a second hard drive into your computer?

---

### Post by este.el.paz on 2013-02-21
> **gordintoronto said:**
> This might be worth reading:
[http://powerpcliberation.blogspot.ca/2012/10/lubuntu-install-guide.html](http://powerpcliberation.blogspot.ca/2012/10/lubuntu-install-guide.html) 

Are you aware of this command to free up disk space:
sudo apt-get clean

Even so, I think being tight on disk space is painfully annoying. Could you pop a second hard drive into your computer?

@gdintoronto:

It seems like you might be replying to me, so, thanks for the link--I have done numerous Linux installs, but there were some tips there, like the Radeon KMS stuff that might help out.  When I started playing around with Linux a couple years ago, the advice was saying that 5 GB was "adequate" and so I cut out 6.  

It's interesting to see the "zen" comment that the "iMac G4 is one of the most difficult systems to install Linux on . . . ."  That has been my experience.  But, here we're talking about the iBook . . . radeon driver, and, as I've never had it apart I don't know for sure, but I would guess there is no room for another HD.  Certainly it would be perhaps easier to go that route, but right now the 40GB HD is cut approx. 34 GB for OSX and 6 GB for Wheezy.  As far as I remember the Wheezy install did not require an xorg.conf file, but it did take adding the wifi driver--and it's more or less OK, sort of a step up from OS9.

When the iMac had the Xu/Lu system running in LXDE it was fine as well, but it's all about the time factor right now . . . finding the several hours to do the install and then the multiple hours to fiddle with it.  If I could see that 12.10 would go into the tight space I have now, without needing a lot of tweaking I might do that, but it seems like??? from the couple comments posted back that 12.04 is easier to install . . . but from "zen's" comment it seems like 10 GB would be better, so . . . I'd need a bit more time to re-chop the HD . . . .

Yes, I am familiar with the "sudo apt-get clean" or "sudo apt-get autoclean" commands.  It's interesting how the Wheezy update process will sometimes tell me "low disk space" for an upgrade and yet will seemingly do it anyway, and then next time not have "low disk space" . . . .  Anyway, for checking email and minor web surfing most anything will do--but Lubuntu looks like it's a bit more fun, if only it installed the "suspend" feature . . . . : - (

e.e.p.

---

