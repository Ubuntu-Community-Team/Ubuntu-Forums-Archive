---
title: "GNOME fails to launch"
date: 2007-10-18
forum: Apple PPC Users
---

### Post by colinhayes on 2007-10-18
Apparently something has broken since the last time I booted into Ubuntu.

I can no longer fully boot up.  if I kill the splash screen, it gets to "Starting GNOME Display Manager..." and then goes black.  Does the same thing with the new 7.10 cd.

any idea what's going on?

---

### Post by colinhayes on 2007-10-19
okay, I just tried to 7.04CD in live mode and after trying to start GNOME it came up with a screen informing me that X is not configured correctly.  

I am at a loss here as nothing has changed with my computer (except for a hard drive with OSX on it) since Ubuntu last ran correctly.

---

### Post by colinhayes on 2007-10-22
so I installed kubuntu 6.06.1 and it worked until I went into display settings and specified the graphics card from ati generic to ati radeon (fglrx), so it seems that somehow ubuntu is choosing the wrong driver for my ati radeon 9600 xt card.

so I guess my question is now, how to I fix this?  Really, I would like to get Ubuntu 7.10 or 7.04 working on here again and NOT kubuntu...

---

### Post by Knoeki on 2007-10-22
hrm, I was about to suggest a different windowmanager, but it appears you prefer Gnome... I think this is a matter of editing the xorg.conf file... I don't remember exactly where it's located though... not sure if it's the right fix for the problem either.

---

### Post by BladeMelbourne on 2007-10-22
/etc/X11/xorg.conf

---

### Post by Knoeki on 2007-10-22
ah yes, that's it ;_) I remember now.. I once configged it wrong, so X would crash after 5 minutes.. I've never done command line work this efficient as then ;_)

---

### Post by colinhayes on 2007-10-25
I've tinkered with it a lot and cannot get it to work.  I have copied the xorg.conf file from the live cd to the harddrive and it still doesn't work.

pics of the X server output are here:
[http://adelie.spd.louisville.edu/~cmhaye02/1.jpg](http://adelie.spd.louisville.edu/~cmhaye02/1.jpg)
[http://adelie.spd.louisville.edu/~cmhaye02/2.jpg](http://adelie.spd.louisville.edu/~cmhaye02/2.jpg)

---

### Post by colinhayes on 2007-11-04
okay.

so I installed 6.10 without problems.  I updated everything, no problems.  I run a distribution upgrade to 7.04, problems.

same X server output as before, but here's a readable image as I recently discovered the macro button on my camera:
[http://adelie.spd.louisville.edu/~cmhaye02/xoutput.jpg](http://adelie.spd.louisville.edu/~cmhaye02/xoutput.jpg)

I had backed up my xorg.conf file when everything worked and loaded that in place of what the distribution upgrade created (did it create a new one?) and it gave me the same error.

do I need a different version of the radeon driver?  How can I load in an old one without getting version mismatches? (I've tried this before and get version mismatch errors)

---

### Post by ssam on 2007-11-04
could it be a date problem? have a look at [https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

---

### Post by colinhayes on 2007-11-04
no, it's X... I would change the post title if I could.

the date bug: "The system boots fine, and gets to the gdm login screen. The user types name and password and presses enter. The screen goes and the user is left on a brown screen."

check out the screenshot I took of the X output... it's some kind of problem with memory allocation with the radeon driver (I think)

edit:  should I try installing the fglrx driver?

---

### Post by BladeMelbourne on 2007-11-04
Hi Colin,

This is from my /var/log/Xorg.0.log:
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 4.2.0
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 1.0
(WW) ****INVALID IO ALLOCATION**** b: 0xf0000400 e: 0xf00004ff correcting^G

The invalid IO allocation does not result in an unusable display IMHO.

Can you read this thread: [http://ubuntuforums.org/showthread.php?t=579487](http://ubuntuforums.org/showthread.php?t=579487)

I'm interested to know what version of xserver-xorg-video-ati you have installed. (I'm using 6.6.3-2 on Gutsy).

The backtrace in one of your screenshots mentions Int10. You could possibly try a line like the following in /etc/X11/xorg.conf inside the device section (comment out any other line with NoInt10 in it).
Option                 "NoInt10"                               "True"

HTH.

---

### Post by colinhayes on 2007-11-05
my guess is that I now have: (6.6.3-2ubuntu6)
[http://packages.ubuntu.com/feisty/x11/xserver-xorg-video-ati](http://packages.ubuntu.com/feisty/x11/xserver-xorg-video-ati)
and that I used to run: (6.6.2-0ubuntu4)
[http://packages.ubuntu.com/edgy/x11/xserver-xorg-video-ati](http://packages.ubuntu.com/edgy/x11/xserver-xorg-video-ati)

I had clean installs on both, so it shouldn't have changed, unless package updates after a clean 6.10 insrtall changed that package from 6.6.2 to 6.6.3

I noticed an xserver package being upgraded, but not that one.  something like that probably would have caught my attention. 


Maybe I'll try what you suggested tomorrow.

---

### Post by colinhayes on 2007-11-05
> **BladeMelbourne said:**
> You could possibly try a line like the following in /etc/X11/xorg.conf inside the device section (comment out any other line with NoInt10 in it).
Option                 "NoInt10"                               "True"


Since I am writing this from Ubuntu, it looks like your little trick worked.  thanks!

also... I'm tempted to try upgrading again.  I know you mentioned that you had to use feisty's ati driver, but did you run into any other problems?  Also, what's your setup like?  I have a dual G5 2.0GHz w/ radeon 9600 XT

---

