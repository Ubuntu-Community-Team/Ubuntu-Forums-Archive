---
title: "CUPSYS Installation crashes system"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by seaside on 2006-10-26
Hi community!  
I have a problem with the mentioned above for a while now. 
When selecting "cupsys" in Synaptic, or doing a "apt-get install cupsys", my machine crashes when it tries to install the data: 
The mouse pointer is no longer visible, the screen freezes and swiching to another tty or restart X by "Ctrl-Alt-Del" is impossible. Only a (hard) reset let me use the computer again.

I thought maybe there is something wrong with whatever data is in the repository, so I downloaded the source code directly from [www.cups.org](www.cups.org) and compiled it myself. But when "make install" reaches a certain point, the screen freezes again. (Copying to Data, or sth like that)

I have little to no idea where to look to solve this problem. The Kernel and System logs don't show events that i can relate to CUPS.

Any help would be appreciated :) 

Carsten

---

### Post by senior on 2006-10-26
Hi Karsten,

Are you using Ubuntu V6.06??? or an old version on an Intel machine???


Senior.

---

### Post by seaside on 2006-10-26
Hi Senior, 
sorry I forgot: 
Yes, I'm using 6.06 Dapper (dist-upgraded from Breezy, which was upgraded from Hoary) on an older 1,2 GHz Athlon.  I think it was back then ( in Breezy times), when the problem first occurred.

I downloaded the cups 1.2.5 sources, and tried 1.2.2 from the repository. 

Perhaps this is helping:
Kernel: 2.6.15-27-k7
Gnome: 2.14.3

---

### Post by senior on 2006-10-26
Hi Carsten,
The problem is the dist-upgrade to V6.0.6 I did the same.
I solved the 'freezing problem' with a fresh install of V6.0.6SLT
After that all the freezing was gone 
Success.
Senior

---

### Post by seaside on 2006-10-26
Hmm, I was hoping to avoid the windowesque solution, cause i'm really, really lazy ;) But thanks anyway!

---

