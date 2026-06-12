---
title: "Kde on Ubuntu wireless problem"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by williampbonnes on 2008-03-13
Hi,
I just recently installed  Kubuntu on my system and now the wireless does not work. I get a no active devices message. I worked with Gnome until I installed KDE then it stopped altogether. Does any one have any suggestions?
Thanks
WPB

---

### Post by OffAxis on 2008-03-13
does it show up in knetworkmanager?

---

### Post by williampbonnes on 2008-03-13
No it does not. It is visible in the Hardware browser but it says status unknown.

---

### Post by OffAxis on 2008-03-20
What kind of card is it?
USB or PCI?

you could try manually bringing the card up with 

```
sudo ifconfig <card name> up
```

if you don't know the name of your card you can issue a 

```
sudo ifconfig
```

command and it'll list all the available interfaces; eth0, eth1 are usually your wired connections and wlan0, rausb0, etc. is usually the wireless connection.

If that doesn't work hopefully this'll help:
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

