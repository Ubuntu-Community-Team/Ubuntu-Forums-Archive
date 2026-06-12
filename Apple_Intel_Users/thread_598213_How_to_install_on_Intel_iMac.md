---
title: "How to install on Intel iMac"
date: 2007-10-31
forum: Apple Intel Users
---

### Post by blop on 2007-10-31
Hi guys im trying to liberate my work iMAc 20" core 2 duo 2ghz 2gig ram from the clutches of Mac OSX but im not sure how.....and im quite surprised to find there is no easy HOW TO....

so i was wondering how i go about it....

sadly i must have it dual booting with MAC OS and hopefully it defualting to MAC OS so it does not disturb my colleagues....its supposed to be a test machine apparantley and not my personal toy.

Cheers all! 

:)

So far i have resized the partitions with GParted booted from the GUtsy install disc.....im gonna reboot and hope MAC OS still works!

---

### Post by cyberdork33 on 2007-10-31
> **blop said:**
> Hi guys im trying to liberate my work iMAc 20" core 2 duo 2ghz 2gig ram from the clutches of Mac OSX but im not sure how.....and im quite surprised to find there is no easy HOW TO....

so i was wondering how i go about it....

sadly i must have it dual booting with MAC OS and hopefully it defualting to MAC OS so it does not disturb my colleagues....its supposed to be a test machine apparantley and not my personal toy.

Cheers all! 

:)

So far i have resized the partitions with GParted booted from the GUtsy install disc.....im gonna reboot and hope MAC OS still works!
If you have already resized the partition, you just have to install. After installing, hold ALT on bootup to choose between OSX and Ubuntu.

---

### Post by doublemeat on 2007-11-01
There are tons of how-to guides out there for macbook and ubuntu.  I referenced about a half dozen of them when I did what you are doing.  I don't have the URLs handy any more, but a smart google search will turn them up quickly, e.g. "macbook dual-boot ubuntu".  I know there's even a guide for Gutsy already out, and in these forums no less.  Good luck.  Ubuntu on the macbook rocks.  Although, getting the wireless and power management features working properly is still a bit challenging.  It works perfectly as a desktop so far, not so great (yet) as a battery-operated notebook.

I have mine triple-booting with OSX, Gutsy, and XP.  And within Ubuntu, I run a few different flavors of Windows via the free VMware Server, which imo is a better vm player than VMware Player, and every bit as fast as VMware Fusion is on the mac...  It's just too bad I can't run mac osx in ubuntu via VM.  (Without serious hackery, at least.)

---

### Post by liberalist on 2007-11-04
Hi all,

I am trying to upgrade to Kubuntu 7.10 Gutsy Gibbon on my Intel Core 2 Duo iMac. However, it fails with the i386 desktop edition CD. Should I download and burn an AMD-64 desktop edition CD? It says in the [MacBook Community documentation]("https://help.ubuntu.com/community/MacBook") that this is an option for Core 2 Duo processor (note the '2'). 

Will this solve my problem? I cannot boot into the K desktop environment, namely. Even not when I opted for "Start Kubuntu in safe graphics mode". 

Thank you in advance. 

PS: I have Kubuntu 7.04 successfully installed on a ~20 GB partition and 2 GB swap :) However, I would like to use the latest version. I use rEFIt to choose between two operating systems, Mac OS X and Kubuntu.

**Update:** I have found [Ubuntu documentation on how to upgrade to 7.10]("http://www.ubuntu.com/getubuntu/upgrading") using an alternate CD (near the bottom of the page). The question remains whether I should opt for the i386 Intel or AMD 64 version? Does this work with Kubuntu too?

---

### Post by cyberdork33 on 2007-11-04
> **liberalist said:**
> Hi all,

I am trying to upgrade to Kubuntu 7.10 Gutsy Gibbon on my Intel Core 2 Duo iMac. However, it fails with the i386 desktop edition CD. Should I download and burn an AMD-64 desktop edition CD? It says in the [MacBook Community documentation]("https://help.ubuntu.com/community/MacBook") that this is an option for Core 2 Duo processor (note the '2'). 

Will this solve my problem? I cannot boot into the K desktop environment, namely. Even not when I opted for "Start Kubuntu in safe graphics mode". 

Thank you in advance. 

PS: I have Kubuntu 7.04 successfully installed on a ~20 GB partition and 2 GB swap :) However, I would like to use the latest version. I use rEFIt to choose between two operating systems, Mac OS X and Kubuntu.

**Update:** I have found [Ubuntu documentation on how to upgrade to 7.10]("http://www.ubuntu.com/getubuntu/upgrading") using an alternate CD (near the bottom of the page). The question remains whether I should opt for the i386 Intel or AMD 64 version? Does this work with Kubuntu too?
you shouldn't need any cd, just get the updates from online and you can upgrade like that.

---

### Post by liberalist on 2007-11-04
> **cyberdork33 said:**
> you shouldn't need any cd, just get the updates from online and you can upgrade like that.

Thanks for your reply.

However, I can't do a network upgrade as I did not manage to get my wireless Airport Extreme card working on Kubuntu 7.04 Feisty Fawn. I tried ndiswrapper and this failed over and over again, which gave me a headache. Unfortunately, my wireless access point is too far away to reach with an ethernet cable. 

If you have any suggestions how to get an airport extreme card working on Kubuntu, that would be very nice. Please note I have an iMac Intel Core *2* Duo, of which the airport extreme card might not be supported by restricted drivers.

---

### Post by cyberdork33 on 2007-11-04
> **liberalist said:**
> Thanks for your reply.

However, I can't do a network upgrade as I did not manage to get my wireless Airport Extreme card working on Kubuntu 7.04 Feisty Fawn. I tried ndiswrapper and this failed over and over again, which gave me a headache. Unfortunately, my wireless access point is too far away to reach with an ethernet cable. 

If you have any suggestions how to get an airport extreme card working on Kubuntu, that would be very nice. Please note I have an iMac Intel Core *2* Duo, of which the airport extreme card might not be supported by restricted drivers.
You cannot move your imac for a few minutes? there isn't much to move.

What was wrong with your ndiswrapper install? what do you mean by 'failed'?

---

### Post by liberalist on 2007-11-04
> **cyberdork33 said:**
> You cannot move your imac for a few minutes? there isn't much to move.
True, but I don't have a good desk nearby... My access point is in the meter cupboard. On top of that, my dog sleeps there most of the time (she is quite old). She is not really obedient. 

> **cyberdork33 said:**
> What was wrong with your ndiswrapper install? what do you mean by 'failed'?

It produced some errors; probably beginners' mistakes. I will try the guidelines of a MacBook again, see if they do work on my iMac. There are other matters to attend to at the moment, so you will hear the results in a week or so.

---

### Post by liberalist on 2007-11-05
The upgrade to Kubuntu 7.10 produced an error: I cannot boot into the graphical K desktop environment. I have read through the [release notes]("http://www.ubuntu.com/getubuntu/releasenotes/710") and it seems to be a problem related to my ATI graphics card. 

Should I open a new thread with pictures of my problem and a detailed explanation? Or should I search for a how-to? I could install Kubuntu 7.04 again, as I have a back-up of important documents.

---

### Post by cyberdork33 on 2007-11-05
> **liberalist said:**
> The upgrade to Kubuntu 7.10 produced an error: I cannot boot into the graphical K desktop environment. I have read through the [release notes]("http://www.ubuntu.com/getubuntu/releasenotes/710") and it seems to be a problem related to my ATI graphics card. 

Should I open a new thread with pictures of my problem and a detailed explanation? Or should I search for a how-to? I could install Kubuntu 7.04 again, as I have a back-up of important documents.

If you want to start from scratch that is fine, but I don't think that will fix the problem.

The ATI 'blank screen' issue affects those using the open source ATI driver. This should not be what you are using.

What does it do exactly? are you getting a message about x crashing?

---

### Post by liberalist on 2007-11-05
> **cyberdork33 said:**
> If you want to start from scratch that is fine, but I don't think that will fix the problem.

The ATI 'blank screen' issue affects those using the open source ATI driver. This should not be what you are using.
I haven't chosen for the open source ATI driver, but for the "safe graphics one" (vesa driver). 

> **cyberdork33 said:**
> What does it do exactly? are you getting a message about x crashing?
Yes, something like that. The computer tries to boot into KDE, but an error is displayed after about six unfruitful attempts. 

**Good news:** Upon a second try (installing through "Start Kubuntu in safe graphics mode"), I managed to install Kubuntu 7.10 (Intel i386 desktop edition). It works quite good and several 7.04 bugs are solved :) 

Anyway, I would like to thank the community very much for making such a versatile Linux distribution. And, of course, for your kind help.

---

