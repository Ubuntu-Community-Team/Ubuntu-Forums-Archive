---
title: "Wireless problem using 7.04 on an iMac"
date: 2007-04-20
forum: Apple Intel Users
---

### Post by pikz on 2007-04-20
I have managed to get my wireless connection working, but there is a problem. I have to start the wireless connection every time I have restarted my computer. I use the following commands to start it:

sudo iwconfig eth1 essid wlan-ap
sudo ifconfig eth1 up
sudo dhclient

But 'ifconfig eth1 up' only works after I have put the computer to sleep and wake it up. If I don't do that then ifconfig won't find eth1.

Can someone help me?

---

### Post by Greywhind on 2007-04-21
Sounds to me like your wireless is being loaded in your suspend/resume script but not on boot. But I'm not an expert. Try searching the web for how to automatically get your wireless to set itself up on boot. (I don't want to assume you're using ndiswrapper, although that's my guess. If so, look at this link: [Ubuntuguide: Feisty - ndiswrapper]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29"))

Good luck.

---

