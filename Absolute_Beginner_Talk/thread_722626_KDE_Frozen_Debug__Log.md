---
title: "KDE Frozen: Debug?  Log?"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by ackey on 2008-03-12
Recently my beautiful System76 laptop has been completely freezing on me fairly often (perhaps once per 6 hours of use).  I've checked the log reports that usually have information on crashes, but since this is a true freeze - must power off by holding the button down - I suspect I won't find anything helpful.  I'm using KDE 3/gutsy.

I've had the lappy since August and this seems to be a "new" problem.  A few times in a row (ie, I noticed a pattern) both Rythmbox and electricsheep (screensaver) were running.  I changed the screensaver, hoping that would help.  It just froze when rhythmbox wasn't even running, so I'm out of ideas.  I noted that the external monitor the laptop was plugged into had the power light oscillating between on and standby.  I don't know what that means or if it is helpful.

I'm looking for ideas on how to debug this.  I don't think I am running anything particularly unstable or unusual.  I believe the open programs during the last freeze were firefox, evolution, and terminal.  I would have had 2 sshfs and 1 ssh connections open.

Any advice on what to try is appreciated.  I'm about ready to give up on KDE - I don't think I had these problems in gnome and I'm also having a mouse problem I didn't have in gnome. 

Sorry for asking such a nebulous question!

---

### Post by neurostu on 2008-03-12
Did you install any software before the freezing started?  What about system changes?

Have you tried running top or htop to see if there are any renegade processes that might be causing the freeze?

---

### Post by ackey on 2008-03-12
Since the freezing has been going on for some time, I'm not sure if it has been slowly ramping up in frequency or if it "suddenly" started.  It *may* have started when I switched from Gnome to KDE.  The only other change (and I believe the freezing was happening beforehand) was adding ec_intr=0 as a boot parameter to get the power management working properly.

The worst culprits in top tend to be beagled and its helper.  The freezing *tends* to be when I'm not particularly doing anything, perhaps other than playing music.

---

### Post by neurostu on 2008-03-12
When you switch back to Gnome you does the freezing stop?

---

### Post by ackey on 2008-03-13
I'm running in Gnome now to see if the problem resurfaces.  It will probably take a few days for me to be convinced that it was KDE specific.

If it is a KDE problem (which I am willing to believe) is there any solution other than switching back to Gnome?  I know System76 tests the laptops with Gnome, so possibly KDE just doesn't play nice with the hardware.

---

