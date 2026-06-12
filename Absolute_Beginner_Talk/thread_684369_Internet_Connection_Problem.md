---
title: "Internet Connection Problem"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by Jidderstein on 2008-02-01
I'm running 7.10 on my Inspiron 6000 laptop trying to connect to the wired network in my home. It used to work flawlessly until a few days ago, when I got a message at startup warning me that I was using restricted drivers. 

Ever since then I haven't been able to get a working wired connection here. I am using the neighbors (slow) wireless router right now and I am able to connect there. The wired connection I am trying to connect to works on all other computers but mine.

Going to the restricted drivers manager and enabling the Software Modem Driver was no help. Any suggestions?

---

### Post by jan quark on 2008-02-01
pls post the results of the following commands

```
iwconfig
```
```
ifconfig
```
```
lspci | grep Ethernet
```
```
lspci
```
```
sudo iwlist scan
```

---

### Post by Jidderstein on 2008-02-01
1) ross@RossLap:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:10:99:68:BA   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=68/100  Signal level=-59 dBm  Noise level=-88 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:57  Invalid misc:6   Missed beacon:36

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

2) ross@RossLap:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:22:EA:18:65  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17905 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2171172 (2.0 MB)  TX bytes:18215 (17.7 KB)
          Interrupt:19 

eth1      Link encap:Ethernet  HWaddr 00:16:6F:13:D4:38  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:6fff:fe13:d438/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:122 errors:0 dropped:6 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:86980548 (82.9 MB)  TX bytes:5627356 (5.3 MB)
          Interrupt:17 Base address:0x6000 Memory:dfdfd000-dfdfdfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:126 errors:0 dropped:0 overruns:0 frame:0
          TX packets:126 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14581 (14.2 KB)  TX bytes:14581 (14.2 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:192.168.1.2  Bcast:255.255.255.254  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2928 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:172.16.236.1  Bcast:172.16.236.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2687 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

3) ross@RossLap:~$ lspci | grep Ethernet
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

4) ross@RossLap:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
03:01.2 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
03:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

5)ross@RossLap:~$ sudo iwlist scan
[sudo] password for ross:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:18:3F:DF:7E:89
                    ESSID:"2WIRE967"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=61/100  Signal level=-64 dBm  
                    Extra: Last beacon: 204ms ago
          Cell 02 - Address: 00:13:10:99:68:BA
                    ESSID:"linksys"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=64/100  Signal level=-62 dBm  
                    Extra: Last beacon: 92ms ago

vmnet1    Interface doesn't support scanning.

vmnet8    Interface doesn't support scanning.

---

### Post by jan quark on 2008-02-01
> eth1 IEEE 802.11g ESSID:"linksys"
Mode:[COLOR="Lime"]Managed [/COLOR]Frequency:2.437 GHz Access Point: 00:13:10:99:68:BA
Bit Rate:54 Mb/s Tx-Power=20 dBm Sensitivity=8/0 

mode managed means you have set the wired network manually, have you?

so perhaps after the restricted drivers for your network adapter were installed you have to reconfigure your network setting ?

system > administration > netowrk see pics

is your wired connection listed there and when you click on the properties is everything configured well ?

---

### Post by Jidderstein on 2008-02-01
It is listed there, and when I click on properties roaming mode is enabled by default and the connection settings are blank. I have tried disabling roaming mode and entering the connection settings myself, but that didn't help either

---

