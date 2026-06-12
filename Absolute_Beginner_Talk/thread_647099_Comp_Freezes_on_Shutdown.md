---
title: "Comp Freezes on Shutdown"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by Dougie187 on 2007-12-21
I have a really weird problem.

So, Sometimes (not every time) when I shutdown my computer, instead of completing the shutdown sequence, the computer just goes to a black screen, and then just sits there. The CPU fan revs every couple of minutes too, and it pumps out hot air.

So when I was checking the messages log the only things that I found that had concerned me were the following.

Dec 21 07:53:40 xxxxx kernel: [   22.824000] Failure registering capabilities with primary security module.
--and--
Dec 21 07:54:23 xxxxx dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.     dbus.get.nis_servers

let me know if anyone has any ideas or if there is somewhere else that I can look for help. Thanks.

---

### Post by wormser on 2007-12-22
What type of wireless card do you have?  There is some error with eth1 which I am assuming is your wireless.  I have problems sometimes with my Broadcom card.  Post the results of:

```
lspci
```

---

### Post by Dougie187 on 2007-12-24
I have an intel 2200.

Here are the results of lspci. Thanks!

00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:05.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
01:0b.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
01:0b.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
01:0b.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller

---

### Post by philinux on 2007-12-24
You might try the known bugs link below.

---

