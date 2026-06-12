---
title: "CPU usage"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by FreakTech on 2007-01-04
I am very new to linux and just had some questions about CPU usage.  When I bring up my system monitor it says that 100% of my CPU is being used is this normal.  I am running a 1.6Ghz Centrino Duo processor.  My memory is fine.  I am only using about 13% and none of the swap.  Is the CPU being displayed wrong??

Any one have any ideas

---

### Post by _simon_ on 2007-01-04
No it's not normal but I doubt that's a true reading, if 100% was being used you'd really know about it as everything would crawl along.

What does it say is using 100%? - click the processes tab, click the VIEW menu and select All Processes. If you click the CPU column so that a down arrow appears, it should list the highest users first.

---

### Post by carlosfocker on 2007-01-04
Have you just installed Ubuntu? What distro and version? When you are viewing the system monitor what process is eating the most processor time.

---

### Post by FreakTech on 2007-01-04
I am running beryl with xgl and it's saying that xgl is taking from 69 to 76% of it.  Is that normal?

---

### Post by _simon_ on 2007-01-04
ouch no!

Unfortunatly I can't help further except to say try doing a search on this forum and the beryl forum.

---

### Post by FreakTech on 2007-01-04
I am wondering if I have an argument wrong in my xgl and I'm not using the video hardware but the processor instead?  Could that be?

---

### Post by _simon_ on 2007-01-04
I don't think so otherwise it wouldn't work, XGL is an X server on top of OpenGL so it HAS to use your video hardware.

---

### Post by carlosfocker on 2007-01-04
what are you complete system specs?

---

### Post by FreakTech on 2007-01-04
1.6ghz centrino duo processor, 1 gig ram,  Nvidia Gforce 7600, dual 100 gig sata HDD one for linux other for windows,

---

### Post by carlosfocker on 2007-01-09
Even tho the CPU usage shows 100% is Ubuntu lagging at all? How is the overall performance? Just wondering because it should work.

---

### Post by carlosfocker on 2007-01-09
Was there any files you edited by hand. If so please post them.  

I would also take into the account this might also be a bug, so you might want to think about submitting one

---

### Post by crazedgremlin on 2007-01-10
On my 1.8 ghz AMD Sempron (64-bit (Running 64-bit edgy)), *Xgl* takes about 47%.
I don't think it should be doing that.

If I'm watching the system monitor graph while I rotate the cube, it spikes up to 100%.

It's probably not an untrue reading because the fan goes on a lot more than it does if I'm not running Xgl.

btw, I'm running Xgl and Beryl 0.1.4 on an ATI card (fglrx).

---

### Post by crazedgremlin on 2007-01-12
Ok I might have figured out what's going on in my situation:
I started up gdesklets and put a cpu plotting thingy on my desktop.  At the bottom of the thingy it says @1000.00M, and if I do something like moving a window, it says @1800.00M.
It's frequency scaling!
My processor was running at 1 gigahertz when it didn't need it.  Could this be the same thing for you guys?

---

