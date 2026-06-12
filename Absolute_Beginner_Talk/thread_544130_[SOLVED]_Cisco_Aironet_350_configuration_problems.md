---
title: "[SOLVED] Cisco Aironet 350 configuration problems"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by kdchapman1776 on 2007-09-05
My system: 
Compaq Armada M700 Laptop
Has built in ethernet
Added a Cisco Aironet 350 Wireless card - Model AIR-CB21AG-A-K9

A while back I had this configuration working on Kubuntu Edgy.  It worked out of the box.  I then upgraded to Feisty when it was released.  This update was perfomed on top of Edgy.  Wireless worked wonderfully.  Then I did stupid things.  I decided to see if a Linksys card would work....it did not....then my Cisco card never worked again.  So after much frustration I decided to reload the machine.  So I loaded Ubuntu Feisty....wireless network would not work.  Got message of Restricted Drivers and it listed the Atheros chipset.  I read plenty of information and discovered that the drivers for the card are not enabled by default in Feisty.  I think the drivers are madwifi from madwifi.org.  I followed their "newbie" setup instructions and I get as far as trying to get a DHCP address.  Requests are made but Offers are never received.  

Side note:  Ubuntu was too much for this poor laptop so I installed Xubuntu Gutsy.  Runs great now but still having wireless problems.  

I apologize for the long post.  I am adding the most recent iwconfig and dhclient information.

root@freyja:/home/kevin# ifconfig ath0 up
root@freyja:/home/kevin# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"fatbstrd"  Nickname:""
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:14:BF:6C:FE:EE   
          Bit Rate:24 Mb/s   Tx-Power:20 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:3238-3138-3539-3433-3831   Security mode:restricted
          Power Management:off
          Link Quality=44/70  Signal level=-39 dBm  Noise level=-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

root@freyja:/home/kevin# ifconfig
ath0      Link encap:Ethernet  HWaddr 00:40:96:A8:5F:56  
          inet6 addr: fe80::240:96ff:fea8:5f56/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:67 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:15885 (15.5 KB)

ath0:avah Link encap:Ethernet  HWaddr 00:40:96:A8:5F:56  
          inet addr:169.254.6.143  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth0      Link encap:Ethernet  HWaddr 00:D0:59:15:A1:71  
          inet addr:192.168.0.12  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2d0:59ff:fe15:a171/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:1297 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1025 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1485818 (1.4 MB)  TX bytes:138516 (135.2 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-40-96-A8-5F-56-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24102 errors:0 dropped:0 overruns:0 frame:9
          TX packets:627 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:2075826 (1.9 MB)  TX bytes:43567 (42.5 KB)
          Interrupt:11 

root@freyja:/home/kevin# wlanconfig ath0 list scan
SSID            BSSID              CHAN RATE  S:N   INT CAPS
fatbstrd        00:14:bf:6c:fe:ee   10   54M 39:0   100 EPs 
root@freyja:/home/kevin# iwlist ath0 scan
ath0      Scan completed :
          Cell 01 - Address: 00:14:BF:6C:FE:EE
                    ESSID:"fatbstrd"
                    Mode:Master
                    Frequency:2.457 GHz (Channel 10)
                    Quality=39/70  Signal level=-56 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:18:39:97:E8:C9
                    ESSID:"linksys"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=1/70  Signal level=-94 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100

root@freyja:/home/kevin# iwconfig ath0 essid "fatbstrd"
root@freyja:/home/kevin# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"fatbstrd"  Nickname:""
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:14:BF:6C:FE:EE   
          Bit Rate:36 Mb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:3238-3138-3539-3433-3831   Security mode:restricted
          Power Management:off
          Link Quality=40/70  Signal level=-43 dBm  Noise level=-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

root@freyja:/home/kevin# dhclient ath0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:40:96:a8:5f:56
Sending on   LPF/ath0/00:40:96:a8:5f:56
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by kdchapman1776 on 2007-09-11
No answers given.  Switched to a Linksys wrt54g ver. 2 card and Ndiswrapper.  Finally got back on the network.

---

### Post by dew_jose on 2007-11-03
I had similar issues with the same card. I found that the iwconfig command did nothing and the network administration applet seemingly corrupted the /etc/network/interfaces file.

I was able to fix the problem by modifying /etc/network/interfaces directly then restarting my wireless interface with ifdown/ifup.

---

