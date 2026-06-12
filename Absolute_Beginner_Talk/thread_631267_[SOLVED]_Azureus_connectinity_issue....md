---
title: "[SOLVED] Azureus connectinity issue..."
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by loverman210 on 2007-12-04
Hello everyone...

Well here is my new problem...

I installed azureus 2.5.0.4 and have set a static internal ip  192.168.1.45 and opened a port 53565..

The Problem is that while azureus doesn't have any NAT or reachability problems, it takes extremely long to load and when it's done it keeps everytime it loads to pop up a message 

<<There appears to be another program process already listening on socket [127.0.0.1: 6880]. Loading of torrents via command line parameter will fail until this is fixed.>>

But the thing is I don't run any other programs!! Only one at a time and right now it's azureus...

--When I had the router choose my internal IP I was using "ifconfig" to see which one was, and then I forwarded the port in there...-- 

Note that this problem started from the time I set s static internal ip so that I could forward my port...and not change the settings all the time...

thnx in advance..

---

### Post by lvleph on 2007-12-04
You changed the port Azureus is suppose to use, right? Because that message suggests that Azureus is still trying to use port 6880.

---

### Post by loverman210 on 2007-12-04
azureus is using 6880 on 127.0.0.1 on IP 127.0.0.1!! I have opened 53565 on 192.168.1.45!! doesn't make any sense! Also when I check the NAT reachability is says: ok!

---

