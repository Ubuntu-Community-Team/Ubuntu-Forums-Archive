---
title: "NO Wireless Connection option"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by NHery on 2008-03-07
I get no 'wireless connection' option in system>administration>network when trying to configure and open the network.

I have downloaded UBUNTU 7.10 desktop twice (from separate sites) and I get the same results with both files; 'no errors found' on either burned disc.

?Should I try more UBUNTU sites?        :(

---

### Post by spiderbatdad on 2008-03-07
I believe that indicates there is no recognized wireless device connected to your mobo. What type of wireless card do you have? If pcmcia you might try discovering it with ```
iwconfig
```
Then run ```
sudo ifup device
``` where "device" is the listed recognized extension, such as wifi0, wlan0, or eth1.

---

### Post by NHery on 2008-03-08
using static IP address

iwconfig - lo       no wireless extensions
                eth0   no wireless extensions

sudo ifup lo - interface already configured.
sudo ifup eth0 - interface already configured

I was able to connect with PUPPY LINUX using no CLI commands.

Running UBUNTU as live CD, until I can get the connection to function.

---

### Post by seshomaru samma on 2008-03-08
it would help if you tell us what kind of wireless device you have
if this is a windows machine you can look under device manager (right click "my computer" and choose properties)

---

### Post by jan quark on 2008-03-08
definitely it would help to know the model of your wlan card

please post the results of these terminal commands:

```
sudo lshw -C network
```

```
lspci
```

```
iwconfig
```

```
sudo iwlist scan
```

```
cat /etc/network/interfaces
```

---

### Post by NHery on 2008-03-08
> **seshomaru samma said:**
> it would help if you tell us what kind of wireless device you have
if this is a windows machine you can look under device manager (right click "my computer" and choose properties)

Wireless device is Intel PRO/1000 CT Network Connection.

---

### Post by Truffs on 2008-03-08
hello

I have the same problem... so here are the results to the commands you requested... 
I hope somebody can help me.
Thanks in advance.

Result to **sudo lshw -C network**:
 *-network               
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:72:0e:ce:f8
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.77 firmware=5787m-v3.23 latency=0 link=no module=tg3 multicast=yes port=twisted pair
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0

Result to **lspci**:
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
04:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
0f:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0f:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0f:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
0f:06.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

Result to **iwconfig**:
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

Result to **sudo iwlist scan**:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

Result to **cat /etc/network/interfaces**:
auto lo
iface lo inet loopback

---

### Post by seshomaru samma on 2008-03-08
> **NHery said:**
> Wireless device is Intel PRO/1000 CT Network Connection.


i'm not sure


before you do anything - please post the output of the commands that jan quark asked you to 2 posts before

then try this:
[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

if it doesnt work then there are drivers[ here]("http://www.nodevice.in/driver/PRO_1000/get43916.html") but i don't know the source , i don't know if i can recommend this site, maybe some of our indian ubuntu users can verify it. however if you are on a live CD i don't think any harm can happen. 

to install the driver - read[ this ]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by seshomaru samma on 2008-03-08
> **Truffs said:**
> hello

I have the same problem... so here are the results to the commands you requested... 
I hope somebody can help me.
Thanks in advance.

k

your problem is different, you have an Atheros wireless not Intel
I suggest you start a new thread, perhaps in the networking section and paste the output of the commands + the version of ubuntu you are using

---

### Post by NHery on 2008-03-10
results of *iqwconfig *    no wireless extensions

results of *sudo iwlist scan*   lo               interface doesn't support scanning
                                                     eth0           interface doesn't support scanning

results of *cat /etc/network/interfaces*    auto  lo
                                                                          iface lo  inet loopback

How do I printout longer results when working live CD?

When I'm starting the UBUNTU disc, one of the msgs is at the start is 'Intel_rng: FWH not detected'.

:(

---

