---
title: "connect to the internet with feisty"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by nehc on 2007-04-24
how do i connect to the internet?
when i open the "network setting", then go to property of "wireless connection (wmaster0)" i have a check on "enable roaming mode".
then next, on the desktop next to the date and hour i can see all the wireless connection. i connect to mine using this options
wireless security: wep 128-bit passphrase
passphrase:5ba45bc4200eaa8e760a6cf89b
authentication: open system
after clicking in the "login to network option" the icon next to the date said "wireless network connection to "coldpot (0%)
i wrote lsusb on the terminal and this is what i got
Bus 004 Device 003: ID 413c:2003 Dell Computer Corp. 
Bus 004 Device 002: ID 0461:4d15 Primax Electronics, Ltd 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 045e:00f7 Microsoft Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 043d:00e9 Lexmark International, Inc. 
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 008: ID 13b1:0020 Linksys 
Bus 002 Device 001: ID 0000:0000

do i have to do the ndiswrapper thing in order to connect to the internet?
i really hate the ndiswrapper process, is long and not effective on me.
henry

---

### Post by rjfioravanti on 2007-04-24
please output results to

ifconfig

iwconfig

iwlist scan

---

### Post by nehc on 2007-04-24
HI, thanks for looking my post

nehc@NEHC-UBUNTU:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:72:D9:A3:16  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1432 (1.3 KiB)  TX bytes:1432 (1.3 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:18:39:1B:68:0E  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:11319 (11.0 KiB)

wlan0:ava Link encap:Ethernet  HWaddr 00:18:39:1B:68:0E  
          inet addr:169.254.2.194  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-18-39-1B-68-0E-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

nehc@NEHC-UBUNTU:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:"ColdPot"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

nehc@NEHC-UBUNTU:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Failed to read scan data : Operation not supported

wlan0     No scan results

Henry

---

### Post by nehc on 2007-04-24
i also try [http://ubuntuforums.org/showthread.php?t=381117](http://ubuntuforums.org/showthread.php?t=381117) and this is what i got
nehc@NEHC-UBUNTU:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

nehc@NEHC-UBUNTU:~$ sudo iwconfig wlan0 essid "ColdPot"
Password:
nehc@NEHC-UBUNTU:~$ sudo iwconfig wlan0 key 5BA45BC1955EAA9E540A5CF50B
nehc@NEHC-UBUNTU:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:18:39:1b:68:0e
Sending on   LPF/wlan0/00:18:39:1b:68:0e
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Henry

---

### Post by silkstone on 2007-04-24
Your are using a hexadecimal passphrase. When you are asked to input the passphrase, you can choose from different types including hex - try selecting that and then enter the code.

You may also have to enter a keyring password when requested. Choose a new password carefully because it is difficult to change later.

---

### Post by nehc on 2007-04-24
i can go online if i plug the cable
henry

---

### Post by rjfioravanti on 2007-04-24
try the wireless with no password first, if you can disable the security in your router

This will tell you for sure if the problem is with your password or with your wireless drivers

---

