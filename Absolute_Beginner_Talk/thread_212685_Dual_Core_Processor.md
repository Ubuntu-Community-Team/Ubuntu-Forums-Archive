---
title: "Dual Core Processor"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by tonyp1969 on 2006-07-10
How do I tell Ubuntu 6.06 that I have a Dual Core processor? When I view processes it seems to me that the system is only seeing one. 
Do I in fact need to "advise" the system that I am running dual core?

---

### Post by Jagot on 2006-07-10
You need to install the smp kernel which supports dual-core processors, multiple processors, hyper-threading, etc:

```
sudo aptitude update && sudo aptitude install linux-686-smp
```

---

### Post by tonyp1969 on 2006-07-10
Thank you.

---

### Post by Frank Golden on 2006-07-10
After updating kernel use the add feature of the panel,
that is right click panel and choose add and place two
CPU frequency applets on it. You can then configure each one 
to monitor each processor core. Right click an applet and you can
change the processor it is monitoring from the drop down.
You can have one set to 0 for instance and the other set to 1.

---

### Post by tonyp1969 on 2006-07-11
Now that is how a PC should run, absolutely stunning performance.
I have now ordered my 64Bit version, lets see if it gets any better!

---

### Post by crystal on 2006-07-11
> After updating kernel use the add feature of the panel,
that is right click panel and choose add and place two
CPU frequency applets on it.

Could you elaborate? I do not understand what panel is being referred to.

---

### Post by srt4play on 2006-07-13
> **tonyp1969 said:**
> Now that is how a PC should run, absolutely stunning performance.
I have now ordered my 64Bit version, lets see if it gets any better!

What are your system specs? I've almost convinced myself to upgrade to a AMD64 4200 x2.  Is there that noticeable of a difference in day to day stuff compared to single core?

---

### Post by Frank Golden on 2006-07-13
> **crystal said:**
> Could you elaborate? I do not understand what panel is being referred to.
The panel, Crystal is the bar at top and bottom of the screen
with icons. If you right click a clear area of it yo can choose
add to panel. In the menu that shows op is a applet called 
CPU frequency scaling monitor. Add 2 of them to panel and right click each one in turn. You will be able to assign each one to a
different CPU core. For instance one could be Cpu 0 and the other
Cpu 1. This will allow you to keep an eye on each processors
frequency. By default a program called Powernowd will automatically control CPU frequency based on demand. You will
see that graphicaly. At idle the procs on my machine show 1000Mhz
when under load one or the other will show 1300MHz or 1660MHz. 
1660MHz is the max for my processor. This throttling effect
is intended to save power and reduce heat.

---

### Post by tonyp1969 on 2006-07-21
The POWERDNOW program sounds very useful, especially in this weather, thanks for the tip

---

### Post by Guy Smiley on 2007-01-24
New to Ubuntu and forums so hope this isn't out of line, but having just installed Ubuntu on my Sony Vaio vgn-N11s, I followed this post to add two Processor frequency monitor icons to my Crystal panel and sure enough I can assign the two icons to processor0 and processor1, with both running at 800Mhz, which when altered to a % relates to 50% (for each of the two processors) which is correct as its a 1.6GHz dual core processor machine and thereby proves the Ubuntu system has recognised dual processors 'straight out of the box' without tweaking. Took me a while and several posts to find this post, so just wanted to say thanks for the prompt - sorry for stating the b*******n obvious but it is the absolute beginner forum !

---

