---
title: "DWA-645 ( D-Link RangeBooster N 650)"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by Boblen on 2007-11-09
I am testing Ubuntu from a live CD on my laptop, but can not connect to the Internet. My D-Link RangeBooster N 650 is not working. Is there a driver I can install to make it work?

---

### Post by Pumalite on 2007-11-09
Is it set to give DHCP and are you WIRED to it?

---

### Post by Trebaruna on 2007-11-09
It's not a router, it's a PCMCIA wireless card.

---

### Post by Pumalite on 2007-11-09
That's a different can of beans. I'll see if I can find something.

---

### Post by Boblen on 2007-11-12
Any suggestions? Do I have to continue to run Windows to be able to use Internet?

---

### Post by Pumalite on 2007-11-12
Try this page. This is the chipset they use:

[http://www.atheros.cz/](http://www.atheros.cz/)

---

### Post by Boblen on 2007-11-13
Thank you Pumalite. It is the Atheros AR5416 chipset, but I can not find the driver.

---

### Post by Boblen on 2007-11-13
Can I use this?  [http://sourceforge.net/projects/madwifi/](http://sourceforge.net/projects/madwifi/)

---

### Post by eldepeche on 2007-11-13
> **Boblen said:**
> Can I use this?  [http://sourceforge.net/projects/madwifi/](http://sourceforge.net/projects/madwifi/)

Are you using version 7.10 Gutsy Gibbon? The newest version of Ubuntu includes MADWifi by default. If it isn't activated, then your card may use a different chipset. 

Can you run "lspcmcia" in a terminal (without the quotation marks) and post the output here?

---

### Post by Boblen on 2007-11-15
ubuntu@ubuntu:~$ lspcmcia
Socket 0 Bridge: [yenta_cardbus]  (bus ID: 0000:02:04.0)
  CardBus card -- see "lspci" for more information

---

### Post by eldepeche on 2007-11-15
OK, what about the output of "lspci"?

---

### Post by Boblen on 2007-11-15
ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE
DRAM Controller/Host-Hub Interface (rev 02)

00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 02)

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) 
USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M)
USB2 EHCI Controller (rev 02)

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)

00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)

00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97Audio Controller (rev 02)

00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97Modem Controller (rev 02)

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]

02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)

02:04.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)

02:04.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller

03:00.0 Network controller: Atheros Communications, Inc. AR5416 802.11a/b/g/n Wireless PCI Adapter (rev 01)

ubuntu@ubuntu:~$

---

### Post by Boblen on 2007-11-15
This is output from the Device Manager:

info.bus                   string pci
info.parent              string \orgfreedesktop\hal\devices\pci_10c_ac44
info.product             string AR5416 802.11a/b/g/n Wireless PCI Adapter
info.subsystem        string pci
info.udi                     string /org/freedesktop/Hal/devices/pci_168c_23
info.vendor               string Atheros Communications, Inc.
linux.hotplug_type    int 2(0x2)
linux.subsystem       string pci
linux.sysfs_path      string /sys/devices/pci/0000:00/0000:00:1le./ 0000:02:04.0/0000:03:00.0
pci.device_class        int 2(0x2)
pci.device_protocol   int 0(0x0)   
pci.device_subclass   int 128 (0x80)
pci.linux.sysfs_path   string /sys/devices/pci/0000:00/0000:00:1le./ 0000:02:04.0/0000:03:00.0
pci.product                 string AR5416 802.11a/b/g/n Wireless PCI Adapter
pci.product_id            int 35(0x23)
pci.subsys_product_id int 14857(0x3a09)
pci.subsys_vendor_id  int 2001(0x7dl)
pci.vendor                   string Atheros Communifations, Inc
Pci.vendor_id              int    5772 (0x168c)

---

### Post by Boblen on 2007-11-16
Do you get something out of this?

---

### Post by Boblen on 2007-11-16
Any suggestions?

---

### Post by eldepeche on 2007-11-16
Does your wireless work with the live CD? I have a desktop and a laptop, both with Atheros wireless chipsets, and MADWifi is loaded automatically on both of them; after installation, the restricted drivers manager asked if I wanted to continue using it.

Are you using Gutsy? Are the packages "madwifi-ng" and "madwifi-ng-tools" installed?

---

### Post by Boblen on 2008-04-25
Can't get the card to work with ubuntu 8.04 either, when I runned the hardware test from the live CD ubuntu chrashed. I'm so tired of ubuntu not working...

---

### Post by urk_nono on 2008-04-26
[http://ubuntuforums.org/showthread.php?p=4804935#post4804935](http://ubuntuforums.org/showthread.php?p=4804935#post4804935)

It worked perfectly for me.

---

### Post by Boblen on 2008-04-27
YESSSS. Now the wireless card is up and working. Thank you for the link urk_nono. Finaly running Ubuntu after 2 years wanting to use it, but without a working network card I had to use Windows. Now everything works fine:)

---

