---
title: "Wireless Networking"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by WolfCarinea on 2007-03-16
ok, i used "windows network drivers" to install the drivers bcmwl5.inf and bcmwl5a.inf to get my wireless card (broadcom 4306 802.11b/g WLAN) to work, the widnows network drivers program says "Hardware Present: Yes" for both installed drivers. i cannot connect however to a wireless network, there is a blue light on my computer that says when the wireless card is active/looking for a network, i have yet to get that light to come on while using linux. what do i do?

---

### Post by K.Mandla on 2007-03-16
Have you tried 

```
iwlist --scanning
```
I believe that searches for local wireless networks (I'm at work, so the command might be slightly off.) Or just go straight to ...

```
sudo dhclient eth0
```
Substitute your interface address for *eth0*. I'm not sure if you can straightaway ping your router without being part of the network, but you could try it.

```
ping 192.168.1.1
```
You might have to substitute the address of your router for that one. 

Hope those help.

---

