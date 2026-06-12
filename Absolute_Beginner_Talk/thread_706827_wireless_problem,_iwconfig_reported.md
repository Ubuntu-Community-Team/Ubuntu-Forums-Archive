---
title: "wireless problem, iwconfig reported"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by PGScooter on 2008-02-24
Hi,
my first post on the forum, yay! I'm using xubuntu 7.10. Wireless worked perfectly for me before but my motherboard died so I put my hd and wireless pci card in my other comp and it booted fine, detected everything, including the wireless card, but for some reason it doesn't connect to the internet. I find this very strange.

Also, what's the best way to see if you successfully connected to the internet without openning up Firefox?

Thanks!
Scott


roddick@Happy:/media/KINGSTON$ iwlist scanning|more
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 02 - Address: 00:1D:5A:AF:E3:79
                    ESSID:"2WIRE698"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=49/100  Signal level=29/100  Noise level=0/100
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s


roddick@Happy:/media/KINGSTON$ sudo ifdown wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 5250
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:e0:98:c6:48:ca
Sending on   LPF/wlan0/00:e0:98:c6:48:ca
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.254 port 67


roddick@Happy:/media/KINGSTON$ sudo ifup wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:e0:98:c6:48:ca
Sending on   LPF/wlan0/00:e0:98:c6:48:ca
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


root@Happy:/media/KINGSTON# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:"2WIRE698"  Nickname:"acx v0.3.36"
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3  
          Retry min limit:7   RTS thr:off   
          Encryption key:3467-0574-81   Security mode:open
          Power Management:off
          Link Quality=49/100  Signal level=29/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by bazzawill on 2008-02-24
The easiest way would be to use ```
 ping google.com
``` and see if you get a response it should give similar output ```
PING google.com (72.14.207.99) 56(84) bytes of data.
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=2 ttl=243 time=261 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=3 ttl=243 time=262 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=4 ttl=243 time=263 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=5 ttl=243 time=268 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=6 ttl=243 time=266 ms

--- google.com ping statistics ---
6 packets transmitted, 5 received, 16% packet loss, time 5023ms
rtt min/avg/max/mdev = 261.431/264.388/268.549/2.627 ms

``` if you are connected

---

### Post by PGScooter on 2008-02-24
Hi bazzawill,

nope, didn't get any reply (said the host was unkown).

Any ideas? thanks

---

### Post by PGScooter on 2008-02-25
I just downloaded a live version of ubuntu 7.10. Would it be a good idea to do a clean install and try everything again or would that not likely make a difference?

does my iwconfig output look ok?

---

### Post by jan quark on 2008-02-25
if you haven't any important data or have done a backup 
you can do a fresh install of ubuntu

it is my very personal opinion that ubuntu handles wlan better than xubuntu
just my feeling, not based on any proofs

---

