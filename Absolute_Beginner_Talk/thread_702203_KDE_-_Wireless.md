---
title: "KDE - Wireless"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by Kasyx on 2008-02-20
Hi, I am having trouble with my wireless networking in KDE. There doesn't seem to be a way to scan for wireless networks, the only way I could get it to connect was by manually adding the SSID and WPA key in the Network Settings. What can I do to just get it to scan for wireless networks and then let me connect to one through KnetworkManager? Right now when I check my connection status it tells me there is no active device. Help :(

---

### Post by jan quark on 2008-02-20
please post the results of these terminal commands

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

lspci
```

```
sudo lshw -C network
```

---

### Post by Kasyx on 2008-02-20
Here you go, thanks :)

iwconfig
```
eth1      unassociated  ESSID:"wlan1"  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:775  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```


ifconfig
```
eth1      Link encap:Ethernet  HWaddr 00:16:6F:C3:1B:E8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:16 errors:775 dropped:775 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:11889 (11.6 KB)
          Interrupt:17 Base address:0x6000 Memory:bc008000-bc008fff 

eth1:avah Link encap:Ethernet  HWaddr 00:16:6F:C3:1B:E8  
          inet addr:169.254.8.50  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0x6000 Memory:bc008000-bc008fff
```

sudo iwlist scan
```
eth1      Scan completed :
          Cell 01 - Address: 00:02:6F:44:15:79
                    ESSID:"wlan1"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=33/100  Signal level=-32 dBm  
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 376ms ago
          Cell 02 - Address: 00:19:F6:00:02:82
                    ESSID:"wlan2"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=33/100  Signal level=-80 dBm  
                    Extra: Last beacon: 276ms ago
          Cell 03 - Address: 00:13:D3:84:D6:69
                    ESSID:"wlan-ap"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=35/100  Signal level=-79 dBm  
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 7876ms ago
```

lspci
```
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 10)
06:00.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:00.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:00.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:00.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
06:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
```

sudo lshw -C network
```
*-network               
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:e0:91:0f:ec:65
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.18 duplex=full firmware=N/A ip=192.168.0.91 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       logical name: eth1
       version: 05
       serial: 00:16:6f:c3:1b:e8
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.0kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=32 link=no maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=unassociated
```

---

### Post by jan quark on 2008-02-20
the drivers for your card seem to be active
but you are on the wrong channel I guess

see here:

```
eth1      unassociated  ESSID:"wlan1"  
          Mode:Managed [COLOR="DarkOrange"] Channel=0[/COLOR]  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:775  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth1      Scan completed :
          Cell 01 - Address: 00:02:6F:44:15:79
                    ESSID:"wlan1"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                   [COLOR="DarkOrange"] Channel:6[/COLOR]
```

please post the output of:

```
cat /etc/network/interfaces
```

---

### Post by jan quark on 2008-02-20
also try to change the channel

```
sudo iwconfig eth1 channel 6
```

---

### Post by Kasyx on 2008-02-20
```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0


iface eth1 inet dhcp
wireless-essid wlan1
wireless-key xxxxxxxxxxxxxx

auto eth1

iface eth0 inet dhcp

auto eth0

```

I attempted to change the channel to 6, how would I check if this fixed anything? I really appreciate your help with this

---

