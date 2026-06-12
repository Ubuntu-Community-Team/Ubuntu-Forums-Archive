---
title: "iMac G3 Will NOT see Xubuntu disk"
date: 2009-05-11
forum: Apple Hardware Users
---

### Post by RealEmotionX on 2009-05-11
no matter what I do, with any Burnt OS (10.2, 10.3 as I dont have a copy of the original disks, or Xubuntu) OS 8.6 does the following "Disk is unrecognizeable"

Except with Xubuntu's disk which will sometimes load in the OS but will not boot. 

I would like to get this machine working and usable for my grandmother, and Xubuntu seems like a good direction to go since I cant get OS X to load. *sigh* but I am about the end of my rope. Except she really wants to email me when I go to college and I cannot stand to break her heart.

---

### Post by stream303 on 2009-05-11
I'd make sure that the disk you burned is done at a very low speed so that the drive can handle it, (you may be on the edge), onto good CD-R media.

That machine may not have enough horsepower to run Xubuntu efficiently - how much ram does it have and which one is it?

[http://www.everymac.com/systems/apple/imac/index-imac.html](http://www.everymac.com/systems/apple/imac/index-imac.html)

Since Xubuntu isn't really very light for old G3's, you may want to use Debian Lenny "stable", and choose the XFCE+LXDE iso for powerpc:

[http://www.debian.org/distrib/](http://www.debian.org/distrib/)

---

### Post by RealEmotionX on 2009-05-11
The mac has somewhere around 160 megs ram.

I got the machine with OS 10.3 installed, about a year ago, and decided to load the then new version of Xubuntu on it. However upon discovering that it would not run Flash videos ( I think there is flash for PPC now, but I am not concerned about it anymore ) I sorta put it away and stopped fooling around with it. At one point I tried loading OSX into it directly but it would have to be downgraded to OS 8.6 before I could go that route.

Thats where I am now.

---

### Post by RealEmotionX on 2009-05-11
Burnt the suggested Debian release at 8x (Toast was set to 1x) and same result. The mac sits there tryng to read the disk but gets to this folder icon with the FINDER logo and a ? mark in rotation. 

Its really annoying to have a useless machine laying around.

---

### Post by stream303 on 2009-05-12
Ah, actually 1x is better, especially for the old G3's.

I have to ask:  are you burning it as an iso-image and not just copying it over?  Is there something in Toast that specifies you want to burn an iso image?

You may also want to try another burner.  This has some good suggestions like using disk utility in osx, isorecorder in windows etc.  Just in case whatever you're running toast on is the problem:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

It applies to Debian as well....

---

### Post by RealEmotionX on 2009-05-12
I set toast to Burn at 1x but it says the average was 8x

And yes I was burning the ISO image in TOAST. I had been using Disk Utility also to the same result. and I have gone through almost 30 CDrs now. So I am trying not to be burn happy anymore. ~_~

---

### Post by RealEmotionX on 2009-05-13
Going to double post here. 

Anyone have any other suggestions? Maybe an external drive or get it to boot from USB? (if either are possible in this case)

---

### Post by tiresia on 2009-05-13
First of all - there is still no flash support for ppc. You can try to use gnash and/or swfdec - but they don't work always good. So if you or your gramdmother really need it, go with MacOSX
Another way to get around this problem is to download the video you want to see.

About Xubuntu: stream is just right. Debian with Xfce and lxde would be the lightest and easiest solution for your hardware.

About booting from Xubuntu or from MacOSX. Are you sure, you are using the right medium for your optical drive (I mean CD±)? Try to Reset PRAM at start up (ctrl-opt-P-R) Do you have an external USB or Firewire HD? Do you have a second Mac?

---

### Post by RealEmotionX on 2009-05-13
The disks are Labeled CD-R and some boot and some dont.

I have an intel Macbook. and the Machine has no firewire ports.

Nothing happens while trying to reset prram

---

### Post by cyberdork33 on 2009-05-13
> **RealEmotionX said:**
> The disks are Labeled CD-R and some boot and some dont.

I have an intel Macbook. and the Machine has no firewire ports.

Nothing happens while trying to reset prram
So, you have a G3 or you have an Intel Machine? Your posts are confusing.

---

### Post by tiresia on 2009-05-13
> **cyberdork33 said:**
> So, you have a G3 or you have an Intel Machine? Your posts are confusing.
Since I asked him, if he has another Mac, I think he means that he has an iMac AND a MacBook.

If it's so, copy the .dmg image of the macOSX 10.2 Installer to your MacBook and plug in your USB HD. With the Apple Disk Utility choose to RESTORE the .dmg image to the USB HD.
Now you should be able to restart the iMac from the USB HD and install MacOSX 10.2 pressing at bootup the OPT-Key

If you are still interested in dual-booting with Xubuntu let me know

---

### Post by cyberdork33 on 2009-05-13
> **tiresia said:**
> Since I asked him, if he has another Mac, I think he means that he has an iMac AND a MacBook.
Sorry, I must have missed that.

---

### Post by jgpcexpert on 2009-05-13
I got an Ubuntu 8.04 on an Apple G3. I found a version that someone posted that already had an Apple boot partition on the .iso so it was able to be easily recognized. It was in this forum actually. If I find the thread again, I'll post it. All I had to do was burn the .iso onto a cd, turn on my G3 and insert the disk quickly, then immediately kept tapping "c" until it booted to the disc.

---

### Post by stream303 on 2009-05-13
> **jgpcexpert said:**
> All I had to do was burn the .iso onto a cd, turn on my G3 and insert the disk quickly, then immediately kept tapping "c" until it booted to the disc.

Some of those drives as they get older and/or dirty inside can be quite finicky about how they boot even when burned at 1x with good quality CD-R's.  So your tip was great.

Some have had to hold down the "C" key for a long time, whereas others had to merely tap it.  Others have had to power on with the CD in the drive first, and others had to power up first, and then insert the cd, doing the "C" key dance.

So don't give up just yet. :)

---

### Post by RealEmotionX on 2009-05-13
would a thumb drive work? 

and I think it owuld be a draw on the 8gb HD I have inside the machine to have Xubuntu and OS X. and useless considering where it is going.

and as far as I can tell, holding C is enough since it has booted OS 8.6's installer that way. As well as a faulty burn (or something) of OS 10.1, but that is useless software anyway. Nothing is compatable with 10.0

---

