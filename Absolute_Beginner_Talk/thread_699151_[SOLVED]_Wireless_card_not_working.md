---
title: "[SOLVED] Wireless card not working"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by Jem00 on 2008-02-17
Hey guys i bought i cheap wireless card off eBay and i want to get it to work on ubuntu 7.10.

On windows XP the driver is an Atheros 4.1.2.133.

This is wat i got from the hardware information in ubuntu
```
03:00.0 Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
        Subsystem: Atheros Communications, Inc. EZ Connect g 802.11g 108Mbps Wireless PCI Adapter
        Flags: bus master, medium devsel, latency 168, IRQ 16
        Memory at 34000000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

```

Can someone tell me wats wrong?

Thanks.

---

### Post by jan quark on 2008-02-17
you can run this in terminal

```
lspci -v | less
```

and check here if your card is supported by ubuntu in the first place

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by Jem00 on 2008-02-17
Its a no name brand so its a bit hard to check...

Any ideas?

---

### Post by Jem00 on 2008-02-17
Why does it tell me <access denied> ?

---

### Post by jan quark on 2008-02-17
can you post the result of these commands
thank you

```
lspci
```
```

sudo lshw -C network
```

```
iwconfig
```

> Why does it tell me <access denied> ?
when and where?

---

### Post by Jem00 on 2008-02-17
lspci


```

00:00.0 Host bridge: ATI Technologies Inc RS300 Host Bridge (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP AGP Bridge
00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01)
00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01)
00:13.2 USB Controller: ATI Technologies Inc EHCI USB Controller (rev 01)
00:14.0 SMBus: ATI Technologies Inc SMBus (rev 17)
00:14.1 IDE interface: ATI Technologies Inc Dual Channel Bus Master PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc Unknown device 434c
00:14.4 PCI bridge: ATI Technologies Inc Unknown device 4342
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01)
01:05.0 VGA compatible controller: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
03:00.0 Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
```

sudo lshw -C network

```



  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth0
       version: 10
       serial: 00:02:3f:d3:8d:16
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.14 latency=128 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network
       description: AR5001-0000-0000
       product: Wireless LAN Reference Card
       vendor: Atheros Communications, Inc.
       physical id: 0
       version: 00
       slot: Socket 0
       resources: irq:16
  *-network
       description: Wireless interface
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications, Inc.
       physical id: 1
       bus info: pci@0000:03:00.0
       logical name: wifi0
       version: 01
       serial: 00:19:e0:86:34:60
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.3.2) ip=192.168.0.15 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
```

iwconfig

```



lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"NADER_9"  Nickname:""
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:09:5B:6D:92:7A   
          Bit Rate:5 Mb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=41/70  Signal level=-53 dBm  Noise level=-94 dBm
          Rx invalid nwid:1  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

It tells me access denied in the ```

Code:

lspci -v | less

 
```

```

lspci -v | less

```

Thanks.

---

### Post by Jem00 on 2008-02-17
lspci -v | less

```
03:00.0 Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
        Subsystem: Atheros Communications, Inc. EZ Connect g 802.11g 108Mbps Wireless PCI Adapter
        Flags: bus master, medium devsel, latency 168, IRQ 16
        Memory at 34000000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

```

---

### Post by Jem00 on 2008-02-17
well? Any ideas?

---

### Post by jan quark on 2008-02-17
it seems so as if your card is recognized by ubuntu and the drivers are enabled

```
 *-network
       description: Wireless interface
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications, Inc.
       physical id: 1
       bus info: pci@0000:03:00.0
       logical name: wifi0
       version: 01
       serial: 00:19:e0:86:34:60
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
     [COLOR="DarkOrange"]  configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.3.2[/COLOR]) ip=192.168.0.15 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
```

try to configure your network connections 

go to system > administration > network
do you see an wireless connection?

try to enable the roaming mode or configure teh setting manually

please post the also the output of
```

cat /etc/network/interfaces
```

---

### Post by Jem00 on 2008-02-17
```
auto lo
iface lo inet loopback


iface ath0 inet dhcp
wireless-key 3bed7e3b65de1945b3923e5502
wireless-essid NADER_9

auto ath0
```

Theres the output

I've tried to set it manually but with no success.

---

### Post by jan quark on 2008-02-17
try to connect with this
```

sudo dhclient ath0
```



wlan can be tricky with ubuntu especially with unknown wlan cards :)

---

### Post by Jem00 on 2008-02-17
Yea that seemed to work.

Will I have to do that everytime i log in to ubuntu?


By the way thanks alot

---

### Post by jan quark on 2008-02-17
usually the file 

/etc/network/interfaces

controls which network is run at start up
and I think your interfaces file you have posted is set up correctly
try to reboot and see if the network starts up automatically if not
we will have to search further :)

---

