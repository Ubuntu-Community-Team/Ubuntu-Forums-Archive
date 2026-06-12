---
title: "Compiz Fusion on Intel GMA X3100"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by icelechi on 2007-11-14
Hi,
I have a computer that runs on an Intel Graphicas Media Accelerator X3100.
This has problems with Compiz-Fusion so it was black-listed in the /usr/bin/compiz file. 
I got it to run by editing the /usr/bin/compiz file but every now and then, it crashes on startup. :)
Right after I enter login info, the computer freezes :(
Is there anything I can do about this?

Thanks

---

### Post by victorgreen on 2007-11-21
Ah ha. I have an x61 (x3100gma) and the reason compiz doesnt run by default is something about intel's driver sucking in some way so the graphics was blacklisted by the compiz developers. You clearly around the work around. 

Unfortunately once you have it running compiz great (and it DOES :) ), you can play any video files when compiz is enabled. 

Anways, Im not sure what you did, but heres what I did on a clean install of 7.10 to get compiz running.

popped the following into terminal:
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager

reboot
get the compiz settings manager through synaptic
 and then go to system ==> preferences ==> appearance ==> visual effects tab and enable custom and mess with the compiz preferences to your satisfaction

---

### Post by napsy on 2007-12-28
I have the same card with compiz enabled but I can't watch any movies. Totem won't display any image and mplayer segfaults with this error:

> 
Movie-Aspect is 2.35:1 - prescaling to correct movie aspect.
VO: [xv] 640x272 => 640x272 Planar YV12 
X11 error: BadAlloc (insufficient resources for operation)?,?% 0 0 


MPlayer interrupted by signal 6 in module: vo_check_events
- MPlayer crashed. This shouldn't happen.


How can I fix this?

Greets,
Luka

---

### Post by X40nick on 2007-12-28
Well I tried everything to get the Compiz working on my laptop, with Ubuntu it just doesn't work!!! But with Opensuse 10.3 it worked out of the box.

I don't use opensuse anymore, but hopefully someone can post the necessary files. 

I don't think it will work, I hope in the next release they will fix it. I gave up on it.

Nick

---

