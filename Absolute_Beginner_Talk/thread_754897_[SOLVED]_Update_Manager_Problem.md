---
title: "[SOLVED] Update Manager Problem"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by ssdurn on 2008-04-14
Hi - Newbie calling!

I have just run the Update Manager and half way through the system died and PC shut off.

Now I can't get the Update Manager to complete the job:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


So went to terminal and ran the stated command but it's saying it required supervisor access? 

So 2 questions:  

1.How do I login as a supervisor?

2. I have run the memory test thingy and no faults found - how should I go about detecting what's causing the system to crash and die intermittently.

---

### Post by jken146 on 2008-04-14
Type ```
sudo dpkg --configure -a
```

---

### Post by Oldsoldier2003 on 2008-04-14
> **ssdurn said:**
> Hi - Newbie calling!

I have just run the Update Manager and half way through the system died and PC shut off.

Now I can't get the Update Manager to complete the job:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


So went to terminal and ran the stated command but it's saying it required supervisor access? 

So 2 questions:  

1.How do I login as a supervisor?

2. I have run the memory test thingy and no faults found - how should I go about detecting what's causing the system to crash and die intermittently.

in a terminal do this
```
sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade
```
that should sort you out. If you have further problems after this let us know exactly what happens and what error messages you receive and we'll be more able to help trouble shoot.

---

### Post by forestpixie on 2008-04-14
> 2. I have run the memory test thingy and no faults found - how should I go about detecting what's causing the system to crash and die intermittently.

Next time it crashes - have a look in the system logs to see if it shows what caused it - they can be found in System >admin > System - System Log

Although that said last time I had a similar issue it was crying out for the power supply to be chnaged.

---

