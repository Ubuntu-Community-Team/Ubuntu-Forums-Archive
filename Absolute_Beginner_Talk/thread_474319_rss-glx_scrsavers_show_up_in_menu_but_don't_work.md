---
title: "rss-glx scrsavers show up in menu but don't work"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by Blowfly on 2007-06-14
I've installed the package rss-glx (The Walsh 3-D savers).

The screensavers show up in name only in the screensaver but don't work. Ironically, before I did my 2nd or 3rd OS reinstall, these were working at one point.

Can anyone help me negotiate the cryptic Ubuntu maze to find the correct folder and correct config file to do this ridiculously simple thing, because it's been 2 hours and my "playing with software" time has been far exceeded. I did read the doc file, but it gave some really unhelpful info to add to a blank .xscreensaver file, and that of course did nothing.

Also, is it possible to rename critical directories and folders with names that actually have something to do with their function, or will my system implode?

Thanks in advance, sorry about the cynicism born of frustration...:p

SOLUTION: When using KDE, the [COLOR="Red"]kscreensaver-xsavers[/COLOR] hooks are necessary to link the screensavers with the OS. Less bitchin' and more competence, Blowfly! Thanks for the reply, Freebird..:)

---

### Post by freebird54 on 2007-06-15
Just a note about renaming 'critical' directories...

If they are critical to you - go ahead
if they are critical to the OS - option 2 required...

Look up the information on links (including symbolic ones) - you can call the links anything you want without affecting their real names  :)

What video are you running?  There can be problems with AIGLX screensavers trying to run with fglrx ATI drivers, for instance....

---

### Post by Blowfly on 2007-06-15
Well I've just been through the whole video driver miasma--I'm using an ATI Radeon Mobility 7500 which is competent to do 3-D renderings....but I would wager that half the forum's server is dedicated to the people trying to make that happen. Personally I've given up because what's the point in throwing one's life away chasing after a rotating cube that is more elusive to most than the Holy Grail?

Call me undedicated, lazy, what have you, I have to keep the kids fed...:)

glxgears works, though that's not the definitive confirmation to be accepted into the elite world of 3-D.

No, my problem is that the 3-D screensavers installed by the OS work fine, but the ones in rss-glx don't because they haven't been placed in the proper places and/or the proper links or config files adjusted. It was working at one point, now it's not. So I know it's possible.

But I'm burned out on it now--it's going the way of the rotating cube:

An ephemeral morsel of eye-candy dangled in front of the writhing masses as bait to suck them in to the burning chasm of Linux-hell...lol

Sorry 'bout that...:popcorn:

PS: Was kidding about the critical directory renaming. I know the chaos that ensues when the names remain unchanged, so... ;)

---

### Post by freebird54 on 2007-06-16
Actually, Beryl works pretty well with an ATI card - but you have to use 1 of 2 completely contradictory settings

1. Use fglrx drivers (origin ATI) - and set composite off, and run in an XGL session

OR

2. use the ati (radeon) drivers (origin - open source) - with composite (and another bunch of settings) on - and NOT in an XGL session.

Version 1 works well in Beryl, but some other graphic programs and games do NOT work in XGL.  Version 2 works, but is noticeably slower than version 1 - but has no other impacts on other programs.  BTW - Beryl is  MORE than eye candy - it is a better way to work.  I have 2 configurations... one for 'showing off' what it can do - and one with few effects turned on, but all workspace/program selection options turned on, including the cube :)

---

