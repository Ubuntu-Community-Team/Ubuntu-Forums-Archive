---
title: "Sound problems please read!"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by especlipse290 on 2007-08-18
I have logitech speakers (no idea what sound card, so i'm not helping that much) but sometimes my sound works and sometimes it dosent 


This is really bugging me

---

### Post by Happy_Man on 2007-08-18
> **especlipse290 said:**
> I have logitech speakers (no idea what sound card, so i'm not helping that much) but sometimes my sound works and sometimes it dosent 


This is really bugging me
Thanks, but speakers aren't the issue. To really help, you need to give us your sound card name. Just as a general tip, though, open up a Terminal (Applications --> Accessories --> Terminal) and type ```
alsamixer
``` Make sure all the bars are maxed out, and try again.

---

### Post by especlipse290 on 2007-08-18
ugh the bars were maxed.. 

I have no idea what sound card =( i totally forgot

---

### Post by Happy_Man on 2007-08-18
OK. Your computer should know, and we can make it spill the beans by typing ```
lspci
``` into the terminal. Look for something that could be the name of a sound card, and if you can't find it, post the output here.

---

### Post by especlipse290 on 2007-08-18
quentin@quentin-desktop:~$ lspci
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
00:1f.5 **Multimedia audio controller**: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:04.0 Multimedia audio controller: Creative Labs SB Audigy LS
01:05.0 Communication controller: Conexant HSF 56k Data/Fax Modem
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)


I think the bold could be it

---

### Post by Happy_Man on 2007-08-18
> **especlipse290 said:**
> quentin@quentin-desktop:~$ lspci
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
00:1f.5 **Multimedia audio controller**: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:04.0 Multimedia audio controller: Creative Labs SB Audigy LS
01:05.0 Communication controller: Conexant HSF 56k Data/Fax Modem
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)


I think the bold could be it
Could also be the Creative Labs Audigy one. Just to check... could you please type ```
alsamixer -c2
``` and check those bars too?

---

### Post by especlipse290 on 2007-08-18
That command didnt work

ahh jeez this is stupid, I wonder why some days it works and some days it dosent

---

### Post by especlipse290 on 2007-08-18
!!!

I found a cd for soundblaster Live 24-bit

but i dono how to install windows apps.

---

### Post by Happy_Man on 2007-08-18
It wouldn't work anyway, you see, because Windows drivers are made for Windows and not Linux. Fundamentally different. 

See if this link works: [http://www.goesping.org/archives/2006/05/13/ubuntu-sound-on-gateway-laptop/](http://www.goesping.org/archives/2006/05/13/ubuntu-sound-on-gateway-laptop/)

---

### Post by especlipse290 on 2007-08-18
no luck =(


im going to reboot


maby that will fix something

---

### Post by especlipse290 on 2007-08-18
There we go, i have sound, but i have a feeling its going to go out again like always

---

### Post by Happy_Man on 2007-08-18
Well, cross your fingers and hope. :D

---

### Post by especlipse290 on 2007-08-18
haha thanks a lot

---

