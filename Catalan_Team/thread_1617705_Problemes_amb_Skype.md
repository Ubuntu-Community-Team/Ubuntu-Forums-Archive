---
title: "Problemes amb Skype"
date: 2010-11-09
forum: Catalan Team
---

### Post by Pimi on 2010-11-09
Hola
Tinc problemes per parlar amb l'Skype, tot em funciona correctament, càmera, recepció de so i vídeo... menys el micròfon, que no funciona. No puc sentir el retorn de la meva veu en la trucada de configuració de l'Skype ni en fer trucades a altres usuaris. També he provat l'Ekiga, amb els mateixos resultats, no em funciona  el micròfon.

He intentat solucionar-ho utilitzant el pacocontrol, com expliquen a [https://help.ubuntu.com/community/SkypeTroubleshooting?action=fullsearch&context=180&value=linkto%3A%22SkypeTroubleshooting%22](https://help.ubuntu.com/community/SkypeTroubleshooting?action=fullsearch&context=180&value=linkto%3A%22SkypeTroubleshooting%22) ,  però no se'm soluciona.

Tinc instalat l'Ubuntu 10.10 en un ordinador netbook AspireOne, amb les següents característiques: 

00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications AR8132 Fast Ethernet (rev c0)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

Gràcies

---

### Post by wgarcia on 2010-11-10
Suposo que hauràs provat tot el que se suggeria en un fil anterior, sobre mirar les coses bàsiques tipus els nivells a terminal-> alsamixer. 

Aquí hi ha un altre suggeriment.

1) Obre una terminal (Accessoris -> terminal)

2) Edita un fitxer de sistema:
sudo gedit /etc/modprobe.d/alsa-base.conf

3) Afegeix aquest línia al final d'aquest fitxer:
snd-hda-intel model=auto

Reinicia i mira si s'ha arreglat, si no s'arreglat desfés els passos anteriors per si un cas.

---

