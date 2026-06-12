---
title: "Realtek network card driver?"
date: 2014-02-11
forum: Asus Ubuntu Support (CLOSED)
---

### Post by AlecJ on 2014-02-11
After upgrading my motherboard to a Asus M5A78L/USB3. The internet was much slower than before?
I have 3 of these motherboards 2 with the Nvidia video on-board and this latest one with ATI (not good with Linux).
All of them have the same on-board network chip, but this new one was causing problems.

A lot of Google showed that the Linux Kernel uses the wrong driver for this card?

sudo lshw -C network   gives:-

```
 *-network                      description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 09
       serial: d8:50:e6:bc:a8:3f
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes [COLOR=#ff0000]driver=r8168[/COLOR] driverversion=8.037.00-NAPI duplex=full ip=192.168.1.254 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:50 ioport:e800(size=256) memory:fdfff000-fdffffff memory:fdff8000-fdffbfff
```

Network card RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
Note the driver version r8168 (this was r8169 Wrong driver!)

So go here
[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#RTL8111B/RTL8168B/RTL8111/RTL8168<br>RTL8111C/RTL8111CP/RTL8111D(L)<br>RTL8168C/RTL8111DP](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#RTL8111B/RTL8168B/RTL8111/RTL8168<br>RTL8111C/RTL8111CP/RTL8111D(L)<br>RTL8168C/RTL8111DP)

get the latest driver downloaded (8.037.00 as of 11/02/2014)
extract the tar with Archive Manager to your Home folder
Open a terminal Ctrl-Alt-T
```
cd r8168-8.037.00
sudo ./autorun.sh
```

All being well this should unload the old module and load the new.
Massive improvement on all 3 Motherboards.

Mythbuntu streams HD across the network like I've never experienced before.

Not sure yet but might have to install this after every Kernel update?

---

### Post by varunendra on 2014-02-13
> **AlecJ said:**
> Network card RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
Note the driver version r8168 (this was r8169 [COLOR="#FF0000"]Wrong driver[/COLOR]!)
r8169 is not the wrong driver, it is supposed to work with this chip and it has been with its older variants. It is just that it seems to not yet able to handle these new variants properly (or maybe it's buggy with only a few ones that are reported here..).

In the upcoming kernels, when the r8169 driver is improved enough to handle these new variants (if the bug reports have been submitted and the work is in progress), you won't have to resort to the proprietary r8168 driver.

> Not sure yet but might have to install this after every Kernel update?
Yes you will have to, unless you get a "dkms" package of it, which reinstalls itself automatically after each kernel upgrade.

---

