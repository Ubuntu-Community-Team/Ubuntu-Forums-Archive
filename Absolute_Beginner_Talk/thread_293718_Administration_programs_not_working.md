---
title: "Administration programs not working"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by c0rd3l1a on 2006-11-05
I just installed Ubuntu 6.06.1 amd64 onto my Dell Dimension e521n (open-source desktop with AMD Athlon 64x2 Dual Core 5000+). The installation went off with only one hitch: configuring DHCP didn't work out. 

So now I am trying to configure the wireless connection through System>Administration>Networking. It loads normally, but when I click on the wireless connection and then click "configure" it freezes up. 

Furthermore, if I do that one time and have to force quit, then it will never even load at all again until I reboot. Also, at this point I cannot get Terminal to run. Or Device Manager or anything else under System>Administration.

What do I need to do? Should I just install the 32-bit i386 version?

Thank you in advance for any help you can give me!

---

### Post by MasterOfDisaster on 2006-11-05
This happened to me when I attempted to install the rt2x00 drivers for my wireless card.  The solution for me was to completely rid my installation of the driver, and use ndiswrapper.

Try to configure it through /etc/network/interfaces, by adding the following

iface wlan0 inet dhcp
wireless-essid myapname
wireless-key s:myplaintextpassword
auto wlan0

Change myapname to your wireless essid, and the myplaintextpassword to your WEP key.  Make sure to change wlan0 to whatever your wireless card's identifier is.

If this doesn't work, look at [https://help.ubuntu.com/community/WifiDocs/NdiswrapperOnAMD64](https://help.ubuntu.com/community/WifiDocs/NdiswrapperOnAMD64)

Good luck

---

