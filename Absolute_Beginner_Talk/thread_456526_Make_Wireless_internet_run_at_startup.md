---
title: "Make Wireless internet run at startup"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by bgissal on 2007-05-27
After about 12 hours of tinkering, I finally was able to connect my Dell c400 laptop (7.04 Feisty) with Dell 1350 TrueMobile chipset to connect to my wireless network.

But I still have a problem. Everytime I restart the computer, I need to grab a terminal and type:

sudo modprobe ndiswrapper 
sudo iwconfig wlan0 essid asdf

The first command opens the wireless options under Network Manager. The second actually connects to the internet.

My question is...How do I make these commands run at startup so I don't have to enter these commands everytime I restart/shut down?????

I am a complete n00b.

---

### Post by Ek0nomik on 2007-05-27
You should be able to start the command at startup.

System/Preferences/Sessions

Than you can type

```
sudo modprobe ndiswrapper
```

---

