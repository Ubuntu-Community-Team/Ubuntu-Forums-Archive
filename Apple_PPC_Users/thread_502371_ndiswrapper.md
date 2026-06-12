---
title: "ndiswrapper"
date: 2007-07-16
forum: Apple PPC Users
---

### Post by ajmctaggart on 2007-07-16
Hey everyone, 

I'm getting a Powerbook Pismo up and running on Feisty.  Everything is going pretty well, except for ndiswrapper...

I am using a buffalo wifi card, its the 4318 chipset, but before I even get to that...

WHERE THE HELL IS THE NDISWRAPPER?

Is it because I am using a PPC? I have never had this much trouble installing a program in ubuntu...

Anyone know the answer, is it even possible?
Downloaded a .deb of 1.38...it said it installed but it doesn't respond to ndiswrapper commands at the terminal, says it isn't installed...

Anyone....

Thanks, ajm

---

### Post by RHTopics on 2007-07-16
ndiswrapper is designed to work with x86 type architecture not PPC. 

The drivers you would be trying to wrap with ndiswrapper would have to be from a Windows XP environment and that binary code will not work on a PPC architecture.

---

### Post by ajmctaggart on 2007-07-16
Thanks RH, 

I figured as much...when I stopped and thought about the very definition of ndiswrapper, I didn't think there would be an answer...


As far as THIS wifi card goes, do I need to be using an atheros based card?  I suppose that fw-cutter would work, but I'm going for "G" not "B"

Thanks, 
ajm

---

### Post by stmiller on 2007-07-16
The Orinoco / Prism2 based cards work well in Linux. I dislike the current state of wireless and Linux, also. I wish manufacturers would write Linux drivers for their own hardware...

---

