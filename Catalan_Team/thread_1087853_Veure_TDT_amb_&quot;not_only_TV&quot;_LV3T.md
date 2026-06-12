---
title: "Veure TDT amb &quot;not only TV&quot; LV3T"
date: 2009-03-05
forum: Catalan Team
---

### Post by mininomutante on 2009-03-05
Hola a tots,
Estic provant de veure la TDT amb una tarja "not only tv" LV3T. He utilitzat el Me TV i el TV time Television Viewer.

En el primer (Me TV), en el moment d'executar, em surt un missatge dient "no tuner device".

En el segon (Tv Time) la pantalla em surt en blau i no sé com sintonitzar canals (em surt el missatge "no signal" , però amb windows veig canals), i dubto si ja és un tema de compatibilitat del hardware.

He llegit en algun lloc que això pot ajudar, però soc novell :-( :
 lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IB (ICH9) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IB (ICH9) 2 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9800 GT (rev a2)
02:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
05:01.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)
05:02.0 Multimedia video controller: Device 1a2d:1768
05:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0)

Gràcies per l'ajuda

---

### Post by papapep on 2009-03-05
Realment encara estàs amb la 7.04 (Feisty Fawn) tal i com diu el teu perfil? o és que no l'has actualitzat (el perfil)? Ho dic, per que abans de fer res jo provaria amb la última versió d'Ubuntu, i de nucli, per si ja està suportat. Han passat gairebé dos anys... :)

---

### Post by mininomutante on 2009-03-06
Hola Papapep,
Crec que ja ho he actualitzat (el perfil) :oops: ;)

---

### Post by papapep on 2009-03-08
No he estat capaç de trobar per enlloc cap referència d'aquesta targeta que dius que tens amb Linux...o és molt nova, o molt rara.

A video4linux, pots trobar això: [http://www.linuxtv.org/wiki/index.php/LifeView](http://www.linuxtv.org/wiki/index.php/LifeView)

i comenten això altre: "The LifeView company are not at all Linux friendly and you should avoid buying their DVB-T devices unless you have no alternative" ("L'empresa LifeView no és gens ni mica "amistosa" amb Linux i haurieu d'evitar comprar els seus dispositius de TDT a no ser que no tinguéssiu cap altra alternativa")

No pinta bé...diuen que ni tan sols donen suport pel Vista, imagina't :D

---

