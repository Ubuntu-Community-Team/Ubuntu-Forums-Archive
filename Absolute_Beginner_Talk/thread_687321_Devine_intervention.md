---
title: "Devine intervention?"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by tomacco0 on 2008-02-04
I was going to go crazy and suddenly, FOR NO APPARENT REASON, the interwebs began operational.
I've read what seems the whole forum and boy have I Google searched.

My other Vista machine. Perfect operation, what can I say
I install Ubuntu, nope sorry you can't have the internet today.

Short and sweet, good things don't last so if anyone could suggest anything to find out if it is stable as is WITHOUT breaking what works XD I'll gladly take their advice.

Eagerly waiting your replies, Tom :KS

---

### Post by jan quark on 2008-02-04
run and post the result of the following terminal commands:

```
iwconfig
```

```
ifconfig
```

```
lspci
```
```

sudo iwlist scan 
```
```

lshw -C network
```

thank you

---

### Post by tomacco0 on 2008-02-05
tom@Linux:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

tom@Linux:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:17:31:8D:5F:D4  
          inet addr:192.168.0.182  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:730 errors:0 dropped:0 overruns:0 frame:0
          TX packets:780 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:352703 (344.4 KB)  TX bytes:121407 (118.5 KB)
          Interrupt:18 Base address:0xc800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:17:9A:AF:0B:F9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wmaster0  Link encap:UNSPEC  HWaddr 00-17-9A-AF-0B-F9-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

tom@Linux:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.5 PIC: VIA Technologies, Inc. K8M890CE I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. Unknown device 6290
00:00.7 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:02.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:0b.0 Network controller: RaLink RT2561/RT61 rev B 802.11g
00:0c.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)
00:0e.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7300 GS] (rev a1)
tom@Linux:~$ sudo iwlist scan
[sudo] password for tom:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1B:2F:F0:60:30
                    ESSID:"NETGEAR"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz
                    Signal level=-60 dBm  
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000002dfd0141def
          Cell 02 - Address: 00:17:9A:F5:20:39
                    ESSID:"Lynx"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz
                    Signal level=-30 dBm  
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000108f8996c4

tom@Linux:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: RT2561/RT61 rev B 802.11g
       vendor: RaLink
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: wmaster0
       version: 00
       serial: 00:17:9a:af:0b:f9
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci latency=64 module=rt61pci multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: e
       bus info: pci@0000:00:0e.0
       logical name: eth0
       version: 10
       serial: 00:17:31:8d:5f:d4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.0.182 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
tom@Linux:~$

---

### Post by tomacco0 on 2008-02-05
So I can ping anything and anyone I like and I can browse the web using firey Firefox yet I can't use Pidgin and update packages etc?
I've played with Software sources and I'm quite sure that's not it.
Either somethings stuffing with it else where or every single server is down (lol).

---

### Post by tomacco0 on 2008-02-05
Uhh.. Bump? :(

---

### Post by anathema415 on 2008-02-05
Are you using a firewall like Firestarter by chance?

---

### Post by tomacco0 on 2008-02-05
I havn't been able to download any packages... So no, I'm not. In fact. I'm in a DMZ

---

### Post by jaytek13 on 2008-02-05
And you can use aim and other instant messengers with the dmz on the windows machine?

---

### Post by tomacco0 on 2008-02-05
LOL I can use anything in the world. I'm probably posting in the wrong forum section for I'm not so much a noob.
I'm dual-booting Vista and Ubuntu with a bit of Mac OS X on the side.. Whoops Did I just say that aloud..
Anyway, everything else on my network operates fine.

---

### Post by tomacco0 on 2008-02-05
Meeeeeeeeer bump.

P.S. Ubuntu just works. I needed to get a few files last night so I rebooted and transferred them straight to my Vista desktop in seconds. Bext linux experiance yet.

---

