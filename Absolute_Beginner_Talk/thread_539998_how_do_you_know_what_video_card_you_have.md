---
title: "how do you know what video card you have?"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by Reljoy on 2007-09-01
how do you know what video card you have?
I went to System Preferences Hardware Information and couldn't see anything there about my video. I think it is built in to the motherboard. The PC is an Acer Veriton 3500 V2.
Thanks.

---

### Post by diatribe on 2007-09-01
lspci or lshw will let you know if run from a terminal

---

### Post by alienexplorers on 2007-09-01
run in terminal
> lspci



You beat me to it diatribe.

---

### Post by Reljoy on 2007-09-01
OK
rperrett@reljoy-ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (CNR) Ethernet Controller (rev 82)

Does this mean I am "safe" from the problems that others are having with ATI cards?

---

### Post by diatribe on 2007-09-01
well considering that from the looks of things you have an intel graphics card, I would say yes ;p

---

### Post by Reljoy on 2007-09-01
Thanks.

---

### Post by Paulmd on 2007-09-01
> **Reljoy said:**
> Thanks.

The question you should ask is "does my card have known problems with Ubuntu?"

---

