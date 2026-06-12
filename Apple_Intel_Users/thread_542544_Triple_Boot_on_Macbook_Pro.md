---
title: "Triple Boot on Macbook Pro"
date: 2007-09-04
forum: Apple Intel Users
---

### Post by Emac on 2007-09-04
Hi, I am trying to find some more info and hints on setting up triple boot on my macbook. I have followed the wiki howto on [http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp#Linux](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp#Linux) but it seems the when i install the third boot. It all crashes. Have tested it and the main problems is that when second os is installed that goes fine and works splendedliy. It can`t handle the third, because it crashes the second os as well as the linux os. Are I approaching it wrong?

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

### Post by LeopoldBloom on 2007-11-06
I'm not sure if this is the correct way but I used [http://macapper.com/forums/showthread.php?t=134](http://macapper.com/forums/showthread.php?t=134) to setup my triple boot. The only thing I really did was use diskutil VolumeResize to create the partitions, installed Windows XP, then loaded the Ubuntu Live CD.  The only thing I did that really followed the guide was in Step 5, where I installed GRUB to the Linux partition. I didn't do anything special in Terminal, just that one step and everything has been fine for 2 weeks.

---

