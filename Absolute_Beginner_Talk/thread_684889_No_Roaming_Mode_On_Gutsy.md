---
title: "No Roaming Mode On Gutsy"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by johnfarrow on 2008-02-01
[HTML][FONT="Arial Black"]I can connect to my router on if I enter the ESSID and thenDHCP.  I would like to be able to connect roaming mode. It stops connecting to my router when I select roaming.  What should a fellow do?  I have a IBM Thinkpad I1400 laptop[/FONT][/HTML]

---

### Post by jan quark on 2008-02-01
please post in a normal way...

what is your network device?

please post the results of the following terminal commands

```
iwconfig
```
```
ifconfig
```
```
sudo iwlist scan
```
```
lshw
```
```
lspci
```

---

### Post by johnfarrow on 2008-02-01
john@npgcable:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11b+  ESSID:"belkin54g"  Nickname:"acx v0.3.36"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:11:50:12:C1:8B   
          Bit Rate:11 Mb/s   Tx-Power=18 dBm   Sensitivity=187/255  
          Retry min limit:7   RTS thr:off   
          Power Management:off
          Link Quality=83/100  Signal level=77/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

john@npgcable:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:03:2F:14:3E:D2  
          inet addr:192.168.2.7  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::203:2fff:fe14:3ed2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:77 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:28029 (27.3 KB)  TX bytes:7198 (7.0 KB)
          Interrupt:9 Base address:0x1400 

john@npgcable:~$ 

john@npgcable:~$ sudo iwlist scan
[sudo] password for john:
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:13:10:17:E9:28
                    ESSID:"linksys"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=48/100  Signal level=39/100  Noise level=4/100
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 02 - Address: 00:11:50:12:C1:8B
                    ESSID:"belkin54g"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=81/100  Signal level=77/100  Noise level=1/100
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s

john@npgcable:~$ 


john@npgcable:~$ lshw
WARNING: you should run this program as super-user.
npgcable.com              
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 1
          size: 191MB
     *-cpu
          product: Celeron (Mendocino)
          vendor: Intel Corp.
          physical id: 2
          bus info: cpu@0
          version: 6.6.10
          size: 450MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr up
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 32KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 128KB
     *-pci
          description: Host bridge
          product: M1621
          vendor: ALi Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 05
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-ali module=ali_agp
        *-pci
             description: PCI bridge
             product: PCI to AGP Controller
             vendor: ALi Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: Rage Mobility P/M AGP 2x
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 64
                width: 32 bits
                clock: 33MHz
                capabilities: vga bus_master cap_list
                configuration: latency=32 mingnt=8
        *-communication UNCLAIMED
             description: Communication controller
             product: WinModem 56k
             vendor: Agere Systems
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0 maxlatency=14 mingnt=252
        *-isa
             description: ISA bridge
             product: M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
             vendor: ALi Corporation
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 0a
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-multimedia UNCLAIMED
             description: Multimedia audio controller
             product: ES1969 Solo-1 Audiodrive
             vendor: ESS Technology
             physical id: 8
             bus info: pci@0000:00:08.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=32 maxlatency=24 mingnt=2
        *-ide
             description: IDE interface
             product: M5229 IDE
             vendor: ALi Corporation
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 20
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ALI15x3_IDE latency=32 maxlatency=4 mingnt=2 module=alim15x3
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   product: HTS424040M9AT00
                   vendor: Hitachi
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   capacity: 37GB
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   product: TOSHIBA DVD-ROM SD-C2202
                   vendor: Toshiba
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   capabilities: packet
        *-bridge UNCLAIMED
             description: Bridge
             product: M7101 Power Management Controller [PMU]
             vendor: ALi Corporation
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             configuration: latency=0
        *-pcmcia
             description: CardBus bridge
             product: OZ6812 CardBus Controller
             vendor: O2 Micro, Inc.
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 module=yenta_socket
        *-usb
             description: USB Controller
             product: USB 1.1 Controller
             vendor: ALi Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32 module=ohci_hcd
     *-network
          description: Wireless interface
          product: ACX 100 22Mbps Wireless Interface
          vendor: Texas Instruments
          physical id: 0
          bus info: pci@0000:02:00.0
          logical name: wlan0
          version: 00
          serial: 00:03:2f:14:3e:d2
          width: 32 bits
          clock: 33MHz
          capabilities: bus_master cap_list ethernet physical wireless
          configuration: broadcast=yes driver=acx_pci ip=192.168.2.7 latency=64 module=acx multicast=yes wireless=IEEE 802.11b+
john@npgcable:~$ 

john@npgcable:~$ lspci
00:00.0 Host bridge: ALi Corporation M1621 (rev 05)
00:01.0 PCI bridge: ALi Corporation PCI to AGP Controller (rev 01)
00:06.0 Communication controller: Agere Systems WinModem 56k (rev 01)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+] (rev 0a)
00:08.0 Multimedia audio controller: ESS Technology ES1969 Solo-1 Audiodrive (rev 02)
00:0f.0 IDE interface: ALi Corporation M5229 IDE (rev 20)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU] (rev 09)
00:13.0 CardBus bridge: O2 Micro, Inc. OZ6812 CardBus Controller (rev 05)
00:14.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)
02:00.0 Network controller: Texas Instruments ACX 100 22Mbps Wireless Interface
john@npgcable:~$

---

### Post by ugm6hr on 2008-02-01
I have heard a few people have problems with roaming on Network Manager.  Fortunately, I'm no longer one of them (since Gutsy).

But I did use Wicd successfully as an alternative roaming app in a previous life.  See the link below (Wicd for Wifi).

Worth a try?

---

