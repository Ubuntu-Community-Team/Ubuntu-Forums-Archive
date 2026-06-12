---
title: "How to lock Keyboard and mouse intentionally"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by buntu_Geek on 2008-02-10
I want to lock the keyboard and mouse(touchpad) of my laptop while a video is running....
So that the person viewing should not tamper with it....

I cant plug off my keyboard and mouse coz its a laptop and its inbuilt.. :D

Anybody have any ideas...???

---

### Post by tyggna1 on 2008-02-10
Depends on how comfortable you are with Linux.  If you are very comfortable, then there is a way.

The first one is to make sure that you touch pad is running as a service (probably is by default).  The second step is to install a service package manager.  From there, you just type in ```
service synaptics stop
``` to stop the touch pad from working.  You might have to replace synaptics with whatever driver is running your touchpad--but that'd be the way to go.

---

