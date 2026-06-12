---
title: "Changing wireless channel?"
date: 2006-05-03
forum: Absolute Beginner Talk
---

### Post by Charax on 2006-05-03
I have Ubuntu Dapper with Kubuntu-desktop installed. By some miracle of fate it actually recognises my AirPlus G650+ wireless PCMCIA card (card's light is on, KWiFi manager works fine) - the problem is my WLAN operates on channel 11 and KWifi only seems to scan on channel 1. Is there any way to alter this?

---

### Post by Horizon on 2006-05-03
Mine uses channel 11 too and it found it fine.
Well technically to set the channel to 11 you have to :
```
sudo iwconfig wlan0 channel 11
```
just change wlan0 to whatever name you use for your wireless card interface.
Although i don't know if that will fix whatever problems you're having :-k

or do you mean you need to change some kwifi config option? i dunno i'll try fiddle with it, although i don't really use kde much so i don't know if i'll be able to find anything and i don't think there would be any reason for kwifi to seperately decide what channel to scan on and ignore your /etc/network/interfaces

---

