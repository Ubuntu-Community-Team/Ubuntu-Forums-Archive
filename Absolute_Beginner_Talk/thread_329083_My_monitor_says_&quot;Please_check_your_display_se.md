---
title: "My monitor says &quot;Please check your display settings&quot;"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by Burningsack on 2006-12-31
So I put in the my live CD, select start, and then it boots up and my monitor says "Please check your display settings" and does nothing. I tried both Breezy Badger and Edgy Eft. I also tried safe graphics mode. My Computer meets the system requirements easily. The monitor I use is a HP Pavilion MX70. I looked in the help guides and can't find anything. ](*,) ](*,) ](*,)

---

### Post by oilchangeguy on 2006-12-31
your monitor probably does not support higher than 800x600 resolution. do you have another monitor (newer) you can try?

---

### Post by Burningsack on 2006-12-31
> **oilchangeguy said:**
> your monitor probably does not support higher than 800x600 resolution. do you have another monitor (newer) you can try?It does support higher than 800x600, I'm running it on 1024x768 on windows XP.

---

### Post by Sigudian on 2006-12-31
> **Burningsack said:**
> It does support higher than 800x600, I'm running it on 1024x768 on windows XP.

do you have a monitor with auto adjust feature? if so pres it when you get the error message.

---

### Post by Burningsack on 2006-12-31
> **Sigudian said:**
> do you have a monitor with auto adjust feature? if so pres it when you get the error message.No auto adjust.

---

### Post by Sigudian on 2006-12-31
> **Burningsack said:**
> No auto adjust.

try to open the menu on your monitor and see if you can change anything for the better,

other thing you can do is to check the MD5 checksum of your cd, or you could run the "check cd for defects" option. to see if the fault is on the cd-rom's side.

---

### Post by Burningsack on 2006-12-31
> **Sigudian said:**
> try to open the menu on your monitor and see if you can change anything for the better,

other thing you can do is to check the MD5 checksum of your cd, or you could run the "check cd for defects" option. to see if the fault is on the cd-rom's side.Check CD for defects showed nothing, only Brightness and Shade on the monitor. Sorry for the trouble.

---

### Post by Sigudian on 2006-12-31
what is the model name of your monitor?

---

### Post by Burningsack on 2006-12-31
> **Sigudian said:**
> what is the model name of your monitor?HP pavilion MX70. It's old, but functional. I

---

### Post by Sigudian on 2006-12-31
I would strongly recommend that you get a cheep LCD monitor, its not that expencive and it much easier on your eyes, never the less im sure that ubuntu can run on your monitor, but i dont know how to fix your problem.

---

### Post by steve.horsley on 2007-01-01
You just might get somewhere by unplugging the monitor while the system boots and the GUI gets started - it might fall back to a safe 640x480. This is not too hard a problem to fix on a real install, but I don't know how easily you can fix the live CD.

---

### Post by Burningsack on 2007-01-01
Thanks for the help. I might be getting a new monitor soon.

---

### Post by Ptero-4 on 2007-06-19
AFAIK. The MX70 can do up to 1280x1024, it may be your GPU what's failing there.

---

### Post by Pelonchas on 2007-12-03
Yes it works on higher resolutions. I got the same monitor. It works perfect until you get another video card modules. Screens and Graphics, get the syncs but not the resolutions modes of this monitor by doing auto, so you have to write them directly in /etc/X11/xorg.conf.

---

