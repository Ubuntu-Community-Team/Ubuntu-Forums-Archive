---
title: "linksys Realtek card"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by kausti on 2006-10-01
Hi all,
I have ubuntu 5.10 and linksys realtek rtl8180 card.
I have a win XP partition also and the card works perfectly on windows.
I installed ndiswrapper and think it's installed correctly

dmesg | fgrep ndiswrapper
[4294793.809000] ndiswrapper version 1.1 loaded (preempt=no,smp=no)
[4294793.955000] ndiswrapper: driver net8180 (Realtek,10/07/2004,5.173.1007.2004) loaded
[4294794.017000] ndiswrapper: using irq 10
[4294795.466000] wlan0: ndiswrapper ethernet device 00:0f:66:bd:ae:e8 using driver net8180, configuration file 10EC:8180.5.conf

I followed the instructions at [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

and got till the point I needed to 
 ifconfig wlan0 up
which also executes without giving any errors. Here is output of some other commands

iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:11:D8:EE:C4:20
                    ESSID:"Wireless214"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-64 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0


 iwconfig wlan0
wlan0     IEEE 802.11b  ESSID:"Wireless214"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:11:D8:EE:C4:20
          Bit Rate:11 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3
          RTS thr:2432 B   Fragment thr:2432 B
          Power Management:off
          Link Quality:100/100  Signal level:-63 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


So..ESSID is set! Then I do
sudo iwconfig wlan0 key open **********
The key by the way is correct.
and I have tried all possible orders to execute the commands and I get to this point everytime.
now apparently all I have to is

 ifconfig wlan0 up
which I do and get no error.
But following is the problem.
ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:0F:66:BD:AE:E8
          inet6 addr: fe80::20f:66ff:febd:aee8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:6192 (6.0 KiB)
          Memory:fbbfd000-fbbfd0ff

following output might be more informative

$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 1
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:0f:66:bd:ae:e8
Sending on   LPF/wlan0/00:0f:66:bd:ae:e8
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


I have done a lot of reading all over the place but I am completely lost here](*,) . Any ideas are truely appreciated.
Thanks,
Kaustubh

---

### Post by dmizer on 2006-10-01
try a copy and paste of the following command (exactly as it is)
```
sudo ifdown wlan0&& sudo iwlist wlan0 scan&& sudo iwconfig wlan0 channel 6 essid Wireless214 mode Managed&& sudo ifup wlan0
```

---

