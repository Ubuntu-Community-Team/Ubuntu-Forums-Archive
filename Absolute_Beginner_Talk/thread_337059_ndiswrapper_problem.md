---
title: "ndiswrapper problem"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by Alvar on 2007-01-12
I installed ndiswrapper-util 1.8 and then the bcmwl5.inf and bcmwl5.sys files. I used that to install the wireless drivers. Before the wireless light (FN +F2) would not respond, but now it lights up. (Btw I have BCM4306) Now when I go to system>admin>networking I don't see wlan0. when I run ifconfig wlan0 I get "wlan0:error fetching interface information: Device not found". Can someone help me here, i'm still a noob at this stuff (gimme c

---

### Post by KentS on 2007-01-12
What's the output from
```
ndiswrapper -l
```
when you give the command in a terminal?

---

