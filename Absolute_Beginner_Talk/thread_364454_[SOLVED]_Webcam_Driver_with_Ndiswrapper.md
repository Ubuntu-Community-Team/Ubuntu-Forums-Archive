---
title: "[SOLVED] Webcam Driver with Ndiswrapper"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by ashmew2 on 2007-02-18
HI folks , I have a Webcam whose driver i have recently installed using ndiswrapper.when i run 
```
lsusb
```
It gives me :
```
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0ac8:301b Z-Star Microelectronics Corp. ZC0301 WebCam
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000 
```

So the Webcam is being detected , now what i did was i found my webcam CD and copied the inf files onto the harddrive  , first it was complaning about some .sys files but i managed to download em off somewhere. The driver installed fine (i think so). 
Now comes the problem , what do i do now ? How do i use my webcam ?
 Thanks!!

---

### Post by teaker1s on 2007-02-18
err your not using ndiswrapper correctly it's quote:-
 > ndiswrapper is intended for wireless network cards, not for installing windows webcam drivers

---

### Post by ashmew2 on 2007-02-19
So is there no way to install and run my webcam then /?

---

### Post by teaker1s on 2007-02-19
according to google your webcam does work with Video4Linux. 
I have never done this but am under the impression the module loads automatically if installed and your best solution would be to ask for help with the model of your webcam and Video4Linux.

---

### Post by ashmew2 on 2007-02-19
Thanks for the pointer , ill try it sooon and get back to ya :)

---

