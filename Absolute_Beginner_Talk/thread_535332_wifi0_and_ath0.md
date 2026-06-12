---
title: "wifi0 and ath0"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by lmlypfan on 2007-08-26
I have been using airsnort and recently firestarter.  
After looking at firestarter's log, it seems i am moving data on both interfaces.
Can someone explain?

Which one is my wireless card?  What is the ath0 interface?

Please advise,

Bo

---

### Post by lmlypfan on 2007-08-26
should I move this to the networking forum?

---

### Post by nonewmsgs on 2007-08-26
ath0 is atheros madwifi.  this is what you are using.  

wifi0 doesnt do much except look pretty AFAIK.

---

### Post by lmlypfan on 2007-08-26
so why is wifi0 moving the most data on my laptop?

---

### Post by nonewmsgs on 2007-08-26
maybe it's an alias there so some programs are happy?  im not sure.  i do know when you set it up all the commands in the console are ath0 ones.

---

### Post by kevdog on 2007-08-26
Please post
lshw -C network
ifconfig
iwlist scan

Maybe this will help us make sense what is going on!

---

### Post by nosrednaekim on 2007-08-26
wifi0 is the representation of the actual hardware, used for creating APs and ad-hoc stuff. Ath0 is a "frontend" to wifi0 which actually does the connecting to the remote AP.

---

### Post by lmlypfan on 2007-08-26
lshw -C network

*-network               
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VM (KM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@02:08.0
       logical name: eth0
       version: 42
       serial: 00:02:a5:b7:de:9d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI firmware=N/A latency=66 maxlatency=56 mingnt=8 multicast=yes
       resources: iomemory:40100000-40100fff ioport:2800-283f irq:11
  *-network
       description: Wireless interface
       product: AR5005G 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@03:00.0
       logical name: wifi0
       version: 01
       serial: 00:15:e9:73:a2:0a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.1.21 latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:3c000000-3c00ffff irq:11


ifconfig

ath0      Link encap:Ethernet  HWaddr 00:15:E9:73:A2:0A  
          inet addr:192.168.1.21  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:e9ff:fe73:a20a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:83556 errors:0 dropped:0 overruns:0 frame:0
          TX packets:67343 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:85087049 (81.1 MiB)  TX bytes:10780357 (10.2 MiB)

eth0      Link encap:Ethernet  HWaddr 00:02:A5:B7:DE:9D  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:31 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2440 (2.3 KiB)  TX bytes:2440 (2.3 KiB)

wifi0     Link encap:UNSPEC  HWaddr 00-15-E9-73-A2-0A-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1081350 errors:0 dropped:0 overruns:0 frame:389422
          TX packets:74767 errors:42 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:191295094 (182.4 MiB)  TX bytes:14108372 (13.4 MiB)
          Interrupt:11 


iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:12:0E:7C:B4:D5
                    ESSID:"michelle"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=5/94  Signal level=-90 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
          Cell 02 - Address: 00:1A:70:F4:D1:09
                    ESSID:"wilson"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=3/94  Signal level=-92 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 03 - Address: 00:0C:41:BD:F2:0F
                    ESSID:"weenrodeo"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=38/94  Signal level=-57 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK

---

### Post by Richard2007 on 2008-02-13
I have the exact same issue, and it didn't happen until the kernel update on ubuntustudio. When I do the iwlist I am now receiving from the router but not transmitting. Or at least all web pages fail.

I have an amd system so no mad wifi applies, so anyone how do I get this fully up?

Richard:guitar:

---

### Post by Richard2007 on 2008-02-14
Ok so it worked I issued sudo ifconfig wifi0 down then hunted in synapic for madwifi, it gave me a restricted fil;e which i promptly uninstalled and I was up!

BUT THEN I did the update on gutsy all 187 files and noticed a network manager file update. After reboot, driver is completely gone, Ill have to reinstall from scratch.

OH boy gutsy is fun.

Richard:guitar:

---

### Post by Richard_2007 on 2008-05-04
Ok this first happened on gutsy now again on heron. The fix is to use synaptic and remove madwifi, then reboot and reinstall under the ubuntu restricted drivers for madwifi. A quick config under the network manager and Im back posting this.

---

