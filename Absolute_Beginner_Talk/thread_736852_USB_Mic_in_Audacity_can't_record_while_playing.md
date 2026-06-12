---
title: "USB Mic in Audacity can't record while playing"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by SMA11784 on 2008-03-27
I actually already tried [asking this]("http://ubuntuforums.org/showthread.php?t=736088") on the Multimedia board, but it seems that either nobody knows what I should do or nobody cares.

I got a new USB mic.  Problem 1 in Audacity is that everything records at half speed, meaning I have to speed it up 100% to sound normal.  Problem 2 is that when I try to record while playing, it becomes very slow and choppy to the point of being unusable.

Idunno what else to try.  I'm not very good at computer.

---

### Post by intel on 2008-03-27
this looks like a usb driver problem,

please send a full description of 
- your problem,
- your hardware
- your software

to the following email address
linux-usb@vger.kernel.org,

---

### Post by northern lights on 2008-03-27
Could you post the output of ```
lsusb
```

Thanks

---

### Post by SMA11784 on 2008-03-27
Without the mic plugged in...
> Bus 008 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000 

With the mic plugged in the front USB port...
> Bus 008 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 074d:0005 Micronas GmbH 
Bus 004 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000 

Back port...
> Bus 008 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 074d:0005 Micronas GmbH 
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000 

I could go on.

---

### Post by SMA11784 on 2008-03-28
...hello?  Now what?

---

### Post by SergeySn on 2008-04-24
> **SMA11784 said:**
> ...  Problem 1 in Audacity is that everything records at half speed... I have exactly the same problem. Any ideas, anybody?

---

### Post by SergeySn on 2008-05-01
I have tried a Logitech USB mic - works good. So the problem is related to Snowball.

---

