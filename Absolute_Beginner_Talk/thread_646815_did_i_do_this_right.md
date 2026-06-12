---
title: "did i do this right?"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by brandon333 on 2007-12-21
ok i partitioned my macs drive in 3 partitions giving ubuntu around 30 and the swap like 8gig, please review this picture I have attached and let me know if i did this right please

---

### Post by AndyCooll on 2007-12-21
Hmmm ...that's fine, though a 7/8gb swap partition seems overkill to me. I would have thought a 2gb max would have been more than enough, though I'm happy to defer to experts on this sort thing if they suggest otherwise.

:cool:

---

### Post by bapoumba on 2007-12-21
It's fine. The only thing I do differently (aside from the swap, usually RAMx2, 1Go max) is set up a separated /home partition.
This way, when a new version is released, I perform a clean reinstall from the cd, rather than an online upgrade, and all the settings in /home are kept.

---

### Post by brandon333 on 2007-12-21
well everything seems ok except 2 big issues:

1) when I turn mac on it just boots ubuntu, mac is even thought of, lol, how can i fix this?

2)screen is kicked to the left and cut off at top a bit, works at lower rez, am I stuck with a lower rez?


also on the desktop only my external hard drive option shows up, shouldnt there be more things such as the actual ubuntu drive?

and lastly for now anyhow can I go into partition editor and make the swap smaller, I made it 8 gig, to big i know.

---

### Post by chris200x9 on 2007-12-21
1) hold option while it boots

also system prefrences and change the start up disk if you want mac os x to start as default.


as for smaller swap probably resize it of the liveCD

that's al I can be of help with

---

### Post by AndyCooll on 2007-12-22
> 1) when I turn mac on it just boots ubuntu, mac is even thought of, lol, how can i fix this?
As mentioned in the reply above. You will probably need to edit the grub menu and change the default OS boot. You'll need to do a search for more information about this. 

> 2)screen is kicked to the left and cut off at top a bit, works at lower rez, am I stuck with a lower rez?
No you are not stuck with lower rez settings. You may need to manually change these. System > Administration > Screens and Graphics is the place to start.

> also on the desktop only my external hard drive option shows up, shouldnt there be more things such as the actual ubuntu drive?
This is correct. Ubuntu's preferred option is a minimal desktop with only plugin media displaying. You access your folders using "Places". 

> and lastly for now anyhow can I go into partition editor and make the swap smaller, I made it 8 gig, to big i know.
Yes you can use a partition editor to resize the drives. You will probably need to do this using a Live CD, e.g. GParted, as you cannot usually resize partitions while they are in use.

:cool:

---

