---
title: "WiFi frustrations"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by pw2buz on 2008-01-23
I have spent hours trying to get wireless to work on my Thinkpad T41 and Feisty Fawn (7.04), after installing Ubuntu to the hard disk.  Network Manager doesn't work, ndiswrapper doesn't work, I couldn't get Linuxan's product to work.  For something that I hoped would be fun, this isn't.  :(

At least ethernet works.

Yet when I pop in the 7.04 CD and run Ubuntu from the CD (LiveCD) it works just fine!

Any thoughts from you more experienced users before I try another Linux distribution (considering PCLinuxOS 2007) or just kiss Linux goodbye and stick with terrible, expensive, Windows XP, which works just fine.

Pw2buz

---

### Post by yourpalal on 2008-01-24
make sure you have your restricted drivers enabled if it is working on the disc this could be it go to system-->administration-->restricted drivers if network manager isn't working perhaps you should just try a fresh install.. something may have gone wrong

when you are running livecd right click on the network manager applet then go to connection information then read what it says for driver...
upon returning to your hard drive installation check restricted drivers as well as synaptic for anything you can find about said driver.

on an only semi-related note, there is something to be said for 7.10, in fact i reccomend it... okay i guess that doesn't quite qualify as semi-related

---

### Post by nick_h on 2008-01-24
This will get confusing if you open other threads - [link](http://ubuntuforums.org/showthread.php?t=676626).

---

### Post by Michl on 2008-01-24
It took me a while to figure out how to work network manager because
you need to edit /etc/network/interfaces to get the manager to work.
There is documentation on this on ubuntu.com or search here.  It isn't
very difficult, though.


BUT before I figured that out, I ignored the applets and connected
with wifi-radar.  FInd it on synaptic -- you need to have universe
repositories enabled.  Setting-up and connecting with wifi is
easy.

---

