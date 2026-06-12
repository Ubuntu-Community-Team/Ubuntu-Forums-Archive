---
title: "Memory Test Failure"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by elite-elitist on 2007-06-01
I run the memory test on the Xubuntu CD and my PC failed. I started Xubuntu in safe mode, but it won't install because of partitioner failure. Windows XP fromats, installs, and runs okay as far as I can tell. 

Does this mean I have to get new memory now? :(

---

### Post by lamalex on 2007-06-01
yeah pretty much. Chances are windows just hasn't hit those bad addresses yet.

---

### Post by Cypher on 2007-06-01
You could always grab a memory testing app in Windows and run it and see what it reports..

---

### Post by kernel tom on 2007-06-01
> **elite-elitist said:**
> I run the memory test on the Xubuntu CD and my PC failed. I started Xubuntu in safe mode, but it won't install because of partitioner failure. Windows XP fromats, installs, and runs okay as far as I can tell. 

Does this mean I have to get new memory now? :(

the reason xubuntu won't install due to partition failure is becuase you can't format mounted drives, and xubuntu cd auto mounts... to change this go to Applications>Settings>Settins Manager>File Manager>Advanced>Configure(blue link in box) then deselect "Mount removeable drives when hot-plugged" and "Mount removable media when inserted"

then close it out, 

right click your hard drive on ur desktop and unmount it... then you can install xubuntu no problem

---

### Post by elite-elitist on 2007-06-01
> the reason xubuntu won't install due to partition failure is becuase you can't format mounted drives, and xubuntu cd auto mounts... to change this go to Applications>Settings>Settins Manager>File Manager>Advanced>Configure(blue link in box) then deselect "Mount removeable drives when hot-plugged" and "Mount removable media when inserted"

Thanks, maybe I'll give it another shot.

---

### Post by tgalati4 on 2007-06-01
Try cleaning the memory tabs with an eraser.  Clean the crumbs with a Q-tip and some alcohol.  Reseat the memory and run memtest again.  If it fails a second time (you should let it run several PASS cycles) then it's time for a new memory module.  

It's risky and time-consuming to install Linux with wonky memory.

---

### Post by elite-elitist on 2007-06-02
I think I have found a potential problem. Somebody installed PC133 memory in my laptop which only uses PC100 memory.

---

### Post by Wim Sturkenboom on 2007-06-02
That should not be an issue. The memory is clocked from the motherboard, so in this case your memory is underclocked (which is fine). Other way around would be an issue.

---

### Post by elite-elitist on 2007-06-02
EDIT: I am re-running the test and after 40 minutes it is passing. It may have failed in the past because I was being stupid and pressing buttons on the keyboard as the test was running.

---

### Post by elite-elitist on 2007-06-03
I have a problem starting xubuntu. It just won't start. It says some module failed, then it displays a black screen, and hangs up.

---

