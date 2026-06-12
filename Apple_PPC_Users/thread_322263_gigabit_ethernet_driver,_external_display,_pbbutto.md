---
title: "gigabit ethernet driver, external display, pbbuttons missfunctioning"
date: 2006-12-20
forum: Apple PPC Users
---

### Post by leafw on 2006-12-20
Dear all,

My machine: PowerBook Ti 3.5 1Ghz, 512 Mb SDRAM, running latest apt-get'ed ubuntu-ppc edgy.

My workplace has switched to gigabit routers, and my ubuntu edgy-ppc can no longer DHCPDISCOVER any LAN with 'sudo ifup eth0'. MacOSX 10.3.9 in another partition works just fine. So I wonder, does the current network driver support gigabit connections? According to 'lspci', my network driver is:
0002:24:0f.0 Ethernet controller: Apple Computer Inc. UniNorth GMAC (Sun GEM) (rev 01)

I would appreciate pointers on how to upgrade this driver if a better one is available, or otherwise configure it for gibabit nets if that is possible.


Second, I have no problem with external VGA displays (as setup following this tutorial: [http://ozlabs.org/~jk/docs/mergefb/](http://ozlabs.org/~jk/docs/mergefb/) ), but DVI (digital) displays don't work. Did anyone manage to get DVI displays to work in powerpc machines?


Third, a long-lasting problem with power management, related to all or any of pbbuttons, KDE and Gnome. The laptop makes a much more inefficient use of battery power, most likely due to never putting the hard drive to sleep (is that possible?) as MacOSX does. But in addition, sometimes it fails alltogether to go to sleep. Hoary, Breezy and Dapper with KDE (kubuntu) where fine. Now that I use Edgy with Gnome, power management is not proper. In the past, power management in gnome did not work at all, but still it's very much imperfect and leads to data lossage when it suddenly fails to go to sleep properly (and simply shuts down).

Does anyone has any recipe on how to fine-tune power managent for laptops, with 100% reliability like there was in Kubuntu-dapper ?

Thanks for any insights.

Albert

---

### Post by webaake on 2007-06-02
I have the same problem with Gigabit ethernet, almost the same setup as above. I get only 100mbit with a brand new 3com gigabit switch.

Take a look at this;
sudo lshw -C network

  *-network
       description: Ethernet interface
       product: UniNorth GMAC (Sun GEM)
       vendor: Apple Computer Inc.
       physical id: f
       bus info: pci@21:0f.0
       logical name: eth0
       version: 00
       serial: 00:30:65:55:9f:68
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sungem driverversion=0.98 duplex=full ip=192.168.0.250 latency=16 link=yes maxlatency=64 mingnt=64 multicast=yes port=MII speed=100MB/s
       resources: iomemory:f5200000-f53fffff irq:41

As far as I understand my Mac should have Gigabit support on eth0 (it's a G4 400Mhz with ADC video port and AGP card)


Is it possible to reinstall driver (kernel module) or update it? Or add parameters to eth0-ifup script or the like?

Regards,

Ake S., Sweden

---

