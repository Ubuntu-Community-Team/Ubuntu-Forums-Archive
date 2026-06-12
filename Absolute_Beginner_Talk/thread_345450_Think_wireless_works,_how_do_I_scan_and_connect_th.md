---
title: "Think wireless works, how do I scan and connect though??"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by chlorinekid on 2007-01-24
I recently bought this wireless card for my laptop:

[http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&ih=001&sspagename=STRK%3AMEWN%3AIT&viewitem=&item=110075382772&rd=1&rd=1](http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&ih=001&sspagename=STRK%3AMEWN%3AIT&viewitem=&item=110075382772&rd=1&rd=1)

Here's what it say's in the description:

> The Ambit card chipset is provided with most Linux distors as well. I tried it with Ubuntu, Kubuntu, SuSE 10 oss and Fedora. Works well with easy setup. You dont need to install and compile your own drivers, its all added by default to your distro.

So I think the card is working and 'wlan0' shows up in network interfaces **but I don't know how to scan for my network and then connect..**

whats the command?? thanks for you help...

---

### Post by nalmeth on 2007-01-24
sudo iwlist ath0 scan
or
sudo iwlist wlan0 scan

You can also use a program called wifi-radar to detect networks. Aparently network-manager is supposed to be great for wireless roaming and detection, but I never saw its touted ability work. 
For now, to connect, enter the information in System-Administration-Networking

---

### Post by chlorinekid on 2007-01-24
thanks for the help pal, i'll try that now. 

whats the command to get wifi-radar in case i need that to search??

thanks

---

### Post by nalmeth on 2007-01-24
No problem

If the universe repository is enabled, simply enter:
```
sudo apt-get install wifi-radar
```
To run it:
```
gksudo wifi-radar
```

If universe is not enabled (it will say package not found), either open Synaptic package manager, find repositories, and enable it. 

OR
```
sudo nano /etc/apt/sources.list
```
Find the following lines:
```
## Uncomment the following two lines to add software from the 'universe'
## universe WILL NOT receive any review or updates from the Ubuntu security
##deb http://archive.ubuntu.com/ubuntu/ edgy universe
##deb-src http://archive.ubuntu.com/ubuntu/ edgy universe
```
And remove the ## (uncomment the lines) to enable the repository.
CNTL-x, hit y to save
```
sudo apt-get update
sudo apt-get install wifi-radar
```

---

### Post by chlorinekid on 2007-01-24
ive managed to get the ethernet connection working so that i can install wifi radar and that all been completed ok. i think my wireless card is on eth1.

however when i try to scan for networks using the wireless card it says that the device dosnt support scannning... any ideas?

do i have to bring the cable connection down before i start messing with the wireless?

i use ```
sudo dhclient eth0
``` to bring the cable connection up, is it the same principle for the wireless??

anyone any ideas on the scanning problem?

thanks...

---

### Post by chlorinekid on 2007-01-24
heres what i have when trying to bring up the wireless:

> dave@dave-laptop:~$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 11909
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFFLAGS: Device or resource busy
SIOCSIFFLAGS: Device or resource busy
Listening on LPF/eth1/00:02:8a:f1:83:2d
Sending on   LPF/eth1/00:02:8a:f1:83:2d
Sending on   Socket/fallback
receive_packet failed on eth1: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
dave@dave-laptop:~$ 

---

### Post by chlorinekid on 2007-01-24
bump

---

### Post by nalmeth on 2007-01-24
Yes, it works the same way. Your settings including network name and any WEP code must be entered for it to connect to the router though.

Follow the names given in System-Administration-Networking

Wifi-radar tells you you can't scan? 
If your device doesn't support scanning, you will have to manually enter the information of your network. Name, WEP code, stuff like that.

You can do this in the Networking applet. For more detailed specifications, open up /etc/network/interfaces

For some troubleshooting, this guide has all the information, though its a bit hard to read at first. A lot of the steps you can skip, because the driver seems to be working. Follow the directions and you should become familiar with where everything is:
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

I wish I knew more to be able to help you, but already your situation is much different than mine. I will come back and check your thread out later or tomorrow to see if there's anything else I can add.

---

