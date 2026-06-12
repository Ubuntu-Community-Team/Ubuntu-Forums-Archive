---
title: "ethernet connection dropping on Linux Mint"
date: 2012-05-07
forum: Any Other OS
---

### Post by X-jo on 2012-05-07
:dmesg

> [83903.387634] atl1c 0000:01:00.0: irq 43 for MSI/MSI-X
[83903.387739] atl1c 0000:01:00.0: atl1c: eth0 NIC Link is Up<10 Mbps Half Duplex>
[84964.096716] atl1c 0000:01:00.0: atl1c: eth0 NIC Link is Down
[84966.229340] atl1c 0000:01:00.0: atl1c: eth0 NIC Link is Up<10 Mbps Half Duplex>
[84971.807822] atl1c 0000:01:00.0: irq 43 for MSI/MSI-X
[84971.807927] atl1c 0000:01:00.0: atl1c: eth0 NIC Link is Up<10 Mbps Half Duplex>
[84977.338789] atl1c 0000:01:00.0: atl1c: eth0 NIC Link is Down
[84979.479611] atl1c 0000:01:00.0: atl1c: eth0 NIC Link is Up<10 Mbps Half Duplex>
[84984.788520] atl1c 0000:01:00.0: irq 43 for MSI/MSI-X
[84984.788624] atl1c 0000:01:00.0: atl1c: eth0 NIC Link is Up<10 Mbps Half Duplex>
[85328.908064] atl1c 0000:01:00.0: atl1c: eth0 NIC Link is Down
[85331.046509] atl1c 0000:01:00.0: atl1c: eth0 NIC Link is Up<10 Mbps Half Duplex>
[85336.265801] atl1c 0000:01:00.0: irq 43 for MSI/MSI-X
[85336.265905] atl1c 0000:01:00.0: atl1c: eth0 NIC Link is Up<10 Mbps Half Duplex>
[86152.111070] usb 2-1.2.3: reset high speed USB device using ehci_hcd and address 6
[86518.038391] atl1c 0000:01:00.0: atl1c: eth0 NIC Link is Down
[86520.177049] atl1c 0000:01:00.0: atl1c: eth0 NIC Link is Up<10 Mbps Half Duplex>
[86525.495829] atl1c 0000:01:00.0: irq 43 for MSI/MSI-X
[86525.495930] atl1c 0000:01:00.0: atl1c: eth0 NIC Link is Up<10 Mbps Half Duplex>
[87004.174316] atl1c 0000:01:00.0: atl1c: eth0 NIC Link is Down
[87006.313711] atl1c 0000:01:00.0: atl1c: eth0 NIC Link is Up<10 Mbps Half Duplex>
[87011.772416] atl1c 0000:01:00.0: irq 43 for MSI/MSI-X
[87011.772520] atl1c 0000:01:00.0: atl1c: eth0 NIC Link is Up<10 Mbps Half Duplex>


i get these in my dmesg everytime. Is this a problem?

I've given every possible info I could, do let me know if i missed any. I am using a wired connection.

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:26:6c:bd:04:a8  
          inet addr:10.10.0.19  Bcast:10.10.0.255  Mask:255.255.255.0
          inet6 addr: fe80::226:6cff:febd:4a8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:142743 errors:57 dropped:10 overruns:0 frame:20
          TX packets:85881 errors:0 dropped:0 overruns:0 carrier:113
          collisions:26701 txqueuelen:1000 
          RX bytes:176687869 (176.6 MB)  TX bytes:9076908 (9.0 MB)
          Interrupt:43 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:203 errors:0 dropped:0 overruns:0 frame:0
          TX packets:203 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17646 (17.6 KB)  TX bytes:17646 (17.6 KB)
```cat /etc/network/interfaces
```
auto lo
iface lo inet loopback
```netstat -rn
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
10.10.0.0       0.0.0.0         255.255.255.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         10.10.0.1       0.0.0.0         UG        0 0          0 eth0
```inxi -N
```
Network:   Card-1 Atheros AR9285 Wireless Network Adapter (PCI-Express) driver ath9k
           Card-2 Atheros AR8152 v2.0 Fast Ethernet driver atl1c
```lspci -v | grep Ethernet -A 1
```
01:00.0 Ethernet controller: Atheros Communications AR8152 v2.0 Fast Ethernet (rev c1)
    Subsystem: Toshiba America Info Systems Device ff1e
```
thanks in advance

---

### Post by Perfect Storm on 2012-05-07
Moved to Other OS/Distro Talk.

---

