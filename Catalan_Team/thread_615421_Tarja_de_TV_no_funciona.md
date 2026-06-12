---
title: "Tarja de TV no funciona"
date: 2007-11-17
forum: Catalan Team
---

### Post by ventma on 2007-11-17
La tarja de TV no em funciona. Jo conec els paràmetres de Windows, però algú sap com introduir aquests paràmetres a UBUNTU.

---

### Post by papapep on 2007-11-17
No ens expliques la placa que tens, ens ho poses difícil.

Aquí tens informació sobre les plaques de tv convencional, tdt i satel·lit suportades a Linux:

[http://www.linuxtv.org/v4lwiki/index.php/Main_Page](http://www.linuxtv.org/v4lwiki/index.php/Main_Page)

---

### Post by ventma on 2007-11-21
No sé la tarja que tinc, el manual posa "BT 878 TV-Tuner Capture Card". Al Windows la tenia configurada com a tarja desconeguda i li havia introduït els paràmetres GPIO i IFORM, que havia obtingut amb un programa específic, manualment. El que penso hauria de fer és introduir aquest paràmetres als driver bttv (?)

---

### Post by CarlesOriol on 2007-11-21
fes lspci i ens copies el resultat

---

### Post by ventma on 2007-11-23
Aquest és el resultat de lspci:
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 741/741GX/M741 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:09.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 02)
00:09.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 02)
00:0a.0 Serial controller: Rockwell International HCF 56k Data/Fax Modem (rev 01)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

---

### Post by papapep on 2007-11-24
Crec que et podria funcionar posant les següents ordres a un terminal:

Descarreguem del kernel el mòdul bt878:

```
sudo modprobe -r bt878
```

Descarreguem el mòdul bttv:

```
sudo modprobe -r bttv
```

I tornem a carregar el mòdul bttv amb un paràmetre concret:

```
sudo modprobe bttv card=100
```

Ara hauries de provar amb qualsevol programa de visualització de televisió (tvtime, xawtv, kaffeine?) a veure si sintonitzes algun canal.

Si efectivament et funciona, caldria que per a poder-la veure sempre posis aquesta línia dins el fitxer /etc/modprobe.d/options:

```
sudo nano /etc/modprobe.d/options
```

i hi afegeixes la línia:

```
options bttv card=100
```

surts desant amb Ctrl+X, i acceptant amb "y" i ja està.

---

### Post by ventma on 2007-11-25
Això ja ho havia provat ficant card=0 amb el mateix resultat: funciona, es sintonitzen tots els canals, però no es veu bé, es barregen les imatges d'un i altre canal, i no té so. També he provat d'introduir tuner=1 (i d'altres nºs) i segueix sense so.

---

### Post by papapep on 2007-11-25
I amb el valor 100 ho has provat?

Explica tot el que has fet i així no repetirem feina.

---

### Post by ventma on 2007-11-26
Si, he provat amb el valor 100, i dies abans havia provat amb el valor 0, amb el mateix resultat: el programa TVtime sintonitza tots els canals però no es veuen bé i sempre sense so.

---

