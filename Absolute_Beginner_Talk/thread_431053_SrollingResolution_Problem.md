---
title: "Srolling?/Resolution? Problem???"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by yiggaman on 2007-05-02
i just installed feisty just like that withou checking specs or if it would work on this laptop, anywayz everything seemed okay except my internal wireless card didnt work,

i went about loooking through forums and google until i posted a thread asking for help? then i began trying all the different terminal commands, just getting used to the terminal and things,

i got it working okayish but because of my exploring the terminal and commands i had a feeling i hAD messed up/modifed the main kernel or something round that area,

i decided to fresh install (did this a couple of times) and do the ndiswrapper driver thing i
evntually got it working using ndiswrapper and downloaded drivers, 

now i want to solve the issue of me having to scroll left right up down to get to the edge of my screen?  like im playing a game or something?

can someone guide me please as to what i have to do?

---

### Post by yiggaman on 2007-05-02
here is my lspci:

Ubuntu 7.04 Feisty Fawn

arch
i686
lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:01.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)

---

### Post by bobplano on 2007-05-02
this sounds more like a resolution problem than anything to do with your wifi card. see what your resolution is under systerm>prefrences for GNOME, not sure about KDE. try sudo dpkg-reconfigure xserver-xorg if just changing the resolution doesn't work

---

