---
title: "Need Serious HELP!!!!!!"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by Sector7 on 2007-08-01
Hi, I am a newbie to linux Ubuntu and I need help installing my Wireless Internet.
Its a sentech modem and i cant seem to figure out how to install.
Please can anyone with insight on how to install a wireless network help me out.
In other words i just need someone to help get my internet up and runing.

---

### Post by tico on 2007-08-01
Hi, I don't know how to help you, but here's an advice for future posts: don't put titles like "Need Serious HELP!!!!!!". You should describe your problem briefly: "How to set up a wireless connection?" It would be easier for other users to help you. Good luck! Hope someone else will be able to help you.

Cheers.

---

### Post by ugm6hr on 2007-08-01
More detail is required:
Your sentech modem - what is it?  Is it a wifi ADSL router?  Or is it a wifi PCI / PCMCIA / USB card?

Help the forum help you by telling us exactly what your hardware is, what you've tried so far, and which version of Ubuntu you are using.

---

### Post by Sector7 on 2007-08-01
thanks guys but i have tried everything i could think of and nothing seems to work so i give up. i will just have to manage without internet.

---

### Post by regomodo on 2007-08-01
open an application called terminal and type in "lspci"

paste here what you get

---

### Post by Sector7 on 2007-08-02
sector7@sector7-desktop:~$ "lspci"
0000:00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
0000:00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 01)
0000:00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
0000:00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
0000:00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
0000:00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV200 QW [Radeon 7500]
0000:02:08.0 Modem: Smart Link Ltd. SmartLink SmartPCI562 56K Modem (rev 04)
0000:02:0c.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)

---

### Post by regomodo on 2007-08-11
you haven't said if it's a usb device or not. From your lspci output the only networking devices i can see is your ethernet and 56k modem. No wifi adapter

enter "lsusb" into the terminal. I can't promise anything, maybe someone else could helpout?

---

