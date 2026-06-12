---
title: "Intermittent sleep mode"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by T-Slyce on 2006-11-13
First off, I'm a seasoned Windows veteran but pretty much a noob to Linux.  I've heard good things about Ubuntu and was quite impressed with the friendliness and professionalism in the forums here so I decided to try out the Dapper Drake release (as suggested for newbies in the sticky topics above).  I've got lots of questions so you'll probably see me around here for a while ;) 

First up I want to try out the live CD (very cool!) to see if I can get everything running.  I burned the CD and booted up no problem.  When the OS starts, though, it intermittently drops into sleep mode and the mouse flies around the screen with wild abandon.  Not sure what the cause is but it's obviously a bummer.

Oddly enough I had the exact same problem with Knoppix 5.01 a while back when I was trying that out (before I knew about Ubuntu ;) )  I was able to solve it by typing "noapm" before booting, turning off some power management feature my laptop (Pentium III 1.1 GHz w/ 512 MB RAM) can't handle.  I tried it with Ubuntu to no avail, did a search on the forums and didn't turn anything up, and decided to jump into the community and post the problem.  

Any ideas?  If nothing else, it would probably be a good thread if someone could simply list the commands one can type in at loading and explain their functions.  Or maybe just point me and any other curious readers in the right direction?

---

### Post by T-Slyce on 2006-11-13
Well I just found a thread that suggested I try typing the following at bootup:

live acpi=off noapic nolapic

No idea what all that was but I tried it... and nothing worked.  The laptop still goes into sleep mode about every three minutes after loading the GUI.  Anybody out there have any ideas?  It's crazyness here!

---

