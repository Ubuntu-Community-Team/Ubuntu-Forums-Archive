---
title: "[SOLVED] Is even 1GB RAM insufficient ???"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by sovereign_soul on 2007-09-17
Hi, 

My HP Pavillion notebook has a RAM of 1GB which I always believed would be sufficient for most tasks. However, that this was a mere illusion , was revealed to me when I installed ubuntu 7.04 on my system.

Upon checking with tools such as top, free the RAM usage was in excess of 1GB with abt 14MB used of swap space too. Compared to this, my XP installation uses only abt 390MB.

What do u think could be the reason ?

---

### Post by bodhi.zazen on 2007-09-17
LMAO !!!!!!!!!!!!!!

RAM usage if VERY different with Linux. The saying goes, unused RAM is wasted RAM.

The OS you are coming from does not use RAM as efficently 

See these links :

	[http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

	[http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?](http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?)

:lolflag:

---

### Post by aysiu on 2007-09-17
To follow up with what bodhi.zazen said, are you basing this concern on an actual noticeable performance difference, or are you just looking at numbers?

I have run Ubuntu on 128 MB, 256 MB, and 512 MB of RAM and have had great performance (well, 128 MB required using IceWM instead of Gnome or KDE). I've never used 1 GB of RAM in Ubuntu.

---

### Post by bodhi.zazen on 2007-09-17
Just to be clear, I am not laughing *at you*, I have a twisted sense of humor and your question struck me as very funny is all.

Your questions are welcome here.

---

### Post by southernman on 2007-09-17
If you install an app called htop (sudo aptitude update && aptitude install htop) you'll see a true(r) sense of what your system is actually using. After installing htop, just run "htop" in the terminal

PS. if the above update and install command fails, add a second sudo in front of the aptitude install part.

---

### Post by southernman on 2007-09-17
> **bodhi.zazen said:**
> Just to be clear, I am not laughing *at you*, I have a twisted sense of humor and your question struck me as very funny is all.

Your questions are welcome here.

Now you clarify it! rofl

I'll edit my post above  *sighs*

---

### Post by bodhi.zazen on 2007-09-17
> **southernman said:**
> Now you clarify it! rofl

I'll edit my post above  *sighs*

LOL, I saw that ninja edit ...

---

### Post by rfruth on 2007-09-17
never had more than 512 MB, no problem(s)

---

### Post by sovereign_soul on 2007-09-17
thanks for the super-fast replies. This article was a real eye opener.

Thanks ppl.

---

### Post by southernman on 2007-09-17
> **bodhi.zazen said:**
> LOL, I saw that ninja edit ...

haha... I just called Chuck in!

---

### Post by graigsmith on 2007-09-17
wow, that article is an eye opener. so linux is only using 700 or so megs of my 2 gigs of memory. is this because of that 888 meg limit thing?  does ubuntu support more that 888 megs of ram?  or is more than half my ram useless?

---

