---
title: "iBook G4 Wireless"
date: 2007-01-19
forum: Apple PPC Users
---

### Post by itsjamila86 on 2007-01-19
I have a late 2004 Apple iBook G4 1.2 GHz.  I'm running Ubuntu 6.10 Edgy with a GNOME frontend and Network Manager.  I have AirPort wireless set up as device "eth1" and device manager sees that I have the card, but I cannot connect to any wireless networks.  I can choose wired connection and connect that way however.  Please help.

---

### Post by quizno50 on 2007-04-04
There is a driver out there for the Apple Airport Extreme card, hence why you can see eth1. The trick is getting the firmware on it. You'll need to use the bcm43xx-fwcutter program to 'cut' out the firmware from Apple's driver... If you look around on the forums or google you can find some instructions on how to do this...

---

### Post by admiralbaty on 2007-04-05
These may be silly questions.

I'm running Ubuntu on a partition of my PowerBook G4, and I've tried setting up my Airport Extreme card according to this thread:

[http://ubuntuforums.org/showthread.php?t=142727](http://ubuntuforums.org/showthread.php?t=142727)

I had to find the AppleAirPort2 file somewhere else, and it was named something else, and I adjusted the instructions accordingly, but I couldn't connect, and I ended up disabling my ethernet connection altogether.  No matter what I tried, I couldn't get on the internet, even plugged in, even after rebooting.

So my questions are these:

1.)  How do I fix my ethernet card so that I don't have to keep rebooting to look for help?
2.)  Did I do something wrong (that anyone can tell) following those instructions? SLASH How do I effing make my Airport Extreme card work with Ubuntu?
3.)  Does fwcutter permanently remove the Apple firmware?  If I succeed, will my Airport Card still work when I boot up OS X?
4.)  What is the ESSID?  Is that a name?  If I call it "linksys" will it find that network?  Or do I need like an IP address or something?

I should mention that I don't have any problems when I boot up OS X, only on the Linux side of things.

I'm brand new to Linux and Ubuntu and all.  I just want to learn!

Many thanks.

---

