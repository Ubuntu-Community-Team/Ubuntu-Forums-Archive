---
title: "Configuració del xorg per la ati MR HD 3400 i el compiz fusion"
date: 2010-01-18
forum: Catalan Team
---

### Post by igaes on 2010-01-18
Hola, el meu dubte és el següent, he instalat els drivers de ati (de la web de ati) per a la targeta per a conseguir un bon funcionament de l'acceleració 3D.

Quan creia que tot anava bé, he instalat el compiz-fusion i he trobat que l'ordinador anava lent quan poso els efectes tipics del compiz. Aleshores, la meva pregunta seria si hi ha alguna configuració que jo no conec del xorg per a que funcione millor el compiz.

L'arxiu xorg.conf esta així en aquests moments

```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "UseFastTLS" "1"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

Gracies

---

