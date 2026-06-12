---
title: "first time install : error loading OS?"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by woodsonoversoul on 2007-03-28
First time installing Ubuntu. Worked fine off live cds, now, after I've installed it it won't boot. I get a "error loading operating system" message. Any help?

---

### Post by oilchangeguy on 2007-03-28
a quick search of error loading operating system leads me to belive the computer is searching for windows. please explain how you installed ubuntu.

---

### Post by GMachine_24 on 2007-03-28
also which version of Ubuntu are you using and what is your hard ware configuration... the more info the better

---

### Post by woodsonoversoul on 2007-03-28
I installed ver 5.04 from a installation disk from ubuntu on to two separate hard drives.

---

### Post by woodsonoversoul on 2007-03-28
Not sure my hardware info is that revalent anymore.  I was messing around with the hard drives (unplugging them etc.) and saw a spark and heard a pop. Now my computer won't turn on.

---

### Post by NicoleM on 2007-03-28
you haven't given much information to go on but sparks and pops are NOT good news.  I really hope you weren't messing around inside your system while anythign was plugged in were you?

although some consider them overkill, anti-static wrist straps are never a bad investment either when you're messing around with stuff.

can you boot off a live CD and see if your drives are still recognized at all?

---

### Post by oilchangeguy on 2007-03-28
Nicole, i doubt he can test the live cd, or anything else. if you'll notice in his last post he indicates the computer will not turn on.

---

### Post by NicoleM on 2007-03-28
whoops! learn2read 101 for me i guess.

hardware is my specialty...i saw snap crackle and pop of hardware and immediately started typing haha.

how many watts was your power supply?  was it possible the psu was either overloaded, overheated or shorted out?

your devices *might* be salvageable...if you have another computer or a daring friend you should try the drives one by one in another system to see how bad the damage really is.

---

### Post by woodsonoversoul on 2007-03-28
Hey, just got back from work and got my system to power up; although with the same error message. It looks like it's reading all my devices. My guess was that it was having a problem deciding on how to boot. I'm running an ABIT motherboard with an Intel chip (I'm guessing a pentium 4?) If that helps...

---

### Post by h0ax on 2007-03-28
Have you specified which harddrive you want to boot first, and did you install a bootloader (GRUB, for example) on the primary hard drive?

Make sure you unplug your computer and wait a few seconds so the capacitors in the powersupply / on the motherboard lose their charge, THEN start fiddling with things.

---

### Post by woodsonoversoul on 2007-03-28
wouldn't that be specified in my BIOS? and I did a full install into both hard drives

---

### Post by h0ax on 2007-03-30
It would be specified in your BIOS which hard drive is booting first, but I can't think of a reason why you would install it on both drives... ?

Install it on the primary drive, then format the second one as storage ?

---

