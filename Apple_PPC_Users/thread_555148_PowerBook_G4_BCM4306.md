---
title: "PowerBook G4 BCM4306"
date: 2007-09-19
forum: Apple PPC Users
---

### Post by BS&amp;SIR on 2007-09-19
I have recently installed Ubuntu FF 7.04 and all updates on my PowerBook G4. Things seem to be going well except for the wireless network. My problem is that the eth1 (BCM4306) shows as being DISABLED [sudo lshw -C network]. I do not know how to ENABLE it. I hope some one has a solution. I can use the wired network, but I really want to go wireless.

---

### Post by pxwpxw on 2007-09-20
Is wireless  enabled in your desktop  Network Manager applet?

---

### Post by BS&amp;SIR on 2007-09-20
Yes, I have a checkmark next to the Wireless connection, the status of eth1 does not change wether the box is checked or not. I read much of the documentation on this subject. I even came across instructions on what to do if this happens (eth1 DISABLED). The instructions say to check with the laptop team, there was no info for testing PowerBooks running FF7.04. Also I was to check my Powerbook G4 manual to see if a keyboard combination was available to turn the network on or off. No luck there, you can DISABLE/ENABLE the network, but only from a menu on the desktop (using the mouse-pad). Lastly the instructions directed me to an Ubuntu Forum to see if someone else has the same Laptop as I do, maybe they have a solution.
Thanks, GRP.

---

### Post by frog_pilot on 2007-09-20
[fix for wireless internet on iBook]("http://ubuntuforums.org/showthread.php?t=526901")

alternatively:

try to install the "bcm43xx-firmware" package from this repository "deb [http://ubuntu.cafuego.net/](http://ubuntu.cafuego.net/) feisty-cafuego bcm43xx"

2. ```
sudo modprobe -v bcm43xx
``` to see if this driver is working for you

3. ```
iwconfig
``` shows you witch interface your wlan-adapter has e.g. wlan0 or eth1

4. to activate the found interface ```
sudo ifconfig eth1 up
```

5. to scan for your local AP ```
sudo iwlist eth1 scan
```

from here you could configure your wireless adapter with the network-manager but the driver is only supporting WEP


maybe for a workaround for your hardware it is necessary to complete uninstall the "network-manager" and "gnome-network-manager" packages

I had to do this to get a Broadcom 4318 WLAN-adapter in an ACER-Notbook with static IP and WPA working. But this was VERY tricky...:popcorn:

---

### Post by BS&amp;SIR on 2007-09-20
THANKS for the tip!!. I used the link to the thread that you supplied, and it worked beautifully !!!. Now I'm off to thank the person, to thank the person who wrote the program.

---

