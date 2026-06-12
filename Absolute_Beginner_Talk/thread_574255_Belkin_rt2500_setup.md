---
title: "Belkin rt2500 setup"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by madmatrixz3000 on 2007-10-12
okay I looked at the Ubuntu wiki for Fiesty to install the rt2500usb drivers and it looks like this.
[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500)

> You will need to blacklist the SerialMonkey driver, add ndiswrapper to /etc/modules, and get the correct ndiswrapper setup, then make sure wpa_supplicant is installed. Then add this to you /etc/interfaces 

""iface ra0 inet dhcp 

wpa-driver wext 

wpa-ssid your-ssid 

wpa-ap-scan 1 

wpa-proto RSN WPA 

wpa-pairwise CCMP TKIP 

wpa-group CCMP TKIP 

wpa-key-mgmt WPA-PSK 

wpa-psk your-wpa-psk"" 

Then disable the wireless card in NetworkManager and do a sudo ifup ra0. 




So what does any of that do and what does it mean how do I do this etc.  I am confused

---

### Post by madmatrixz3000 on 2007-10-12
how do I add nDisWapper to modules?

---

