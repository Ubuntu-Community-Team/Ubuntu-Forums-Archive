---
title: "usb wl-167g ralink driver does not work on ubuntu 8.04 ppc"
date: 2008-08-16
forum: Apple Hardware Users
---

### Post by thetravellor on 2008-08-16
I am working on an iMac G5 (ppc 64). Have given up trying to get the Airport to work (fwcutter driver dies, ndiswrapper incompatible with PPC platform). Now I am trying to get a ralink based ASUS WL-167g to work:

This is the device:

```
Bus 003 Device 002: ID 0b05:1706 ASUSTek Computer, Inc. WL-167G 802.11g Adapter [ralink]

```

My goodness.....what a trial. I have tried Fedora 9, Opensuse 11, YDL and now am having a go with Ubuntu 8.04:

```
Linux blackbox 2.6.24-19-powerpc64-smp #1 SMP Fri Jul 11 23:39:57 UTC 2008 ppc64 GNU/Linux

```


The standard rt2500usb drivers as loaded by the kernel dont work. The interface loads, can sort of associate, but cannot get an ip address.

So, I am trying to get the rt2570 driver working, which is one of serialmonkeys's legacy drivers. It is present in the apt repositories, but will not compile using the "debian" way...:

The particular ubuntu package is rt2570-source

```
sudo module-assistant build rt2570

```

```
&#9474; # Build modules                                                            &#8593;            
            &#9474; /usr/bin/make KERNDIR=/usr/src/linux PATCHLEVEL=6                          &#9618;            
            &#9474; make[2]: Entering directory `/usr/src/modules/rt2570'                      &#9618;            
            &#9474; make[3]: Entering directory                                                &#9618;            
            &#9474; `/usr/src/linux-headers-2.6.24-19-powerpc64-smp'                           &#9618;            
            &#9474;   CC [M]  /usr/src/modules/rt2570/rtusb_main.o                             &#9618;            
            &#9474; /usr/src/modules/rt2570/rtusb_main.c: In function &#8216;usb_rtusb_probe&#8217;:       &#9618;            
            &#9474; /usr/src/modules/rt2570/rtusb_main.c:1904: error: implicit declaration     &#9618;            
            &#9474; of function &#8216;SET_MODULE_OWNER&#8217;                                             &#9618;            
            &#9474; /usr/src/modules/rt2570/rtusb_main.c:1924: error: &#8216;struct net_device&#8217;      &#9618;            
            &#9474; has no member named &#8216;weight&#8217;                                               &#9646;            
            &#9474; make[4]: *** [/usr/src/modules/rt2570/rtusb_main.o] Error 1                &#9618;            
            &#9474; make[3]: *** [_module_/usr/src/modules/rt2570] Error 2                     &#9618;            
            &#9474; make[3]: Leaving directory                                                 &#9618;            
            &#9474; `/usr/src/linux-headers-2.6.24-19-powerpc64-smp' 
```

I also tried a standard "make" but this bombed with the same errors:

```
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-powerpc64-smp'
  CC [M]  /usr/src/modules/rt2570/rtusb_main.o
/usr/src/modules/rt2570/rtusb_main.c: In function &#8216;usb_rtusb_probe&#8217;:
/usr/src/modules/rt2570/rtusb_main.c:1904: error: implicit declaration of function &#8216;SET_MODULE_OWNER&#8217;
/usr/src/modules/rt2570/rtusb_main.c:1924: error: &#8216;struct net_device&#8217; has no member named &#8216;weight&#8217;
make[2]: *** [/usr/src/modules/rt2570/rtusb_main.o] Error 1
make[1]: *** [_module_/usr/src/modules/rt2570] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-powerpc64-smp'
rt2570.ko failed to build!
make: *** [module] Error 1

```

---

### Post by pytheas22 on 2008-08-16
Does it work to follow these steps:
```

sudo -s
mkdir rt2570
cd rt2570
apt-get install build-essential
wget http://prdownloads.sourceforge.net/rt2400/rt2570-1.1.0-b2.tar.gz?download
tar -xzvf rt25*
cd rt25*/Module
make
make install
```

or do you get the same error?  The above may help because you'd be pulling the latest rt2570 source instead of whatever is in the repositories.

Also, how hard did you try to get your Broadcom (Airport) card to work?  There are different drivers (bcm43xx and b43); sometimes you need to use a particular one.  If you want to try harder to get the internal card working, please post:
```

lshw -C Network
lspci -nn
sudo modprobe bcm43xx
sudo modprobe b43
dmesg | grep -e bcm -e b43 -e ssb -e wlan -e eth
```

---

### Post by thetravellor on 2008-08-18
re the Ralink card: the compile bombs....

```
root@blackbox:~/rt2570/rt2570-1.1.0-b2/Module# make
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-powerpc64-smp'

  ERROR: Kernel configuration is invalid.
         include/linux/autoconf.h or include/config/auto.conf are missing.
         Run 'make oldconfig && make prepare' on kernel src to fix it.


  WARNING: Symbol version dump /usr/src/linux-headers-2.6.24-19-powerpc64-smp/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /home/user/rt2570/rt2570-1.1.0-b2/Module/rtusb_main.o
cc1: error: include/linux/autoconf.h: No such file or directory
In file included from include/linux/types.h:11,
                 from include/linux/prefetch.h:13,
                 from include/linux/list.h:8,

```

I tried very hard to get the broadcom to work, it always ends up with the same thing:

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

```

root@blackbox:~/rt2570/rt2570-1.1.0-b2# dmesg | grep -e bcm -e b43 -e ssb -e wlan -e eth
[    2.190468] Frequency method: SCOM, Voltage method: SMU
[   35.843350] windfarm: SMU failed new fan command falling back to old method
[   36.884807] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x04, vendor 0x4243)
[   36.884815] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x05, vendor 0x4243)
[   36.884822] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x02, vendor 0x4243)
[   36.884829] ssb: Core 3 found: V90 (cc 0x807, rev 0x02, vendor 0x4243)
[   36.884835] ssb: Core 4 found: PCI (cc 0x804, rev 0x09, vendor 0x4243)
[   36.888214] ssb: Sonics Silicon Backplane found on PCI device 0001:01:01.0
[   37.006661] eth0: Sun GEM (PCI) 10/100/1000BaseT Ethernet 00:0d:93:5d:12:b2
[   37.006665] eth0: Found BCM5221 PHY
[   39.405580] eth0: Link is up at 100 Mbps, full-duplex.
[   44.422342] Driver 'sd' needs updating - please use bus_type methods
[   76.780092] eth0: Link is up at 100 Mbps, full-duplex.
[   76.780100] eth0: Pause is disabled
[   80.702403] b43-phy0: Broadcom 4306 WLAN found
[   80.736497] b43-phy0 debug: Found PHY: Analog 2, Type 2, Revision 2
[   80.736523] b43-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[  100.276480] eth0: no IPv6 routers present
[ 1653.584714] input: b43-phy0 as /devices/virtual/input/input7
[ 1653.811955] b43-phy0 debug: Loading firmware version 351.126 (2006-07-29 05:54:02)
[ 1655.553147] b43-phy0 debug: Chip initialized
[ 1655.553213] b43-phy0 ERROR: DMA for this device not supported and no PIO support compiled in

```

```

root@blackbox:~/rt2570/rt2570-1.1.0-b2# ifconfig wlan0 up

SIOCSIFFLAGS: Operation not supported

[ 1653.584714] input: b43-phy0 as /devices/virtual/input/input7
[ 1653.811955] b43-phy0 debug: Loading firmware version 351.126 (2006-07-29 05:54:02)
[ 1655.553147] b43-phy0 debug: Chip initialized
[ 1655.553213] b43-phy0 ERROR: DMA for this device not supported and no PIO support compiled in

```

---

### Post by pytheas22 on 2008-08-18
Did you try running:
```

sudo make oldconfig && make prepare
```

to see if it will fix the compilation issues with rt2570?  I don't know what those commands do, but maybe it will solve the problem (or maybe not...).

As for your Broadcom card, I have the same model (4306) in my Dell and it works with bcm43xx, the older Broadcom driver.  It doesn't really work with b43.  Try running this to see if you can get the card working with bcm43xx:
```

sudo -s
echo 'blacklist b43' >> /etc/modprobe.d/blacklist
echo 'blacklist b43legacy' >> /etc/modprobe.d/blacklist
echo 'blacklist ssb' >> /etc/modprobe.d/blacklist
sed 's/blacklist bcm43xx/#blacklist bcm43xx/' /etc/modprobe.d/blacklist
apt-get install bcm43xx-fwcutter
```

You will be asked if you want to download the bcm43xx firmware automatically; say yes.  Then reboot and see if lshw lists "bcm43xx" as the driver for your wireless card.

Also, what is the DISABLED interface mentioned by lshw?  It has an interface name (wlan0) so I'm wondering if something is driving it already.  What happens if you type:
```

sudo ifconfig wlan0 up
```

---

