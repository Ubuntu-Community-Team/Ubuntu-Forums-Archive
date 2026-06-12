---
title: "MacBook trackpad in Oneiric"
date: 2011-10-09
forum: Apple Hardware Users
---

### Post by VirtualOzelot on 2011-10-09
Wasn't sure if this belongs in the Apple Users or Ubuntu+1 subforum. Please move me if I'm in the wrong place.

Installed Ubuntu 11.10 on my MacBook 6.1 yesterday. Almost everything works beautifully, way above expectations. Unity 3D (which didn't work with the Virtualbox drivers) is simply gorgeous and very useable. Kudos!

My only problem is with the trackpad. First of all, it didn't allow two finger scrolling, although I was able to fix this using synaptiks. Second, I'm having problems getting the clicking-dragging-dropping gesture I'm used to from OS X and nearly every other touchpad on any other system, to work. That is, pressing the bottom left corner of the trackpad with one finger while dragging another finger across the trackpad to move objects around. The way it's configured it seems to interpret the second finger's movement as a 'tapping' gesture, which breaks the current 'dragging' mode. The only way to drag windows is currently to press down anywhere on the trackpad and then drag the same finger around (exhausting), or using the three finger (=> middle click?) magic gesture which is, although beside the point, absolutely fantastic. :D

I don't need for any multitouch magic to happen, I just want basic drag-and-drop functionality. I've been searching the forums thoroughly but there's just too many different solutions, drivers, versions of Ubuntu and specific models of the MacBook represented in those answers for me to know what to go for. I'd imagine support for this isn't completely tailored toward 11.10 yet, but I'm sure there must be some MacBook tester out there who could share his or her experience and maybe help me out a little.

Cheers and thanks for a great desktop experience so far. :)

EDIT: Tried touchegg out, it's like synaptiks but with more multitouch functionality, still doesn't solve my problem however. What I need is a software layer that prevents touching the bottom of the trackpad to be interpreted as 'tapping'. Simply put, the bottom of the trackpad should be reserved for clicking, not tapping.

EDIT2: Installed the xserver-xorg-input-multitouch package and put the included conf file in /etc/X11/xorg.conf.d. Solved the basic problem with dragging but the whole experience still is a bit shifty. Tapping is very over-sensitive, resting my thumb on the bottom of the trackpad makes the cursor jump around a little bit too much. Will play around with touchegg, see if that helps.

---

### Post by majortom67 on 2011-10-14
It worked form me on Maverick with instructions here ([https://help.ubuntu.com/community/MacBookPro7-1/Maverick#Touchpad](https://help.ubuntu.com/community/MacBookPro7-1/Maverick#Touchpad)) but some mdoules (BCM5974 first) are not yet available for Oneiric. Hoe it's jus a matter of days.
SImon

---

### Post by qirtaiba on 2011-10-16
I have it working, though it required compiling a custom kernel (which also fixed the wireless driver).  See post 706 in [this thread]("http://ubuntuforums.org/showthread.php?p=11354601").

---

