---
title: "widescreen won't work"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by n-f on 2007-09-23
Hi, i recently built a "Freekbox" at freegeek and installed Feisty on it.  I like the idea of Linux but so far all i have had are problems more annoying than anything i have encountered on my other two computers running xp.

First off widescreen won't work at 1650x1080, only at 1280x768 .  I tried sudo dpkg-reconfigure xserver-xorg and changed the supported resolutions, but now when it boots up i get my 1650x1050 pushed off the side of the screen at the login and it's all fuzzy as if i went above the max res, might be high refresh rate, idk.  When i get to my desktop and try to change it the screen gets big and i have to move the mouse to see the whole thing.  Right now i have it at 1280x768 which isn't as bad as before but i would still like to make it work at something closer to 1650x1080, wasn't there a  command that centered the screen automatically?   I've been looking around this forum and google and can't seem to find anything that works yet.  Oh and my monitor is a Sceptre x20wc i think, max res is 1650x1080 and 1600x1200 is not accepted.

Also on another note, how do i know if my ati driver is working?  I have a radeon 9550 256mb, and i activated some driver on 'restricted drivers' but idk if it's working because until i get cedega or make wine work(most annoying thing about linux is none of my games can run on it) i can't test it on any games or real benchmarks (glxgears fps went down to 10% after this driver was installed).  The instructor at freegeek told me ati drivers for linux suck and that i should have gotten an nvidia card, but my friend and i both went for 9550's because the best nvidia ones were GF3 ti150 & 200 and the choice was obvious.  btw i have an extra fx5200 which i could use if the ati driver situation is as bad as it seems but i would much rather have the "power" of a 9550.

Sorry if that was kinda long, thanks a lot for any help, i'm 100% sure once i get familiar with ubuntu it will be great.

---

### Post by Pumalite on 2007-09-23
Stick in your Nvidia. What good is the 'power' if ATI doesn't support Linux?.

---

### Post by skyjacker on 2007-09-23
Go to this link albertomilone.com/nvidia_scripts1.htmand read. Then go to applications, add/remove, and install Envy. I have Nvidia driver, but this is supposed to work with ATI drivers. Good luck.
Ubuntu rocks:guitar:

---

### Post by overdrank on 2007-09-23
> **n-f said:**
> Hi, i recently built a "Freekbox" at freegeek and installed Feisty on it.  I like the idea of Linux but so far all i have had are problems more annoying than anything i have encountered on my other two computers running xp.

First off widescreen won't work at 1650x1080, only at 1280x768 .  I tried sudo dpkg-reconfigure xserver-xorg and changed the supported resolutions, but now when it boots up i get my 1650x1050 pushed off the side of the screen at the login and it's all fuzzy as if i went above the max res, might be high refresh rate, idk.  When i get to my desktop and try to change it the screen gets big and i have to move the mouse to see the whole thing.  Right now i have it at 1280x768 which isn't as bad as before but i would still like to make it work at something closer to 1650x1080, wasn't there a  command that centered the screen automatically?   I've been looking around this forum and google and can't seem to find anything that works yet.  Oh and my monitor is a Sceptre x20wc i think, max res is 1650x1080 and 1600x1200 is not accepted.

Also on another note, how do i know if my ati driver is working?  I have a radeon 9550 256mb, and i activated some driver on 'restricted drivers' but idk if it's working because until i get cedega or make wine work(most annoying thing about linux is none of my games can run on it) i can't test it on any games or real benchmarks (glxgears fps went down to 10% after this driver was installed).  The instructor at freegeek told me ati drivers for linux suck and that i should have gotten an nvidia card, but my friend and i both went for 9550's because the best nvidia ones were GF3 ti150 & 200 and the choice was obvious.  btw i have an extra fx5200 which i could use if the ati driver situation is as bad as it seems but i would much rather have the "power" of a 9550.

Sorry if that was kinda long, thanks a lot for any help, i'm 100% sure once i get familiar with ubuntu it will be great.

If you would like to try this "how to" it has work well for me on the ATI 9200, and 9600.
[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)
Good luck!

---

### Post by n-f on 2007-09-25
Alright, thanks guys!

---

