---
title: "Software Crashes"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by icairus on 2007-12-04
I've been having software crash on me fairly frequently - using 64bit Gutsy Gibbon on a laptop - AMD Turion x2..
There are all sorts of explanations for why this may happen, and although I'd rather it didn't, it is something I'm certainly at peace with.  Software crashes happen.

However, what does bother me is that almost every time after some sort of crash, the screen... doesn't quite fix itself.  In front of everything there is some bit of an artifact of that window.  It remains in front of all but the occasional dialogue screen, blocking segment of my screen.
I'd like to know if anyone has any suggestions for such a problem, besides logging out, as I'd prefer to be able to continue to use other software I'm running at that time.

---

### Post by khurrum1990 on 2007-12-04
Hi, first of all software crashes should not happen. The way u describe them sounds serious. This is Linux, it shouldn't crash like this. I would suggest that u run some diagnostic scans on ur hard disk and some memory tests as well. Also re download Ubuntu 64 bit and make sure ur iso isn't corrupt. In fact I have been running Kubuntu 7.10 for a long time and never had one crash. This just shouldn't happen. For ur screen the temporary solution is to reconfigure x, do this by typing:
sudo dpkg-reconfigure xserver-xorg
Also try Kubuntu 64 bit cause maybe gnome doesn't work well on ur system.
Good Luck!

---

### Post by Nano Geek on 2007-12-04
What kind of graphics-card do you have?

---

### Post by icairus on 2007-12-04
The primary piece of software that crashes is gnash.  Which is playing bits of Flash it, in theory, isn't capable of doing in the first place.  So, I'm not going to get too upset about things going wrong occasionally.

Video card is ATI Radeon Xpress 1100, using the restricted ATI driver.  I have not actively attempted to update it.

In reference to the sort of crashes, it's unresponsive software, not a system crash.  The problem is that the software is leaving things somehow on the screen, that remains where it is, in front.

---

### Post by Nano Geek on 2007-12-04
You could try using plain Flash player. GNASH is still a tad unstable at the moment.

---

