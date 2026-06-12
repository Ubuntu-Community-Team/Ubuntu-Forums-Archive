---
title: "TrueMobile Problems"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by limelightos on 2007-06-13
Could someone help me with my wireless problems?

My Dell Latitude D600 running Feisty cannot pick up a wireless signal. I have read around and know it is my TrueMobile (1400) card. I have installed ndiswrapper-common and ndiswrapper-utils done:

```
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -l
     drive bcmwl5.inf installed hardware present
sudo depmod -a
     nothing appears to happen
sudo modprobe ndiswrapper
     again, nothing
sudo edit /etc/modules
     added ndiswrapper to the end and saved

```
I then rebooted but the network manager still will not get a signal.

I want to get rid of m$ from my PC

Help!!!

---

