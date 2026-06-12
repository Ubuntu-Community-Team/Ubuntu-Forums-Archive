---
title: "need help with acer 5021 nwlci wireless"
date: 2005-12-23
forum: Absolute Beginner Talk
---

### Post by enlightened on 2005-12-23
I have recently admitted to myself that I had too much with Windows, so I decided to install Ubuntu amd64 on my laptop and I think it will be my primary OS from now on. I have most of hardware working but the only thing that doesn't seem to work is my wireless.
It is Broadcom chipset. I did a lot of googles and found that I need to use acer_acpi in order to switch on my wireless and I got as start the wireless. The problem is that my wireless doesn't seem to connect with my access-point. 

------------------------------------------------------
here is some out put I had with dmesg.

root@FrostBite:~# dmesg |grep ndis
[   41.448616] ndiswrapper version 1.1 loaded (preempt=no,smp=no)
[   41.536205] ndiswrapper: driver bcmwl5 (Broadcom,02/11/2005, 3.100.64.0) loaded
[   41.545246] ndiswrapper: using irq 10
[   42.052554] wlan0: ndiswrapper ethernet device 00:0e:9b:ca:84:2a using driver bcmwl5, configuration file 14E4:4318.5.conf

root@FrostBite:~# dmesg |grep acer
[   28.739645] acer_acpi: Acer Laptop ACPI Extras version 0.3
[  165.777799] acer_acpi: Wireless value 1

root@FrostBite:~# iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:11:95:8E:B9:B7
                    ESSID:"brsp1"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-32 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:48 Mb/s
                    Bit Rate:54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

root@FrostBite:~# iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate=54 Mb/s   Tx-Power:25 dBm
          RTS thr:off   Fragment thr:off
          Encryption key:1122-3344-55   Security mode:restricted
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

root@FrostBite:~# ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:0E:9B:CA:84:2A
          inet addr:192.168.0.99  Bcast:192.168.0.255  Mask:255.255.255.0
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Memory:c0204000-c0205fff

root@FrostBite:~#

------------------------------------
here is my access-point info:
Manufacture: D-Link 2100AP
ESSID : brsp1
KEY (HEX): 1122334455
-----------------------------------
How can I make my wireless connect to the access-point?
P.S. I am certain that my key are correct and the wireless is enabled because I can do iwlist scan. Sorry for the long post.

---

