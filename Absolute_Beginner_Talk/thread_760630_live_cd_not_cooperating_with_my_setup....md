---
title: "live cd not cooperating with my setup..."
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by samckinn on 2008-04-20
I am trying to use the live cd to play around with ubuntu.  I believe my cd is good(the check sum of my iso image on my hard drive matches expected value).  I also believe i have bios configured correctly.

The install screen comes up and i can navigate around that screen using the keyboard, but as soon as i select an option everything freezes.  The install screen is still displayed.  The cd rom drives spins up intermittenly.  And if left long enough the system just reboots.

hardware connected to my crappy dell dimension 4600:

NVIDIA GeForce 6600 GT 
SAMSUNG CD-R/RW SW-248F 
SAMSUNG DVD-ROM SD-616T  ( have tried install from both cd and dvd drvies)
Broadcom NetXtreme Gigabit Ethernet
Intel PRO/100 VE Network Connection (legacy)
1 Gig of RAM
Creative SB Live!
USB keyboard/mouse

Now i assume it is a problem with my hardware, but i can't find anything in the forums to lead me in the debug.  Plus, I don't any error information with the symptom above.  I can get to the root prompt using F1, but don't know what to try...

Any help would be appreciated...thanks in advance!

---

### Post by mick8985 on 2008-04-20
Before you boot hit (something along the lines of) edit boot options f6 I can't remember exactly, and remove "quiet splash" and see if it gives you any clues.

---

### Post by Vermind on 2008-04-20
Hello,
on my system I had to press F6 and also add ```
ide=nodma 
```. My cdrom does not read the Ubuntu livecd properly otherwise.

---

### Post by samckinn on 2008-04-20
neither combination of the quite spash (removal) or the nodma option worked... I also tried it with both the dvd drive and the cd drive(unfortunately, they are both the same vendor so that doesn't say much).   When i do select an install from the install menu it sill freezes.  I guess i didn't note this the first time, but the cdrom doesn't spin upon install selection.  If it does spin at all it is after some delay.  Maybe this indicates the cdrom being the problem...(however unlikely)

---

