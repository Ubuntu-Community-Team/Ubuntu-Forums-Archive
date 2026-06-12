---
title: "Big PROBLEM with the windows (Not Microsoft Windows)"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by VoXoM on 2008-03-03
Hey, at the top right corner of **every** window in gutsy gibbon, the X has disapeared. Along with the _ and the square to maximize the windows. Please help? I tried installing Firefox 3 beta yesterday and enabled the backports in synaptic. Then I got like 9 new updates for different programs, and I remember some being for Compiz if that can help... Upon rebooting, the X and the other stuff had disapeared like mentionned above.

Thanks for the help.

---

### Post by Cypher on 2008-03-03
You're missing the Emerald decoration for the windows. Search for that and you'll find the fix..

---

### Post by sailor2001 on 2008-03-03
happens sometimes with compiz... to get back to normal:  alt/f2 and type  metacity --replace

---

### Post by VoXoM on 2008-03-03
> **Cypher said:**
> You're missing the Emerald decoration for the windows. Search for that and you'll find the fix..

That worked, except that it seems like a weird style. It's red instead of being orange like the default ubuntu theme. Oh well the blinking thing is kinda cool tho. Thanks.

---

### Post by ajgreeny on 2008-03-03
I have never used emerald with compiz-fusion as almost everyone else seems to do.  When I first started I thought it was a dependency of compiz because everyone seemed to mention and use it, but I simply don't find it necessary to install or use it to get the look I want.  Am I just lucky or am I missing out on something very special that emerald imparts to compiz?

---

### Post by SunnyRabbiera on 2008-03-03
sometimes its best to leave desktop effects off, as sometimes compiz has hiccups.

---

### Post by Duck2006 on 2008-03-03
> **SunnyRabbiera said:**
> sometimes its best to leave desktop effects off, as sometimes compiz has hiccups.

+1

---

### Post by Znort_Ubern00b on 2008-03-03
type this into a terminal window...

sudo nvidia-xconfig --add-argb-glx-visuals -d 24
 **(that is assuming you have an nvidia card)**

you should then see the minimise/maximise and close buttons...

---

