---
title: "Problems with live_cd on my PowerBook G4 15'' (2005)"
date: 2009-12-24
forum: Apple Hardware Users
---

### Post by WRATGUT? on 2009-12-24
Well it's actually my dad's girlfriend's old PowerBook but she left it here so I'm messing around with it. 

I downloaded Ubuntu 9.10 for PowerPC 3 hours ago and burned it at 4x on a DVD+R disc since the ISO was 705 MB and the blank CD I had was only 702 MB.  When I booted the DVD on the PowerBook G4 it just went strait to a log in menu and didn't show the options to run it as a live cd, check for defects, or install like on a PC. I was confused because I don't know what username or password it was talking about. Wasn't it just suppose to boot into a live session? What am I suppose to do?

Also, I burned the DVD on my PC not the PowerBook G4 if that matters.

---

### Post by edog76 on 2009-12-25
To get the DVD to boot, hold down the `c' key when you start the computer. Release once you hear the drive spinning and reading the disc.

PowerPC FAQ is here:
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

---

### Post by WRATGUT? on 2009-12-25
I was able to boot to the live_cd in the first place and instead of showing the options to run it as a live_cd or just install it like on a PC, it just went to the UBUNTU long in menu. So I got stuck there. Now what?

---

### Post by edog76 on 2009-12-27
Oh, sorry! That is indeed weird behavior. You are apparently not alone with this bug. It appears to be tied to Nvidia video cards. Here's a launchpad bug report with, unfortunately, no resolution:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nv/+bug/433925](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nv/+bug/433925)

Also found this ubuntu forums thread but it is for an alpha of 10.4:
[http://ubuntuforums.org/showthread.php?t=1362488](http://ubuntuforums.org/showthread.php?t=1362488)

So, basically, I think you are s.o.l. Sorry.

---

### Post by tiresia on 2009-12-27
What do you get if you press TAB at the first prompt?

---

### Post by WRATGUT? on 2009-12-30
> **edog76 said:**
> Oh, sorry! That is indeed weird behavior. You are apparently not alone with this bug. It appears to be tied to Nvidia video cards. Here's a launchpad bug report with, unfortunately, no resolution:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nv/+bug/433925](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nv/+bug/433925)

Also found this ubuntu forums thread but it is for an alpha of 10.4:
[http://ubuntuforums.org/showthread.php?t=1362488](http://ubuntuforums.org/showthread.php?t=1362488)

So, basically, I think you are s.o.l. Sorry.

But non of the PowerBooks have Nvidia graphics they have ATI.

---

### Post by edog76 on 2009-12-31
Sorry, thought I edited that; I was writing as I was searching, and the first few hits came back with Nvidia, so I was kind of hopeful. A fuller search of the forums brought up numerous graphics problems with Karmic graphics for both ATI and Nvidia. There's a stickied thread spanning several pages of problems at the login prompt even after an install. There are a ton of threads with people not able to get the liveCD to run all across the net. And I've yet to see a solution.

You could try burning another disk, but I'm not hopeful.

---

