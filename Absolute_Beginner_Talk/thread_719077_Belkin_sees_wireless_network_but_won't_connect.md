---
title: "Belkin sees wireless network but won't connect"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by yosenut on 2008-03-08
Hello.

I am a brand new Xubuntu 7.10 user (48 hours old- former XP and MacOS user) on my old Dell 2650 laptop, The support on this board has been invaluable to getting my Belkin F5D7010 v.7032 recognized (the amber light is blinking after I have installed the 8185 driver using ndiswrapper and restarted.) I have a Linksys wireless router running a WEP 128 bit network from my BellSouth wired DSL.The Belkin sees my encrypted network (when I go into the network manager), but won't connect. 

When I run sudo /etc/init.d/networking restart,I get:

* Reconfiguring network interfaces...                                    
There is already a pid file /var/run/dhclient.wlan0.pid with pid 5185
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:17:3f:2f:4a:95
Sending on   LPF/wlan0/00:17:3f:2f:4a:95
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.



iwconfig gives me:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Auto  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:-2147483648 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
 
In my network manager properties, I chose the right ESSID, typed in my hexadecimal network key as the passwiord and picked DHCP for the configuration. Does the problem run deeper? 

Thank you in advance for any suggestions,

---

### Post by handydan918 on 2008-03-08
As a general rule, it's best to get into your router and disable wep or wpa encryption when troubleshooting wireless issues. It just helps eliminate possibilities.

After you've done that, please post the output of ```
lspci | grep -i net
```
and someone will be able to get a clue.

---

### Post by yosenut on 2008-03-09
Dear HandyDan,

You're awesome! Thank you for your helpful suggestion. After turning off security, I was able to connect wirelessly. 

grep gave me:
02:01.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
03:00.0 Ethernet controller: Belkin Unknown device 701f (rev 20)
 
I then reactivated security. Then I fooled around with the Network appication a bit, didn't even have to do anything in the terminal and lo and behold, I was getting asked for my key.

So thrilled! Thank(ed) you so much!

---

### Post by handydan918 on 2008-03-09
Great! Glad I could help.

---

