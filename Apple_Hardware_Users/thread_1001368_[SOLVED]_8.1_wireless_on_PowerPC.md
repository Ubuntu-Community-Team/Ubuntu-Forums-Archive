---
title: "[SOLVED] 8.1 wireless on PowerPC"
date: 2008-12-03
forum: Apple Hardware Users
---

### Post by meinzy on 2008-12-03
Been searching posts for hours trying to get my wireless to work on my G5 PPC.  Installed Ubuntu 8.1 successfully.  Hardware Drivers shows B43 wireless driver activated.  Network Manager shows nothing under Wireless.  I've been punching in all kinds of commands (linux noob) in terminal, per other posts, and have gotten nowhere.  At one point, looking at network configurations in the terminal, I could see my wireless router.  But can't get it to work in Ubuntu.  Please help me get wireless configured so I can go all Ubuntu.  Thanks.****

---

### Post by pytheas22 on 2008-12-04
The b43 driver requires firmware to work, which is probably what's wrong.  This firmware is not shipped with Ubuntu by default because it's not open-source.  But if you type this command, you should be prompted to download and install the necessary firmware automatically (provided you are connected to the Internet via ethernet first):
```

sudo apt-get update
sudo apt-get install b43-fwcutter
```

Then reboot.  If your Internet works now, great.  If not, please post the output of the following commands:

```
lshw -C Network
lspci -nn | grep -i broadcom
ls /lib/firmware
sudo iwlist scan
dmesg | grep -e b43 -e wlan
```

It's also possible that there's a weird problem related to the fact that you have a PPC processor, but hopefully not, because that could be trickier to solve.

---

### Post by meinzy on 2008-12-04
Still not working.   Here is the info you requested:

zy@ubuntuMAC:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0001:02:01.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=16 module=ssb
  *-network
       description: Ethernet interface
       product: K2 GMAC (Sun GEM)
       vendor: Apple Computer Inc.
       physical id: f
       bus info: pci@0001:04:0f.0
       logical name: eth0
       version: 00
       serial: 00:0d:93:3e:51:40
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master ethernet physical
       configuration: broadcast=yes driver=sungem driverversion=0.98 ip=192.168.2.16 latency=16 maxlatency=64 mingnt=64 module=sungem multicast=yes
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:11:24:26:9b:6e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 26:38:e0:49:9d:53
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

Can't do next command since I don't know how to make the vertical bar?

---

### Post by meinzy on 2008-12-04
OK...Now I'll continue:

zy@ubuntuMAC:~$ lspci -nn | grep -i broadcom
0001:02:01.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
0001:05:0c.0 IDE interface [0101]: Broadcom K2 SATA [1166:0240]
zy@ubuntuMAC:~$ ls /lib/firmware
b43  b43legacy
zy@ubuntuMAC:~$ sudo iwlist scan
[sudo] password for zy: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:17:3F:BF:DB:CF
                    ESSID:"Belkin_N_Wireless_BFDBCF"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=66/100  Signal level=-59 dBm  Noise level=-67 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Extra:tsf=000000ba4b88267e

pan0      Interface doesn't support scanning.

zy@ubuntuMAC:~$ dmesg | grep -e b43 -e wlan
[   12.687744] b43-phy0: Broadcom 4306 WLAN found
[   25.280007] input: b43-phy0 as /class/input/input5
[   25.840034] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   27.099560] Registered led device: b43-phy0::tx
[   27.100162] Registered led device: b43-phy0::rx
[   27.100614] Registered led device: b43-phy0::radio
[   27.060074] wlan0: Initial auth_alg=0
[   27.060087] wlan0: authenticate with AP 00:17:3f:bf:db:cf
[   27.061677] wlan0: RX authentication from 00:17:3f:bf:db:cf (alg=0 transaction=2 status=0)
[   27.061682] wlan0: authenticated
[   27.061685] wlan0: associate with AP 00:17:3f:bf:db:cf
[   27.064260] wlan0: RX AssocResp from 00:17:3f:bf:db:cf (capab=0x421 status=0 aid=4)
[   27.064266] wlan0: associated
[   27.064270] wlan0: CTS protection enabled (BSSID=00:17:3f:bf:db:cf)
[   27.064317] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[   27.064320] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[   27.064323] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[   27.064325] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[   27.066247] wlan0: disassociate(reason=3)
[   27.067328] wlan0: disassociate(reason=3)
[   30.280131] ADDRCONF(NETDEV_UP): wlan0: link is not ready


Looks to me like the wireless card is seeing my router when in terminal.  But doesn't show up within the GUI.

---

### Post by meinzy on 2008-12-04
I'm a complete N00b who has been running Ubuntu on my PC laptop for about a week.  Don't want to deal with two different OS's so want Ubuntu on my MAC also.  Let me guess at something I see from all that gobbledegook in my previous posts:

In the firmware library I notice both "b43 b43legacy" listed.  Could there be a conflict there?

---

### Post by cyberdork33 on 2008-12-04
> **meinzy said:**
> In the firmware library I notice both "b43 b43legacy" listed.  Could there be a conflict there?
Depending on which Broadcom card you are using, you may need b43legacy.

[http://linuxwireless.org/en/users/Drivers/b43#b43andb43legacy](http://linuxwireless.org/en/users/Drivers/b43#b43andb43legacy)

---

### Post by pytheas22 on 2008-12-04
Thanks for all that information.

Incidentally, I have the same exact wireless card (Broadcom 4306 14e4:4320) in my Pentium IV Dell, and it works fine on Ubuntu 8.10 using the b43 driver.  So you've got the right driver, and the firmware is there.

What actually appears to be happening to you is that you are connecting successfully to the router, but for some reason are getting disassociated immediately after.  This problem may be related to b43, but it could also be either your router doing something strange, or Network Manager (the connection manager) being stupid, or possibly out-of-date firmware.

So let's first rule out Network Manager by connecting without it.  To do that, reboot your computer, then run these commands, which will get you online manually and take NM out of the picture.  Please post all output from these commands (run them in this order):
```

sudo killall NetworkManager
sudo iwconfig wlan0 mode managed channel 6 essid "Belkin_N_Wireless_BFDBCF"
sudo dhclient wlan0
dmesg | tail
```

If this works, you will get an IP address and be able to browse web pages.  If it doesn't work, we can try some other things.

---

### Post by meinzy on 2008-12-04
OK...now my wired network doesn't work so I'm using my laptop to communicate.  The last querry returned "DHCPDISCOVER on wLan0 to 255.255.255.255 port 67 interval 10".  

So...I can no longer get on the internet via wireless or LAN.

---

### Post by pytheas22 on 2008-12-04
Yes, sorry, killing NM would have caused you to lose ethernet--I didn't think of that.  You could get the ethernet connection back by typing 'sudo dhclient eth0' or by rebooting your computer.
```

The last querry returned "DHCPDISCOVER on wLan0 to 255.255.255.255 port 67 interval 10". 
```

Is that all it said?  If dhclient works, it should look similar to:


```
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:19:21:85:0d:87
Sending on   LPF/eth0/00:19:21:85:0d:87
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.47 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.47 from 192.168.1.1
**bound to 192.168.1.47 -- renewal in 36278 seconds.**

```

The last line is key because it means you have an IP address.  Do you not get an IP address even after several seconds when you type:
```

sudo iwconfig wlan0 mode managed channel 6 essid "Belkin_N_Wireless_BFDBCF"
sudo dhclient wlan0
```

---

### Post by meinzy on 2008-12-04
Here is the full listing (now that the Lan is back up):

zy@ubuntuMAC:~$ sudo iwconfig wlan0 mode managed channel 6 essid "Belkin_N_Wirewless_BFDBCF"
zy@ubuntuMAC:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:11:24:26:9b:6e
Sending on   LPF/wlan0/00:11:24:26:9b:6e
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
dmesg DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
|DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
dmesg | DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
tail
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10


redid the lines you suggested and got:

zy@ubuntuMAC:~$ sudo iwconfig wlan0 mode managed channel 6 essid "Belkin_N_Wireless_BFDBCF"
zy@ubuntuMAC:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 10156
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:11:24:26:9b:6e
Sending on   LPF/wlan0/00:11:24:26:9b:6e
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPOFFER of 192.168.2.15 from 192.168.2.1
DHCPREQUEST of 192.168.2.15 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.2.15 from 192.168.2.1
bound to 192.168.2.15 -- renewal in 919070893 seconds.


Now I can't use the Internet again...I copied the info into Open Office and transferred to my laptop to send this message.

---

### Post by meinzy on 2008-12-04
Rebooted and can now use Internet via Lan.  No wireless.  I've got to take my Mom to the doctor and will be gone for several hours.  I'll check back later.

Thanks for your help.  I'm sooooooooooo close to being all Ubuntu.

Zy

---

### Post by pytheas22 on 2008-12-04
From the output you posted, it seems like you did successfully connect using the 'sudo dhclient wlan0' on the second try (not sure why it didn't work on the first).  So when you get back, please try rebooting again, then run these commands, in this order, and post the output:
```

sudo iwconfig wlan0 mode managed channel 6 essid "Belkin_N_Wireless_BFDBCF"
sudo dhclient wlan0
sudo dhclient wlan0
dmesg | tail
dmesg | grep -e wlan -e b43
ifconfig wlan0
iwconfig wlan0
wget google.com
host google.com
ping -c 3 74.125.45.100
ping -c 3 192.168.2.1
```

Sorry to ask for so much, but this should help to clear things up.

---

### Post by meinzy on 2008-12-04
Here it is:

zy@ubuntuMAC:~$ sudo iwconfig wlan0 mode managed channel 6 essid "Belkin_N_Wireless_BFDBCF"
[sudo] password for zy: 
zy@ubuntuMAC:~$ sudo iwconfig wlan0 mode managed channel 6 essid "Belkin_N_Wireless_BFDBCF"
zy@ubuntuMAC:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:11:24:26:9b:6e
Sending on   LPF/wlan0/00:11:24:26:9b:6e
Sending on   Socket/fallback
DHCPREQUEST of 192.168.2.15 on wlan0 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.2.15 on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
Trying recorded lease 192.168.2.15
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.

--- 192.168.2.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.
zy@ubuntuMAC:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 5658
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:11:24:26:9b:6e
Sending on   LPF/wlan0/00:11:24:26:9b:6e
Sending on   Socket/fallback
DHCPREQUEST of 192.168.2.15 on wlan0 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.2.15 on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
Trying recorded lease 192.168.2.15
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.

--- 192.168.2.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.
zy@ubuntuMAC:~$ dmesg | tail
[   73.313691] wlan0: associated
[   73.313698] wlan0: CTS protection enabled (BSSID=00:17:3f:bf:db:cf)
[   73.313740] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[   73.313744] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[   73.313748] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[   73.313751] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[   73.314799] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   73.315332] wlan0: disassociate(reason=3)
[   68.721436] wlan0: disassociate(reason=3)
[   74.328074] wlan0: no IPv6 routers present
zy@ubuntuMAC:~$ dmesg | grep -e wlan -e b43
[   12.352407] b43-phy0: Broadcom 4306 WLAN found
[   25.222704] input: b43-phy0 as /class/input/input5
[   25.720030] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   26.967444] Registered led device: b43-phy0::tx
[   26.968074] Registered led device: b43-phy0::rx
[   26.968547] Registered led device: b43-phy0::radio
[   27.845728] wlan0: Initial auth_alg=0
[   27.845740] wlan0: authenticate with AP 00:17:3f:bf:db:cf
[   27.847356] wlan0: RX authentication from 00:17:3f:bf:db:cf (alg=0 transaction=2 status=0)
[   27.847360] wlan0: authenticated
[   27.847363] wlan0: associate with AP 00:17:3f:bf:db:cf
[   27.850911] wlan0: RX AssocResp from 00:17:3f:bf:db:cf (capab=0x421 status=0 aid=4)
[   27.850915] wlan0: associated
[   27.850921] wlan0: CTS protection enabled (BSSID=00:17:3f:bf:db:cf)
[   27.850970] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[   27.850973] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[   27.850976] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[   27.850978] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[   27.852828] wlan0: disassociate(reason=3)
[   27.853477] wlan0: disassociate(reason=3)
[   29.303048] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   71.327071] wlan0: Initial auth_alg=0
[   71.327081] wlan0: authenticate with AP 00:17:3f:bf:db:cf
[   67.397615] wlan0: RX authentication from 00:17:3f:bf:db:cf (alg=0 transaction=2 status=0)
[   67.397620] wlan0: authenticated
[   67.397623] wlan0: associate with AP 00:17:3f:bf:db:cf
[   71.332733] wlan0: RX ReassocResp from 00:17:3f:bf:db:cf (capab=0x421 status=0 aid=4)
[   71.332741] wlan0: associated
[   71.332749] wlan0: CTS protection enabled (BSSID=00:17:3f:bf:db:cf)
[   71.332795] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[   71.332799] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[   71.332802] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[   71.332805] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[   71.333311] wlan0: disassociate(reason=3)
[   71.345537] wlan0: disassociate(reason=3)
[   68.714346] wlan0: Initial auth_alg=0
[   68.714356] wlan0: authenticate with AP 00:17:3f:bf:db:cf
[   68.715973] wlan0: RX authentication from 00:17:3f:bf:db:cf (alg=0 transaction=2 status=0)
[   68.715979] wlan0: authenticated
[   68.715982] wlan0: associate with AP 00:17:3f:bf:db:cf
[   73.313685] wlan0: RX ReassocResp from 00:17:3f:bf:db:cf (capab=0x421 status=0 aid=4)
[   73.313691] wlan0: associated
[   73.313698] wlan0: CTS protection enabled (BSSID=00:17:3f:bf:db:cf)
[   73.313740] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[   73.313744] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[   73.313748] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[   73.313751] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[   73.314799] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   73.315332] wlan0: disassociate(reason=3)
[   68.721436] wlan0: disassociate(reason=3)
[   74.328074] wlan0: no IPv6 routers present
zy@ubuntuMAC:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:11:24:26:9b:6e  
          inet6 addr: fe80::211:24ff:fe26:9b6e/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:208 (208.0 B)

zy@ubuntuMAC:~$ iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:"Belkin_N_Wireless_BFDBCF"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:17:3F:BF:DB:CF   
          Bit Rate=2 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Link Quality=58/100  Signal level=-67 dBm  Noise level=-68 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

zy@ubuntuMAC:~$ wget google.com
--2008-12-04 15:20:56--  [http://google.com/](http://google.com/)
Resolving google.com... 209.85.171.100
Connecting to google.com|209.85.171.100|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://www.google.com/](http://www.google.com/) [following]
--2008-12-04 15:20:56--  [http://www.google.com/](http://www.google.com/)
Resolving [www.google.com](www.google.com)... 74.125.47.147
Connecting to [www.google.com|74.125.47.147|:80](www.google.com|74.125.47.147|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `index.html.1'

    [ <=>                                   ] 5,856       --.-K/s   in 0.02s   

2008-12-04 15:20:56 (267 KB/s) - `index.html.1' saved [5856]

zy@ubuntuMAC:~$ host google.com
google.com has address 209.85.171.100
google.com mail is handled by 10 smtp2.google.com.
google.com mail is handled by 10 smtp3.google.com.
google.com mail is handled by 10 smtp4.google.com.
google.com mail is handled by 10 smtp1.google.com.
zy@ubuntuMAC:~$ ping -c 3 74.125.45.100
PING 74.125.45.100 (74.125.45.100) 56(84) bytes of data.
64 bytes from 74.125.45.100: icmp_seq=1 ttl=241 time=21.1 ms
64 bytes from 74.125.45.100: icmp_seq=2 ttl=241 time=21.2 ms
64 bytes from 74.125.45.100: icmp_seq=3 ttl=241 time=21.6 ms

--- 74.125.45.100 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2008ms
rtt min/avg/max/mdev = 21.185/21.392/21.699/0.251 ms
zy@ubuntuMAC:~$ ping -c 3 192.168.2.1
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
64 bytes from 192.168.2.1: icmp_seq=1 ttl=64 time=0.301 ms
64 bytes from 192.168.2.1: icmp_seq=2 ttl=64 time=0.278 ms
64 bytes from 192.168.2.1: icmp_seq=3 ttl=64 time=0.279 ms

--- 192.168.2.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 0.278/0.286/0.301/0.010 ms

---

### Post by pytheas22 on 2008-12-04
Thanks again for the output.  Unfortunately, I'm still not positive what's going on--it looks like you get an IP address on your wired interface, but it gets lost immediately.  I think we're close, though.

Please post the output of these commands, in this order, with your ethernet cable unplugged the whole time (you can plug it in after running these commands in order to be able to post the output):
```

sudo iwconfig wlan0 mode managed channel 6 essid "Belkin_N_Wireless_BFDBCF"
sudo dhclient wlan0
ifconfig wlan0
wget google.com
dmesg | tail
```

---

### Post by meinzy on 2008-12-04
Here we go:

zy@ubuntuMAC:~$ sudo iwconfig wlan0 mode managed channel 6 essid "Belkin_N_Wireless_BFDBCF"
zy@ubuntuMAC:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 10123
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:11:24:26:9b:6e
Sending on   LPF/wlan0/00:11:24:26:9b:6e
Sending on   Socket/fallback
DHCPREQUEST of 192.168.2.15 on wlan0 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.2.15 on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
Trying recorded lease 192.168.2.15
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.

--- 192.168.2.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.
zy@ubuntuMAC:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:11:24:26:9b:6e  
          inet6 addr: fe80::211:24ff:fe26:9b6e/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:570 (570.0 B)

zy@ubuntuMAC:~$ wget google.com
--2008-12-04 19:34:40--  [http://google.com/](http://google.com/)
Resolving google.com... failed: Name or service not known.
wget: unable to resolve host address `google.com'
zy@ubuntuMAC:~$ dmesg | tail
[ 1263.679896] wlan0: associate with AP 00:17:3f:bf:db:cf
[ 1263.682680] wlan0: RX ReassocResp from 00:17:3f:bf:db:cf (capab=0x421 status=0 aid=5)
[ 1263.682686] wlan0: associated
[ 1263.682694] wlan0: CTS protection enabled (BSSID=00:17:3f:bf:db:cf)
[ 1263.682749] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[ 1263.682752] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[ 1263.682754] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[ 1263.682757] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[ 1263.684112] wlan0: disassociate(reason=3)
[ 1263.684843] wlan0: disassociate(reason=3)
zy@ubuntuMAC:~$ 

I really appreciate your determination.  Hope this helps.  It's all greek to me.

---

### Post by pytheas22 on 2008-12-05
Please first try running these commands, with your ethernet cable unplugged:
```

sudo iwconfig wlan0 mode managed channel 6 essid "Belkin_N_Wireless_BFDBCF"
sudo dhclient3 wlan0
```

That may get you online.  If not, we can try the next thing...

---

### Post by meinzy on 2008-12-05
Hmmm...doesn't seem to have worked.  I unplugged cable and still no internet or options to enable wireless.  So onward we slog.  I'm taking Ma to the hospital today to get a pacemaker so I may not be able to check back till later today.

Thanks many times for hanging in there,
Zy

zy@ubuntuMAC:~$ sudo iwconfig wlan0 mode managed channel 6 essid "Belkin_N_Wireless_BFDBCF"
[sudo] password for zy: 
zy@ubuntuMAC:~$ sudo iwconfig wlan0 mode managed channel 6 essid "Belkin_N_Wireless_BFDBCF"
zy@ubuntuMAC:~$ sudo dhclient3 wlan0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:11:24:26:9b:6e
Sending on   LPF/wlan0/00:11:24:26:9b:6e
Sending on   Socket/fallback
DHCPREQUEST of 192.168.2.15 on wlan0 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.2.15 on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
Trying recorded lease 192.168.2.15
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.

--- 192.168.2.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.
zy@ubuntuMAC:~$

---

### Post by pytheas22 on 2008-12-05
Sorry that that didn't help.

The next thing to try is to use [wicd]("http://wicd.sourceforge.net") to connect instead of Network Manager.  To install wicd, run these commands:
```

echo 'deb http://apt.wicd.net intrepid extras' | sudo tee -a /etc/apt/sources.list
wget -q http://apt.wicd.net/wicd.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install wicd
```

After running those commands, you should be able to launch wicd from your Applications>Internet menu.  Please try connecting to your wireless network with it and see if you have any better luck.

Also, note that installing wicd will require you to uninstall Network Manager.  If you want NM back later for any reason, just type 'sudo apt-get install network-manager-gnome'

If wicd doesn't help, the only other thing I can think of is to use bcm43xx, and older driver for this card, instead of b43.  bcm43xx may work better, but unfortunately it's not included anymore in Ubuntu 8.10, so you'd have to switch to 8.04 or earlier.

But it's very puzzling to me that b43 won't work, because as I said, I have the exact same wireless card and it works fine under b43 on Ubuntu 8.10.

I would just recommend trying ndiswrapper, but it won't work on ppc.

Hope things went well for your mom...

---

### Post by meinzy on 2008-12-05
You are the MAN!!!!   That did it!  That was a tough slog but you got me over my hesitancy about using the Terminal.  I'm old school from back in the DOS days and dreaded going back there.  But I'm now over it.  I also received my Official Ubuntu Manual today and will plow through it.

Your persistence has inspired me to return the favor to some other poor noob trying to get up and running, as soon as I get more familiar with Ubuntu.

I have one last question...Will I need to manually connect every time at boot up?  Or is there a simple script or something I can do to automate the process?

Thanks again,
Zy

---

### Post by meinzy on 2008-12-05
Isn't there some way to note that the problem was solved for this thread?

NEVERMIND...found it.

---

### Post by pytheas22 on 2008-12-05
Glad to hear it's finally solved :)  I guess it was a problem with Network Manager all along, not your wireless driver itself.

> I have one last question...Will I need to manually connect every time at boot up? Or is there a simple script or something I can do to automate the process?


Yes, you can do this.  First, make sure that you check the box in wicd that says 'Automatically connect to this network' for your network.  Then go to System>Preferences>Sessions.  Under the 'Startup Programs' tab, click add.  Create the new entry as follows:
```

name: wicd
command: wicd-client --no-tray
description: whatever you want
```

From now on, wicd will be launched automatically whenever you log into your desktop, and should auto-connect to your wireless network as long as it's in range.  I should mention that I've had trouble in the past making wicd actually auto-connect, though, so if it doesn't seem to work, let me know.
> 
I'm old school from back in the DOS days and dreaded going back there. But I'm now over it.

I think you'll find that the command-line in Linux is vastly superior to the kind of stuff from the DOS days, both in terms of ease of use and power.  I was terrified of the command-line as well when I was new to Linux, but now I find myself using it a lot just because it can be soooo much faster than using a GUI.  It's also more user-friendly than DOS because of things like color-coded text, tab auto-completion (i.e., start typing a command and press tab and the computer will finish it for you), the man pages, etc.  I'm sure your book will contain all the details.

I hope you continue to have fun with Ubuntu!  And that you'll try to help others here as time allows.

---

