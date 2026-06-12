---
title: "Dual Monitor Problem Fixed"
date: 2008-11-07
forum: Apple Hardware Users
---

### Post by Riptide614 on 2008-11-07
I have a Mac Pro (2.8 GHz Dual Quad-Core Xeon) with an ATI Radeon HD 2600XT graphics card driving two Apple 20" Cinema Displays.

After installing the envyNG package and having it install the ATI drive, both monitors 'worked', but instead of a large, extended desktop (big desktop), both monitors were mirroring the same desktop (mirrored displays).

I tried running ATI Catalyst Control Center ('sudo amdcccle' from a term window command prompt) but it was returning the following error:

"Parse error on line 32 of section Module in file /etc/X11/xorg.conf  "Disable" is not a valid keyword in this section."

Trying to run 'sudo aticonfig' also returned the same error.

I spent some extensive time googling for a solution and finally just decided to try fixing it on my own.  For me, it was a *really* simple fix.  All I had to do was comment out line 32 in /etc/X11/xorg.conf

**Note: The line you need to edit may not be line #32 as it is in my xorg.conf file.  Just search for the line below if yours isn't line 32:**

My line initially read: Disable	"dri2"

and I just changed it to: #	Disable	"dri2"

Then saved /etc/X11/xorg.conf file.

I was then able to run ATI Catalyst Config by typing into a term window: sudo amdcccle

That brought up the ATI Catalyst Config Control Center and I was then able to set my dual displays to an extended desktop.

I hope this helps out other Mac and non Mac Ubuntu users. Any questions, just ask and I'll try and help the best I can.

Thanks for a great Linux distro Ubuntu gang,

- Rip

---

