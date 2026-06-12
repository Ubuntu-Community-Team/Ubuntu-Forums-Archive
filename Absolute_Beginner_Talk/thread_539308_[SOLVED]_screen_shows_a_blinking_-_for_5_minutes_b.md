---
title: "[SOLVED] screen shows a blinking - for 5 minutes before loading ubuntu"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by arai on 2007-08-31
when i start the computer it asks if i wud use windows or linux. i select linux and then the screen show an "-" blinking for nearly 5 minutes or more. then ubuntu linux loads. 

why does it happen? how to reduce the blinking screen time?

---

### Post by Spr0k3t on 2007-08-31
Post up your system specs if you could.  I have a computer that takes forever to boot... however it is an extremely old system that I was shocked to see Ubuntu running on.

---

### Post by arai on 2007-08-31
what are the specifications you would want? kindly specify them.

---

### Post by Spr0k3t on 2007-08-31
Processor, memory (size and speed), drive speed (rpms)... that should do for now.

oh yeah, from the terminal, type "lspci" and post the output back here in a reply.

---

### Post by arai on 2007-08-31
processor p4 memory 500 mhz hard disk 80 gb (10 gb allocated for ubuntu linux)

the output is here

> usrnme@usrnme-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:00.0 Modem: Motorola Unknown device 3052 (rev 04)
01:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 81)
usrnme@usrnme-desktop:~$ 



---

### Post by arai on 2007-09-02
i got this problem resolved (thanks to [schneiderman]("http://ubuntuforums.org/showpost.php?p=3298265&postcount=10"))

Using the terminal

sudo apt-get remove usplash

and then restart system.

---

