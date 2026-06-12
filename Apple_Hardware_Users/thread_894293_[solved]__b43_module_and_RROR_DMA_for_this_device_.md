---
title: "[solved]  b43 module and RROR: DMA for this device not supported and no PIO support"
date: 2008-08-19
forum: Apple Hardware Users
---

### Post by thetravellor on 2008-08-19
The b43 module in the standard ubuntu ppc kernel as installed via apt-get does not work in my particular airport extreme:

```

linux-headers-2.6.24-19-powerpc64-smp'

```


```
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: Shasta (Sun GEM)
       vendor: Apple Computer Inc.
       physical id: f
       bus info: pci@0001:03:0f.0
       logical name: eth0
       version: 00
       serial: 00:0d:93:5d:12:b2
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sungem driverversion=0.98 duplex=full ip=192.168.1.52 latency=16 link=yes maxlatency=64 mingnt=64 module=sungem multicast=yes port=MII speed=100MB/s
  *-network
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0001:01:01.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=16 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:11:24:93:b1:94
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

```


lspci -v

```
0001:01:01.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
	Subsystem: Apple Computer Inc. AirPort Extreme
	Flags: bus master, fast devsel, latency 16, IRQ 60
	Memory at 80084000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: [40] Power Management version 2

```

This is what happens with the standard kernel:

```

root@blackbox:~/rt2570/rt2570-1.1.0-b2# ifconfig wlan0 up

SIOCSIFFLAGS: Operation not supported

[ 1653.584714] input: b43-phy0 as /devices/virtual/input/input7
[ 1653.811955] b43-phy0 debug: Loading firmware version 351.126 (2006-07-29 05:54:02)
[ 1655.553147] b43-phy0 debug: Chip initialized
[ 1655.553213] b43-phy0 ERROR: DMA for this device not supported and no PIO support compiled in

```

I resolved it by downloading 2.6.26 Patch 2 and compiling my own kernel. I noted there was a new kernel parameter that was not present in 2.6.24:

CONFIG_B43_FORCE_PIO=y

the other paramters were:

CONFIG_B43=m
CONFIG_B43_PCI_AUTOSELECT=y
CONFIG_B43_PCICORE_AUTOSELECT=y
# CONFIG_B43_PCMCIA is not set
CONFIG_B43_PIO=y
CONFIG_B43_LEDS=y
CONFIG_B43_RFKILL=y
CONFIG_B43_DEBUG=y
CONFIG_B43_FORCE_PIO=y
CONFIG_B43LEGACY=m
CONFIG_B43LEGACY_PCI_AUTOSELECT=y
CONFIG_B43LEGACY_PCICORE_AUTOSELECT=y
CONFIG_B43LEGACY_LEDS=y
CONFIG_B43LEGACY_RFKILL=y
CONFIG_B43LEGACY_DEBUG=y
CONFIG_B43LEGACY_DMA=y
CONFIG_B43LEGACY_PIO=y
CONFIG_B43LEGACY_DMA_AND_PIO_MODE=y
# CONFIG_B43LEGACY_DMA_MODE is not set
# CONFIG_B43LEGACY_PIO_MODE is not set


So now it works.

---

### Post by pxwpxw on 2008-08-19
Yes, I can confirm that on a PPC64 G5 with BCM4306, the PIO does the trick.
The 2.6.26 kernel has it covered so intrepid shoul be ok for 4306.

---

