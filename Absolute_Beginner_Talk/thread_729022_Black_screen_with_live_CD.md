---
title: "Black screen with live CD"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by Papa-san on 2008-03-19
I'm trying to diagnose a winXP machine for a friend. I popped in a Gutsy CD that I received through the mail from Canonical. (It's a good copy)

When I let it boot to run Live, I end up with a black screen, and it acts like it is done loading. He has a NVIDIA GeForce 6200 display adapter. I don't know if this is the problem or not. 

If you need system specs, I'll need to know how to pull them off a windows machine...

I've tried running it three times, to no avail. 

He is not opposed to having me install Ubuntu on his system, but if I can't see it, it may not be the best choice! I have already backed up his Outlook emails, Netscape bookmarks, word documents and his Quicken and Turbo-tax information, so if I flub it, it's OK (as long as we can get the above mentioned things working and imported in Ubuntu...

---

### Post by bred on 2008-03-19
boot in safety mode from liveCD

---

### Post by caravel on 2008-03-19
What were you trying to diagnose that made you try to boot from the Ubuntu disk?  Does your friend want to switch to Ubuntu or were you just booting into Ununtu to try and diagnose some kind of hardware problem?  That's the point I'm not clear on.  If it's blacking out on boot up it could be related to the graphics card.  My 7300GT graphics card does the same in Ubuntu, the solution was to *enable* AGP fast writes and this fixed it (strangely enough).

---

### Post by djbsteart1 on 2008-03-19
For system specs you can try system info, under accessories i think. Or just run, dxdiag.exe which gives system info aswell. If you have another distro kicking about you could just try it, or get a copy of damn small and see if that will boot.

---

### Post by Houli on 2008-03-19
Have you checked the disc for defects? That could be the problem.

---

### Post by Saint Angeles on 2008-03-19
when i ran gutsy on my home computer, i would always need to push ctrl+alt+f1 during startup, after the screen goes black.

after i got used to it, i upgraded to hardy and i dont have that problem anymore.

---

### Post by Papa-san on 2008-03-19
Thanks for the replies! 

The computer was randomly locking up and/ or shutting down on it's own. In the last two days, from what he is describing, the monitor seems to lose it's incoming signal an instant before it turns off...

I am just trying to use Ubuntu for diagnostics so far. He saidhe doesn't care if I install it, he just needs to be able to surf and do e-mail. (Occaisional kids games, but I'll get those working...)

He has so much garbage on here! No wonder it crashes!  I'm going to try going live again in the safe graphics mode, and if that doesn't work, I'll try the ctrl+alt+f1 thing...

---

### Post by Papa-san on 2008-03-19
It came up OK in the safe graphics mode.

Any suggestions to give the hardware a workout? Or has anyone thought of any specific things to check?

I ran glxgears and it said I was getting about 210 fps, but the gears were kinda twitching back and forth. I opened another glxgears and it popped me to the login splash screen...  Logged in OK

---

