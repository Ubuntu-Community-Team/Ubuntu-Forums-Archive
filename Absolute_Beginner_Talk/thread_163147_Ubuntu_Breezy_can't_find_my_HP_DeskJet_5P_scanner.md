---
title: "Ubuntu Breezy can't find my HP DeskJet 5P scanner"
date: 2006-04-20
forum: Absolute Beginner Talk
---

### Post by SeeWhy on 2006-04-20
I'm abot a new to Linux as one can be, so please forgive my ignorance. I've just installed Ubuntu Breezy and find that it will not identify my HP 5P scanner. 

I did a search on the Forum and the nearest thing to my problem I located was a thread saying that the HP 5P's SCUSI card had caused the install to stall. I did not have any problems installing, but if someone else has had problems with an HP 5P on installation, I suspect my problem may well be the scanner's SCUSI card.

As mentioned already, I'm atotal newbie to Linux so please couch any replies as to a total Windows-centric idiot

---

### Post by SeeWhy on 2006-04-21
Wow! 15 hours since I posted and my post is buried on page 5! I had no idea the forum was so active.

I still have the problem with the HP 5P, and to clarify, the Device Manager doesn't find it (my WindowsXP setup - on a separate HD, not a dual boot - does, so it's "there"). 

I'd also like to know what to do to get my second computer to recognise my printer. I was able to set up the printer on my primary computer, but I haven't been able to get the printer to run from the second computer.

---

### Post by patrick295767 on 2006-04-21
Probably, you need to configure the driver to use the correct firmware for your scanner. Look here for more info: [http://snapscan.sourceforge.net/](http://snapscan.sourceforge.net/)

---

### Post by Sef on 2006-04-21
From the terminal, type this:

sudo apt-get install libsane-extras

that was how I got my scanner working (HP PSC 1610)

If not, then try this:

Your scanner is listed as complete on the sane-project, so the drivers are there.

[http://www.sane-project.org/sane-mfgs.html#Z-HEWLETT-PACKARD]("http://www.sane-project.org/sane-mfgs.html#Z-HEWLETT-PACKARD")

---

