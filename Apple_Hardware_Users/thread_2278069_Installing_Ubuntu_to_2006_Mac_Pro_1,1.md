---
title: "Installing Ubuntu to 2006 Mac Pro 1,1"
date: 2015-05-13
forum: Apple Hardware Users
---

### Post by andrew_bishop2 on 2015-05-13
Hi all. I'm new to the forums but pretty familiar with Ubuntu. However, I'm hoping to get a good discussion going on how to install Ubuntu to a 2006 Mac Pro 1,1. This machine is setup with 16GBs of RAM and two 3.0Ghz Quad-Core processors. I know that the 32-bit EFI chip is going to cause me some problems. But, it's important to me because I have 4 of these machines currently running OS X 10.7 and they work extremely well. I just know that eventually I'm going to need an alternative OS as I can't (easily) go past 10.7. 

Here's my hope:[INDENT]1) Install Ubuntu 14 as the sole OS (I don't need any other operating systems for my purposes). I'm willing to go down to the last LTS version if needed.
2) A decently reliable installation - these are used as workstations in my company and basically run nothing but web-based software. But they are used for work purposes and I'm hoping to have them be pretty solid for daily use.[/INDENT]

I've read a few different posts and webpages regarding installation going back to Ubuntu 11, but I can't find any instructions that apply to anything later than that. Should I just set them up with 11? Does it even matter? It seems the links to the version of 11 that was available are no longer valid so I'm hoping to find a way to make this work with 12 or later.

If anyone can help me jump start this, it would be greatly appreciated. Thank you all!

---

### Post by howefield on 2015-05-13
Thread moved to the "*Apple*" forum.

---

### Post by este.el.paz on 2015-05-14
Andrew:

The general wisdom is to have apple machines set up as "dual boot" and use "rEFInd" as the boot selector . . . it shouldn't "matter" too much about the "32 bit" . . . I believe that 64bit could install on a 32, it just won't run like a 64??  But, in any event there are sometimes variations for 32 bit in "mac" flavors . . . .  Best thing to do is download a few "desktop" iso's and burn them to DVD and boot them and see how they run . . . .  The one that seems to have the least need for boot params to get video going and so forth, should be the one . . . and then try an install on one of the machines.  There can be variation from how it runs in desktop and installed . . . .

I have a few different flavors of Ubuntu running on two PPC machines and I have Linux Mint 17.1 MATE running on a Mac Book Pro circa '09 . . . you probably could get any of those systems to run on your Mac Pro's . . . .  You should even be able to get 10.9 running as OSX update . . . main thing to understand is that any changes to OSX you do should be done first, then partition an area for linux and do those installs last . . . .

Enjoy the process, there are no "instant answers" in linux, only the learning . . . .

e..

---

### Post by andrew_bishop2 on 2015-08-28
I wanted to add back to this thread in hopes of getting further replies. I appreciate the above comment, it's just been frustrating because I feel like I've tried everything. 

Here's where I currently am: 
 - I've installed reFind to the OS X partition and I've successfully gotten it to boot into that screen. 
 - I've created a linux partition on the main hard drive, although there nothing on it right now
 - I've DL'd and attempted to boot 5 different versions of linux including Ubuntu, the Ubuntu x64+mac, Linux Mint, Fedora and a Debian Mini distro with no luck. The furthest I've gotten is getting a "Boot Error" screen when trying to load Ubuntu/Mint. 

I've had the best success with cloning a USB disk to an actual hard drive and then plugging that into the mac as a 2nd hard drive.reFind keeps telling me that my Mac may not boot very well off a USB drive. I've had mixed results with just booting off the DVD drive. 

Again, I'm trying as best as I can to find a way to make this work as these machines are still have very very good hardware specs and I shouldn't have to pay a bunch of money to replace them simply because Apple decided they didn't want to support the 32-bit EFI chip after 10.7. I managed to get one of them to update to 10.9, but it crashed right after running system updates. Not only this, but I've taken it as a personal challenge to see if I can make this work in a reliable way so that I can post it on the web for anyone else to find. 

I also thought about the possibility of running Virtual Box and seeing if I can get it to install to the Linux partition that way. I'm just not really sure how to proceed and the information out on the web seems spotty on how exactly to make this happen. 

Any advice would be more than appreciated!

---

### Post by luciano.x on 2015-08-28
Hi.

Maybe the reason is a bug in its firmware.
I assume you tried to boot the installer from rEFInd menu and alt/option?
 
Food for thought
> The oldest Mini (macmini1,1) is typically the most problematic, due to bugs in its firmware. When booting off CD/DVD, if there is more than one El Torito boot record on the disc then the firmware gets confused. It tried to offer a choice of the boot options, but it locks up instead. Unfortunately, all of the normal Debian installer options for both i386 and amd64 now include 2 El Torito boot records (one for BIOS boot, and one for EFI boot). Specifically as a workaround for this broken firmware, there is now a new flavour of i386 netinst image. Look for **debian-mac-XXX-netinst.iso**. This image should boot and install happily on a macmini1,1, giving you a normal Debian installation when it's finished, booting in BIOS mode using GRUB. There's quite a delay before the GRUB menu comes up (~30s or so) - be patient!
Source [https://wiki.debian.org/MacMiniIntel](https://wiki.debian.org/MacMiniIntel)

 [URL="https://wiki.debian.org/MacMiniIntel"]
[/URL]

---

### Post by este.el.paz on 2015-08-28
> **andrew_bishop2 said:**
> 

Here's where I currently am: 
 - I've installed reFind to the OS X partition and I've successfully gotten it to boot into that screen. 
 - I've created a linux partition on the main hard drive, although there nothing on it right now
 - I've DL'd and attempted to boot 5 different versions of linux including Ubuntu, the Ubuntu x64+mac, Linux Mint, Fedora and a Debian Mini distro with no luck. The furthest I've gotten is getting a "Boot Error" screen when trying to load Ubuntu/Mint.  

Andrew:  Possibly lucianox's comment might be apt, but it seems like you should be able to find something to run very well on your MacPro.  When you say "attempted to boot" . . . how are you making that attempt?  Did you check the md5sum number for the iso?  Did you try to burn the iso to a DVD and use the "c" key to boot the ****LIVE**** DVD version?  If you are downloading the alt install or mini installer you can't test the system out . . . ????  And, you tried the 14.04 Xubuntu or Lubuntu 32 bit isos?  And/or you tried 12.04 Xubuntu or Lubuntu for 32 bit?  And, none of them booted?  You can also go back in time with LM, but I wouldn't think you would have to, as now rebecca is based on ubuntu 14.04.  And, if you have run an attempt at install, you can't boot into the GUI installer??  Can you boot an OSX install disk?  Can you load or open any DVD?

> I've had the best success with cloning a USB disk to an actual hard drive and then plugging that into the mac as a 2nd hard drive.reFind keeps telling me that my Mac may not boot very well off a USB drive. I've had mixed results with just booting off the DVD drive.   Listen to rEFInd, if it's "telling you something" then . . . mixed results are better than none--try the DVD boot live session.

>  Again, I'm trying as best as I can to find a way to make this work as these machines are still have very very good hardware specs and I shouldn't have to pay a bunch of money to replace them simply because Apple decided they didn't want to support the 32-bit EFI chip after 10.7. I managed to get one of them to update to 10.9, but it crashed right after running system updates. Not only this, but I've taken it as a personal challenge to see if I can make this work in a reliable way so that I can post it on the web for anyone else to find. 
I also thought about the possibility of running Virtual Box and seeing if I can get it to install to the Linux partition that way. I'm just not really sure how to proceed and the information out on the web seems spotty on how exactly to make this happen. 
!

Agreed, apple shouldn't be dropping their machines . . . but, it is interesting that "10.9 crashed" . . . of course there is always 10.8.  I'm still running 10.4.11 on two PPC machines . . . and I've got dual boot Xu/ToriOS 12.04 on a Sawtooth which I'm using right now to post this--12.04 is "rock solid" and you should easily be able to get it to run **if your machines are OK** . . . but you should have no problem getting a 32 bit 14.04 system to run . . . I have 14.04 on a '04ish iBook . . . it works, but probably pushing the technological envelope and I might roll it back or try ToriOS as the DE and see if that is easier on the machine.  Keep trying, but, check the md5sum numbers on the downloads and keep trying to boot a liveDVD . . . whatever works best/easiest then try the install.  But, possibly the Parallels or VMFusionware install might be best all-around solution . . . run linux within OSX--safer.  Read the Mactel FAQ on fan and heat issues.

e...

---

