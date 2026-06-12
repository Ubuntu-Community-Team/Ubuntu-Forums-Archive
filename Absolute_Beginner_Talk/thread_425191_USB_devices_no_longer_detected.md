---
title: "USB devices no longer detected"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by projjalc on 2007-04-27
Hi. I'm completely new to Linux, and I recently installed Ubuntu on my Acer TravelMate 4651LMi (laptop). I'd originally started with Edgy, and I was able to use all my USB devices -- mouse, external hard drive, etc. However, upon upgrading to Feisty, none of these devices are detected any longer. It seems to be aware that the ports exist (I think), but is oblivious to anything connected to them. Could someone please tell me if they have an idea of what's going on, or if there is some specific info that I need to give you before you can determine anything? Thanks.

---

### Post by lamalex on 2007-04-27
could you post the output of ```
sudo lsusb
``` just to check if your usb ports are realizing anything is there?

---

### Post by projjalc on 2007-04-27
Weird ... with only the mouse and the hard drive connected, I get:
```
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 1241:1177 Belkin F8E842-DL Mouse
Bus 001 Device 001: ID 0000:0000
```
The mouse just got detected somehow, but it's not working properly ... the pointer is moving very jerkily. And the hard drive is still undetected.
Btw, I have 4 USB ports in total.

PS: After switching the devices around, I got this:
```
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 1241:1177 Belkin F8E842-DL Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```
And weirdly, the mouse is working fine now. But the hard drive stays undetected, even if I plug it into the ports where the mouse was working.

---

### Post by projjalc on 2007-04-27
After a restart, the problem just somehow sorted itself out. All things USB are now available. Not complaining in the least, but I really wish I knew what was going on.

---

