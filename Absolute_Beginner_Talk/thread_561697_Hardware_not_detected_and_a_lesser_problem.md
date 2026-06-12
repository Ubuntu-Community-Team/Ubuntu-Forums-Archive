---
title: "Hardware not detected and a lesser problem"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by devosion on 2007-09-27
Last night I installed and attempted to get my wifi internet on my linksys wireless usb router to work. After using two different drivers, one through ndiswrapper and one configured for linux, I was unable to get either to work properly. I found out I was using a 32bit driver for my 64bitbit architecture then switched. This failed to work as well, I was able to get a mac address from my wifi point and detect other wifi points but I wasnt able to connect. I should have stopped here but somewhere along the way ubuntu stopped detecting my hardware. When I run iwconfig in the terminal it does not show up anywhere. Is there is a fix for this or should I consider reinstalling ubuntu? All i have loaded is ndiswrapper so far.

Also ubuntu seems to spontaneously freeze on my system for a few seconds the entire time it is running. Sometimes it will also do it in sequence. When I investigated a bit I found out my graphic card is not properly installed so I considered this to be the problem. Any ideas?

---

### Post by eph1973 on 2007-09-27
Try out this link:
[https://help.ubuntu.com/community/WifiDocs/Device/LinksysWUSB54GC](https://help.ubuntu.com/community/WifiDocs/Device/LinksysWUSB54GC)

Assuming you have the WUSB54GC.

Most likely your problem with your video is not causing your wireless internet connection problem.  You should correctly fix your video card configuration (it kinda sounds like you have an idea what's wrong there, so I am not addressing it).  If you have a different wireless networking card, state what brand name and model it is.  Hope this helps.

---

### Post by nonewmsgs on 2007-09-28
what are the results of lspci and what commands are you using to see the AP's mac address?

---

