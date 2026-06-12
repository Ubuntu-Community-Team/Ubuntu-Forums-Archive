---
title: "Help With Sound...."
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by pagzforpres on 2007-06-22
As the title suggests, I can't get my sound working. 


I am pretty new to Ubuntu, and I found out to run a script in the terminal giving me this:
-------------------------------------------------------------------------------------------------------------------------------
02:00.0 Multimedia controller: ATI Technologies Inc Unknown device 4d53
        Subsystem: Dell Unknown device a503
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at dcf00000 (32-bit, non-prefetchable) [size=1M]
        Memory at d0000000 (32-bit, prefetchable) [size=32M]
        Capabilities: <access denied>

03:03.0 Multimedia audio controller: Creative Labs SB X-Fi
        Subsystem: Creative Labs X-Fi XtremeMusic
        Flags: bus master, medium devsel, latency 64, IRQ 5
        I/O ports at dce0 [size=32]
        Memory at dcc00000 (64-bit, non-prefetchable) [size=2M]
        Memory at d8000000 (64-bit, non-prefetchable) [size=64M]
        Capabilities: <access denied> 
--------------------------------------------------------------------------------------------------------------------------------

What does this mean (is it relevant to my problem?) and how can I get a driver to get my sound up and running. 

Please help, I really like this O/S and I want sound :) 

-pagz

---

### Post by kpkeerthi on 2007-06-22
As far as I know Creative X-Fi is not (yet) supported by ALSA.

---

### Post by pagzforpres on 2007-06-22
> **kpkeerthi said:**
> As far as I know Creative X-Fi is not (yet) supported by ALSA.

I am assuming that is bad.... 


Does that mean no sound for me? Are there any alternatives that don't include a monetary cost? ;)

---

### Post by kpkeerthi on 2007-06-22
Check this out...

[http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix](http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix)

---

