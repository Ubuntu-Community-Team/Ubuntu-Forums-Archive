---
title: "Problems with installing atheros ar5008 wireless drivers"
date: 2007-09-13
forum: Apple PPC Users
---

### Post by Emac on 2007-09-13
Hi i have slight some problem to get my wlan to cooporate with my mac on ubuntu linux 7.04 fiesty. Have tried many steps towards getting it enabled. Have installed the ndiswrapper 1.47 and after this gtkndis that enables you to install windows wlan drivers. When I here try to install the wireless driver. It seems that it don`t want to install the drivers. If i choos drivers that are not off *.inf file types. It gives you a notice on this. Have also tried to install the source gnome package. When typing iwconfig. It says that there are no wireless extension.

Macbook Pro 2nd Gen Specification:

Processor: Intel Core 2 Duo 2,33GHz T7600
Memory: 2GB 667MHz DDR2 SDRAM( 2xSO-DIMM)
Graphic: ATI Mobility X1600
Harddisk:Hitachi SATA2 120GB
CD/DVD:Matashita DVD-RW -+
Network:Wireless Airport Extreme
              Built-in Ethernet(Broadcom/RealTek)
FireWire: Firewire 800
BlueTooth:Apple Bluetooth
Sound:Intel High Definition Audio

---

### Post by garlicsalt2 on 2007-10-06
> **Emac said:**
> Hi i have slight some problem to get my wlan to cooporate with my mac on ubuntu linux 7.04 fiesty. Have tried many steps towards getting it enabled. Have installed the ndiswrapper 1.47 and after this gtkndis that enables you to install windows wlan drivers. When I here try to install the wireless driver. It seems that it don`t want to install the drivers. If i choos drivers that are not off *.inf file types. It gives you a notice on this. Have also tried to install the source gnome package. When typing iwconfig. It says that there are no wireless extension.

Macbook Pro 2nd Gen Specification:

Processor: Intel Core 2 Duo 2,33GHz T7600
Memory: 2GB 667MHz DDR2 SDRAM( 2xSO-DIMM)
Graphic: ATI Mobility X1600
Harddisk:Hitachi SATA2 120GB
CD/DVD:Matashita DVD-RW -+
Network:Wireless Airport Extreme
              Built-in Ethernet(Broadcom/RealTek)
FireWire: Firewire 800
BlueTooth:Apple Bluetooth
Sound:Intel High Definition Audio

All right, I'm gonna try to help. Emphasis on TRY.

First off, in the specs you have above, you list AirPort extreme. Why not use that? to do so, you need to temporarily connect via ethernet and install the bcm43xx-fwcutter package.

When it asks you whether you want to download and extract the firmware, answer NO! This is not working, at the moment.

Then, open-up a terminal, and type:

```

wget -c http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o
bcm43xx-fwcutter -w /lib/firmware/`uname -r` ./wl_apsta-3.130.20.0.o

```

Be certain to keep the file that you downloaded via wget, as you'll need to re-run the bcm43xx-fwcutter command every time you upgrade the kernel.

Let me know if I can be of further help.
--Aaron

---

