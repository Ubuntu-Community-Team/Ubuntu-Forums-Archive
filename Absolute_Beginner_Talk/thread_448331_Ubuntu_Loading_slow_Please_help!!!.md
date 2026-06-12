---
title: "Ubuntu Loading slow Please help!!!"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by handuy on 2007-05-19
Hi guys I have a question and hope someone here could help me out.

This is the second time I installed Ubuntu. The first time I remember it loaded really fast at start up. I dunno why after uninstalled and reinstalled Ubuntu. Now it takes forever for Ubuntu to load at start up time. Did I do something wrong? I tried uninstalled and reinstalled again still it takes forever to load. 

Follow is how I partition my hardrive:

I  set 2GB for swap space and 30GB for Ubuntu to install to. I installed Ubuntu into the 30GB space. Did I do it right? or I suppose to install Ubuntu into the 2GB swap. Anyway, why do we need to reserve 2GB swap space? I don't understand this part please explain. I'm a novice

---

### Post by hyper_ch on 2007-05-19
SWAP is fine... swap is virtual memory to enhance your ram... even with 16gb ram it is recommended to have some :)

And the rest should be fine... out of the box it should be quite quick...

---

### Post by Gen2ly on 2007-05-19
handuy you might try checking the harddsik, though I don't think that is the problem.

"Reboot now and run .fsck:"
> sudo shutdown -Fr now

---

### Post by handuy on 2007-05-19
Yes, so how come it takes forever to load before it gets to the username and pw field?

I saw a post on here someone is having the same problem and once he put a blank cd into the cd drive .. it then load real fast. Same thing is happening to me when I put a blank cd in the cd rom drive and wonder if anyone could help?

---

### Post by tchoklat on 2007-05-19
You need double your RAM as a swap drive (up to 2Gb); about 10gb for / and a seperate /home partition of what ever you have left.
 
tchoklat

---

