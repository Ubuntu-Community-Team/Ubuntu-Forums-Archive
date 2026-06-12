---
title: "cdrom opens when its not supposed to"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by foxxx on 2006-09-20
hi!

my problem as mentioned above, is that my cdrom opens at any time i DONT want it to open, e.g. i put a cd in that drive and start browsing some files and suddenly *alakazaam*, its open.

i tried
"sudo dmesg | grep cdrom"
output: "cdrom: open failed"

any suggestions?

thx in advance

---

### Post by foxxx on 2006-10-04
seems to be a hardware/firmware error, installed ubuntu on a second system - and everythings fine. i think i ive got to live with it.

---

### Post by macogw on 2006-10-04
Mine does it too.  I also have hard crashes which the syslog is showing has a relationship to ATAPI and the cd rom drive.

---

### Post by pbaehr on 2006-10-04
Maybe your computer is haunted. ;)

---

### Post by foxxx on 2006-10-05
@macogw: try to take your cdrom drive from the power supply - simply disconnect it and reboot... lets see if those crashes persist

---

### Post by macogw on 2006-10-05
> **foxxx said:**
> @macogw: try to take your cdrom drive from the power supply - simply disconnect it and reboot... lets see if those crashes persist

alright I'll try that.  Someone else on here is having crash problems with the same "symptoms" (no mouse, no keyboard, yet no kernel panic) as me in [http://ubuntuforums.org/showthread.php?t=267959](http://ubuntuforums.org/showthread.php?t=267959) that thread.

---

### Post by macogw on 2006-10-05
I can't get it out. Stupid laptops.  Why must they be un-piece-able?  Desktops are much better.

I'm sending it back to Gateway.  It runs really hot, so I think that's to do with it.  I forgot to tell them about the cd drive popping open, but I did tell them about the heat, mouse/keyboard unresponsiveness, crashing stuff.

---

### Post by macogw on 2006-10-09
Well, I called Gateway and they said it sounds like a mobo problem, so I'm sending it in to have the mobo replaced.  I should've recognized that the randomly turning off speakers, crashing, cd rom drive, overheating, fan not spinning (well that'd explain some of the heat...), etc. all adds up to 1 bad motherboard, not lots of crappy little pieces.

---

### Post by foxxx on 2006-10-11
well, if you look at it this way... then its probably the mobo.
as far as it concerns me, that system i tried to install ubuntu on is now more or less 10 years old - so nevermind, just wanted to know if its a common problem :)

---

