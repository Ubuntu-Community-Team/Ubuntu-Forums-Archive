---
title: "unable to use ppp over wireless. not drivers nor router problem.pls help!"
date: 2011-01-08
forum: Any Other OS
---

### Post by Alejanddro on 2011-01-08
Hi everyone and thanks in advance for taking a minute in reading about my problem!!! I'm a newbie btw.

I've been trying for days (reading dozens of posts and guides) to set back again my internet wireless connexion over ppp. I mean "again" because I managed to set it up somehow under Ubuntu 10.10 using pppoeconf and activating it using pon dsl-provider but no luck yet since I fresh installed Mint 10.

So I know that it can work with my router and wireless card. I just can't remember how I did it, or maybe it simply doesn't work with Mint 10.

My internet provider is Alice (Germany). Authentication process: [email]telefonnumber@alice-dsl.de[/email]  and a password. No problem using Ethernet. 


I am posting all the info requested by the guide on getting help, sorry if it makes this post too long!:

Laptop: Asus Z9200VC 

Wireless router: I can connect to it with no problems.

Wireless card: Intel 2200BG; results from commands:

uname -a:
```
Linux asMintus 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686 GNU/Linux
```

lsb_release -a:
```
No LSB modules are available.
Distributor ID:	LinuxMint
Description:	Linux Mint 10 Julia
Release:	10
Codename:	julia
```

lspci: ```
lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
01:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
01:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
01:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
01:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08)
01:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
03:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce Go 6200/6400] (rev a1)
``` 

running "lshw -class network" I get only this: 
```
sudo lshw -C network
PCI (sysfs)  

```
I have no idea if that's good or bad :confused:

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:15:f2:1f:46:63  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::215:f2ff:fe1f:4663/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:339514 errors:0 dropped:0 overruns:0 frame:0
          TX packets:231695 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:492181101 (492.1 MB)  TX bytes:19334899 (19.3 MB)
          Interrupt:20 

eth1      Link encap:Ethernet  HWaddr 00:15:00:35:52:2c  
          inet6 addr: fe80::215:ff:fe35:522c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:147 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:20505 (20.5 KB)
          Interrupt:22 Memory:fa9ff000-fa9fffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2292 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2292 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:138716 (138.7 KB)  TX bytes:138716 (138.7 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:78.48.108.62  P-t-P:213.191.64.33  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:338492 errors:0 dropped:0 overruns:0 frame:0
          TX packets:230459 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:483293954 (483.2 MB)  TX bytes:13215269 (13.2 MB)
```

iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ppp0      no wireless extensions.
```

route -n:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
213.191.64.33   0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 ppp0
0.0.0.0         213.191.64.33   0.0.0.0         UG    0      0        0 ppp0
```

I ran these too because they appear in the thread guide, though they worked obviously over the Ethernet:

ping -c 3 208.67.219.101:
```
PING 208.67.219.101 (208.67.219.101) 56(84) bytes of data.

--- 208.67.219.101 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2014ms
```

ping -c 3 [www.opendns.com:](www.opendns.com:)
```
PING www.opendns.com (208.69.38.150) 56(84) bytes of data.
64 bytes from 208.69.38.150: icmp_req=1 ttl=54 time=215 ms
64 bytes from 208.69.38.150: icmp_req=2 ttl=54 time=220 ms
64 bytes from 208.69.38.150: icmp_req=3 ttl=54 time=208 ms

--- www.opendns.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 10566ms
rtt min/avg/max/mdev = 208.262/215.012/220.790/5.174 ms
```


I've tried with and without encryption. Same result. Connecting to the router is not the problem but the dial or using the ppp connexion. 


Thanks a lot for any help!!!

---

### Post by Alejanddro on 2011-01-20
No ideas? no solution? I practically stopped using linux because of this. I find it sad, I really like it, it has so much potential and free applications available at the software center but... I need internet!  

cable is not an option :(

---

### Post by Alejanddro on 2011-01-20
No ideas? no solution? I practically stopped using linux because of this. I find it sad, I really like it, it has so much potential and free applications available at the software center but... I need internet!  

cable is not an option :(

---

### Post by kermit666 on 2011-07-10
Hi!

I always succeed in setting ppp over wireless up using pppoeconf - a wizard in a terminal that guides you through the process. After you reboot, though, your Network Manager icon might disappear - in that case try [this]("http://ubuntuforums.org/showpost.php?p=9611450&postcount=2") fix (first 2 steps) or in the worst case purge and re-install the network manager from an Ubuntu installation CD.

Hope it helps...

---

