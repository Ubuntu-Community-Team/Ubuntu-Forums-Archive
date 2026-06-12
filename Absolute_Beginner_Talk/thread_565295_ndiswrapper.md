---
title: "ndiswrapper"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by ubu_new on 2007-10-02
Hey everybody i am a total newbie for Linux (I am kinda enjoying it). I used ndiswrapper to use my wireless to work ( Intel 4965) as posted in some threads of this forum (and it is working!), but now i have to modprobe ndiswrapper everytime i use Ubuntu. Is there some way to start the wirelaess lan at the start of the system. thank you for your community support.

---

### Post by wieman01 on 2007-10-02
Try this:
> sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m

---

