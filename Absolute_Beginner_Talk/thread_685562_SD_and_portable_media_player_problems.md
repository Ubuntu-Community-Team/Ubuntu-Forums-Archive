---
title: "SD and portable media player problems"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by brokenhachi on 2008-02-02
ive got a built in SD card on my Toshiba laptop, and it recognizes the drive, but i cant seem to access the card (cant find it.. doesnt show up in "places")

and basically the same problem with a toshiba portable media player....


any ideas as how i can get this working?

---

### Post by z-vap on 2008-02-02
Sorry no.  

BUT I am guessing someone can.  However they will probably need more info.  Like what model laptop.  Which version of ubuntu are you running?  etc.

---

### Post by brokenhachi on 2008-02-02
ok... 


im running gutsy on a m35-s359 toshiba satellite

---

### Post by brokenhachi on 2008-02-03
noone can help with this????

by the way, here is lspci showing the SD card reader... but when i put the card in, nothing happens and i cant find an icon or anything anywhere....

> ~$ lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 21)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 21)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200 64M] (rev a1)
02:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
02:0a.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
02:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 33)
02:0d.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 05)


---

### Post by brokenhachi on 2008-02-11
is there no help for this?

---

### Post by oedha on 2008-02-11
have you mark the boxes on system - appearances - removable media.......

---

### Post by brokenhachi on 2008-02-11
there is no system - appearances - removable media


there is system-pref-appearances but in there i dont see removable media




edit: i did a search for "removable media" and the boxes for auto-mount are ticked.

---

### Post by White_Panther on 2008-02-12
have you tried to install gnome-volume-manager or if it is already installed try re-installing it, that is what worked for me.  To see it you have it look under System - Preferences - Removable Drives and Media

Cheers,
EJ

---

### Post by brokenhachi on 2008-02-12
doesnt seem like that helped.

i already had it installed so i reinstalled it, but it didnt help i think. at least, i dont see the SD anywhere.


is there a way to manually mount it?

---

