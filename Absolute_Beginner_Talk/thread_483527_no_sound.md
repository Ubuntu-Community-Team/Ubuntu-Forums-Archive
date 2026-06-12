---
title: "no sound"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by brownietodd on 2007-06-24
Hi guys, I get no sound when playing here the Error.... An error occurred

could not establish connection to sound server.

any ideas

Todd

---

### Post by Crafty Kisses on 2007-06-24
> **brownietodd said:**
> Hi guys, I get no sound when playing here the Error.... An error occurred

could not establish connection to sound server.

any ideas

Todd

You might want to post this output:
```
lspci
```

---

### Post by brownietodd on 2007-06-24
todd@todd-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:0c.0 CardBus bridge: Texas Instruments PCI1250 (rev 02)
00:0c.1 CardBus bridge: Texas Instruments PCI1250 (rev 02)
00:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: Neomagic Corporation NM2200 [MagicGraph 256AV] (rev 12)
01:00.1 Multimedia audio controller: Neomagic Corporation NM2200 [MagicMedia 256AV Audio] (rev 12)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
todd@todd-laptop:~$

---

