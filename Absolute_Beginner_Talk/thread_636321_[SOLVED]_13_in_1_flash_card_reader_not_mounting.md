---
title: "[SOLVED] 13 in 1 flash card reader not mounting"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by mramsey on 2007-12-09
Well my flash card reader stopped mounting. I had just used it moments before and forgot to unmount the volume before I removed the CF card. Now when I insert the CF card it does not automatically mount like it did.  What did I do? and how do I get it back?

Thanks

---

### Post by nikoPSK on 2007-12-09
It was working before, and now it's dead? Have you tried it with windows to see if it's the reader malfunctioning? Also is it usb or otherwise? If it's usb let's see if ubuntu recognizes it

```
lsusb
```

and give me the output.

---

### Post by mramsey on 2007-12-10
> **nikoPSK said:**
> It was working before, and now it's dead? Have you tried it with windows to see if it's the reader malfunctioning? Also is it usb or otherwise? If it's usb let's see if ubuntu recognizes it

```
lsusb
```

and give me the output.

Here it is:

```
mramsey@ubuntu-mike:~$ lsusb
Bus 005 Device 007: ID 05e3:0760 Genesys Logic, Inc. Card Reader
Bus 005 Device 006: ID 0424:2504 Standard Microsystems Corp. 
Bus 005 Device 003: ID 0644:0200 TEAC Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 413c:3010 Dell Computer Corp. Optical Wheel Mouse
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 03f0:1312 Hewlett-Packard 
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 413c:2010 Dell Computer Corp. 
Bus 002 Device 002: ID 413c:1003 Dell Computer Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
mramsey@ubuntu-mike:~$ 



```

---

### Post by nikoPSK on 2007-12-10
well it's recognizing your card all right.

```
Bus 005 Device 007: ID 05e3:0760 Genesys Logic, Inc. Card Reader
```
I say, try putting a card in and trying again :D?

---

### Post by mramsey on 2007-12-10
Wierd...I must have tried restarting a dozen times. Now it worked!

---

### Post by nikoPSK on 2007-12-10
Yay! Please mark this thread as "SOLVED".

---

