---
title: "Trying to enable WPA. How d'you comment out lines?"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by newagelink on 2007-01-06
I'm trying to get my wireless internet connection working; Belkin router, Comcast cable modem. I have an Intel PRO Wireless 2200 BG card (is it a NIC? Or are those only what you plug the ethernet cable into?) [which works fine](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel) ... It detects the MTSU wireless network, and was installed during Ubuntu 6.06 installation.

After tinkering with no success, it became apparent to me that I was typing in a Pre-shared Key (PSK) in the space for a WEP key. A friend of mine searched and he found this article: "[Enable WPA Wireless access point in Ubuntu Linux](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)".

Seems to be exactly what I need. I've followed the steps and am now at this direction: > sudo gedit /etc/network/interfaces

Comment out everything other than &#8220;lo&#8221; entries in that file and save the fileHow do you comment out lines?
Also, the next step: > Create a file called /etc/default/wpasupplicant, add entry ENABLED=0 and save the fileWhat does he mean by "add entry ENABLED=0"? Am I to create a text file ...?

Thanks...

---

### Post by taurus on 2007-01-06
Just put a # in front of a line if you want to comment it out.

```
gksudo gedit /etc/network/interfaces
```

---

### Post by wieman01 on 2007-01-07
There are a number of graphical tool you can use for WPA:

1. wifi-radar
2. gnome-network-manager
3. [a new network-manager]("http://www.ubuntuforums.org/showthread.php?t=299462")

Apart from this, try the HOWTO in my signature if you prefer to configure your WPA network manually.

---

