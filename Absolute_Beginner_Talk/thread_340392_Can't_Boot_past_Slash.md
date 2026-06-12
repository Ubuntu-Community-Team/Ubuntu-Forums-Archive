---
title: "Can't Boot past Slash"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by LuckysCharms on 2007-01-17
Hey, I'm new to linux and I started with a live CD of Knoppix This afternoon. After thirty mins just to get it past the loading screen using a failsafe command i find out i can't even use the mouse. 
So I find Ubuntu and figure after reading the page i'll give it a shot. CD loads, but I can't get past the Splash screen that say "ubuntu" and has a progress bar under it. once the bar scrolls across it stops responding. here are my specs;

AMD Ath 64bit 3500
200+gigs HD
1gig RAM
Flat screen Monitor
USB Mouse
ATI Graphics Card with Radeon Express On-Board

Any help you can give me would be great, and anything conflicts I might run into that you could help me with would be great. Thank you

---

### Post by wpshooter on 2007-01-17
Are you using the DESKTOP (live) CD or the ALTERNATE CD ?

Have you checked the integrity of your CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

Have you ran the memtest found on that same menu ?

Have you tried the safe video mode parameter ?

Did you burn your CD at 4X or less ?

---

### Post by LuckysCharms on 2007-01-17
Memory tested out good no errors, I'm not running the Alternative disk, I burned at 4x, and I tried the safe mode option no luck.. oh and when I tried testing the CD it did what I described earlier. 
However I put it in the drive while I was in Windows and it loaded fine. I even installed a few Open Source programs off the disk without fail. I'd Really Love to get this working. :-k

---

### Post by Tomosaur on 2007-01-17
Very strange behaviour. My guess would have been something to do with X (the graphical side of things), but since you can't boot even in safe mode (which is command line only), it's ruled that out. I notice you're using a 64 bit processor. Which version of Ubuntu are you using? 64 bit support is still a little sketchy, I'd recommend you try the 32 bit version for now, just to rule that out. If it works, you may aswell stick with 32 bit until the 64 bit support is better.

---

### Post by ljpm on 2007-01-17
> **LuckysCharms said:**
> Hey, I'm new to linux and I started with a live CD of Knoppix This afternoon. After thirty mins just to get it past the loading screen using a failsafe command i find out i can't even use the mouse. 
So I find Ubuntu and figure after reading the page i'll give it a shot. CD loads, but I can't get past the Splash screen that say "ubuntu" and has a progress bar under it. once the bar scrolls across it stops responding. here are my specs;

AMD Ath 64bit 3500
200+gigs HD
1gig RAM
Flat screen Monitor
USB Mouse
ATI Graphics Card with Radeon Express On-Board

Any help you can give me would be great, and anything conflicts I might run into that you could help me with would be great. Thank you


That sounds pretty much like my system (Cisnet) and I also had the same problem but only with the 64 bit Ubuntu. It would start to load and get to the 3rd or 4th item then freeze.  I installed (many times now) with the 32 bit version and have had no problems.

---

