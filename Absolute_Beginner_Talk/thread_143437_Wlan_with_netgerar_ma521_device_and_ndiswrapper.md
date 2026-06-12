---
title: "Wlan with netgerar ma521 device and ndiswrapper"
date: 2006-03-12
forum: Absolute Beginner Talk
---

### Post by Tobitas on 2006-03-12
Hi, I am new to Ubuntu.
 
Following a nice description at ubuntuwiki ([https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper)) I managed to get the netgear drivers for my WLAN card installed. The driver is listed when I type "ndiswrapper -l" and I can configure the device in system-administration-networking. It is setup as DHCP.

Pinging the router does not work, nor any internet connection. I am sure I typed in ESSID and WEP key in hexidecimal format correctly. When I type iwconfig I get a message that no/any ESSID was detected. I did also type /etc/init.d/networking restart. After some moments I got this output: "*reconfiguring network interfaces... [OK]" Still the device does not connect to the internet. 

How can I configure my WLAN device so I can connect to the internet? Do I need to supply a gateway (192.168.1.1 in my case) and where do I type that in?

Thanks for helping.
Tobias

---

