---
title: "Recognizing PCMCIA wifi card"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by JO68 on 2007-12-03
I've been trying to get kismet working for about a week now and finally i gave up on my broadcom wireless card(nothing worked with it) and bought myself a netgear WG511T card.  I've turned off my broadcom card but when i run iwconfig in the terminal it seems as if my broadcom card is still the card listed.  

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Monitor  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by Severun on 2007-12-03
Your wireless card might be in one of the restricted drivers.  I have an Intel Pro 3945 and it needs the restricted package.

If the driver for you card is in restricted modules, install the appropriate restricted modules for your install, i.e. 64 bit, 386, generic, etc.  Then be sure to enable it in the restricted driver manager in System->Administration->Restricted Driver manager.

Hope this helps.

--Severun

---

### Post by JO68 on 2007-12-03
I have actually removed the hardware support for my old card, and enabled the drivers for my current one.  I don't want to say there is no way that the restricted drivers is the issue but it seems to me that its extremely unlikely

---

### Post by pebo on 2007-12-03
Try adding bcm43xx to your /etc/modprobe.d/blacklist

---

### Post by NullHead on 2007-12-04
I would use this guide. It worked very nicely for me.:popcorn:
[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

---

