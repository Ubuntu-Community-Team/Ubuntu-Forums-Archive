---
title: "yet another netgear wg111 problem"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by KhaaL on 2006-08-14
hey all

I've followed the steps at: [http://www.ubuntuforums.org/showthread.php?t=202254&highlight=wg111+netgear](http://www.ubuntuforums.org/showthread.php?t=202254&highlight=wg111+netgear) in order to get my card working, but at the ndiswrapper window it shows that the hardware are not present, while iwconfig shows there is a wireless extension on eth2 and the device manager lists the wireless dongle.

Can someone help me get this thing working? any help would be very appriciated (or at least point me to a wlan card that works natively in linux)

---

### Post by gn2 on 2006-08-14
I have a D-link DWL-650+ 22mbps version with Texas Instruments chipset works out-of-the-box.

Ideal if you just want it for internet access, not as fast as more modern cards for network file transfer speed.

List of cards here: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by spd106 on 2006-08-14
Try this guide as well
[https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111](https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111)

---

### Post by KhaaL on 2006-08-14
i did try the other guide aswell, and it made my wireless interface (eth2) poof away... so I'm gonna have to wait before reinstalling ubuntu until i got a compatible wlan pci card...

---

### Post by Hezekiah on 2006-08-17
I'm not sure how much variation there is between these things, but I have a Netgear WG111 v2 USB wireless adapter which worked without any extra setup under Ubuntu Dapper - I just plugged it in and entered the WEP key information in the network configuration dialog.

I'm not sure what Ubuntu does that's special to make it work though, because it isn't detected under Etch out of the box.  So some piece of firmware which Ubuntu ships by default seems to cover this hardware.

---

