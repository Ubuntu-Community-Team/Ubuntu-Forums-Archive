---
title: "trouble with netgear wg311v2"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by starblast on 2007-03-31
Need help! what an I doing wrong.
I have ubuntu 6.10 it was working fine. Wlan0 ran great. Installed a new video card had trouble with driver and had to reinstall Ubuntu. Video works great but now my wlan is not working. Have tried every thing others have said should help but it will not work. It's a Netgear wg311v2 it will not talk to or be recognized by the network utility. I did a dmesg | grep acx
 and got this with IRQ Failure 
[17179590.468000] acx: Loaded combined PCI/USB driver, firmware_ver=1.2.0.30
[17179590.468000] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
[17179590.468000] acx: found ACX111-based wireless network card at 0000:02:0b.0, irq:193, phymem1:0xFC220000, phymem2:0xFC200000, mem1:0xf085c000, mem1_size:8192, mem2:0xf0980000, mem2_size:131072
[17179592.120000] acx: form factor 0x01 ((mini-)PCI / CardBus), radio type 0x16 (Radia), EEPROM version 0x05, uploaded firmware 'Rev 1.2.0.30' (0x03010101)
[17179592.120000] acx v0.3.21: net device wlan0, driver compiled against wireless extensions 20 and Linux 2.6.17-11-generic
[17179592.216000] usbcore: registered new driver acx_usb
[17179594.224000] acx: got IV_ICV_Failure IRQ(s)
[17179594.224000] acx: got IV_ICV_Failure IRQ(s)
[17179818.168000] acx: got IV_ICV_Failure IRQ(s)
[17179825.952000] acx: got IV_ICV_Failure IRQ(s)
[17179825.952000] acx: got IV_ICV_Failure IRQ(s) 

How di I fix this ?

---

### Post by dstew on 2007-04-01
It sounds like there is a conflict between your video card and your wireless card. Look at the printout of **lspci -v** to see if they might be sharing some resource (memory, port, or interrupt request).

---

### Post by bigken on 2007-04-04
I had the same problem with my wg311v2 and the same output from dmesg | grep acx
but this seems to fix it dissable wep or any other security on your router then let your card fnd a ip address then enable your wep :)

---

