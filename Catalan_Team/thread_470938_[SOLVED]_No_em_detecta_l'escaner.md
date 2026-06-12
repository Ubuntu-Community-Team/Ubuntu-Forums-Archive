---
title: "[SOLVED] No em detecta l'escaner"
date: 2007-06-11
forum: Catalan Team
---

### Post by Curial on 2007-06-11
Tinc un Scanner Packard Bell Diamond 2450 i quan el connecto a l'USB sembla no ser detectat.
Provo d'insertar imatge amb el processador de textos de l'open Off. i no fa res.

De fet des del gestor de dispositius si que veig que apareix i desapareix l'scanner al port USB, no diu res però, del model ni del fabricant.

He fet servir tant una memòria d'USB com una càmera i no m'ha donat cap problema.

Que us sembla?

Gràcies.

---

### Post by Ferri on 2007-06-11
Tens instal·lat Xsane?
Què et diu si fas (línia de comandaments):```
lsusb
```

---

### Post by Curial on 2007-06-11
Si que el tinc instal·lat. Quan el provo d'obrir diu que no hi ha el dispositiu disponible.

El que si he fet es instal·lar el sane des del terminal, pero no m'ha servit de res.

També em surt un missatge que diu que no s'ha pogut obrir el dispositiu `gt68xx:libusb:001:002"
argument invàlid

Amb lsusb surt:
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 055f:021a Mustek Systems, Inc. BearPaw 2448 TA Plus
Bus 001 Device 001: ID 0000:0000  

:o

---

### Post by papapep on 2007-06-11
Aquí:

[http://www.ubuntu-es.org/index.php?q=node/41467#comment-98211](http://www.ubuntu-es.org/index.php?q=node/41467#comment-98211)

crec que trobaràs la solució.

---

### Post by Curial on 2007-06-26
> **papapep said:**
> Aquí:

[http://www.ubuntu-es.org/index.php?q=node/41467#comment-98211](http://www.ubuntu-es.org/index.php?q=node/41467#comment-98211)

crec que trobaràs la solució.

He baixat el firmware i l'he desat a l'escriptori.
Com haig d'escriure la línia des del terminal. Suposant que el firmware és A2Dfw.usb.

Jo he escrit :sudo cp A2Dfw.usb /usr/share/sane/gt68xx.

Gràcies.

---

### Post by papapep on 2007-06-26
Potser primer t'hauries d'assegurar de que el directori /usr/share/sane/gt68xx existeixi.

Un cop ho has verificat, cal que vagis fins el directori on tens el firmware: Segons tu mateix, l'escriptori:

```
cd /home/elteuusuari/Desktop

```

Ara ja pots executar la comanda de copiat:

```
sudo cp A2Dfw.usb /usr/share/sane/gt68xx
```

També ho podries fer en un sol pas:

```
sudo cp /home/elteuusuari/Desktop/A2Dfw.usb /usr/share/sane/gt68xx
```

---

### Post by Curial on 2007-06-26
Sí efectivament, s'ha copiat finalment l'arxiu A2Dfw.usb al subdirectori /gt68xx.

Tot i això tant quan faig servir el Xsane com el kooka em surt que no s'ha pogut trobar disposistiu.

---

### Post by Curial on 2007-07-03
Bé, cal llegir-ho tot, fins hi tot la lletra petita!!

Pel qui li pugui interessar:

Seguint el consell d'en Papapep he visitat la pàgina on donen tots aquests drivers i baixant el que sortia pel meu model d'scanner no funcionava.

Bé, com que originariament el tenia funcionant en l'XP he vist que dins de c:\windows\system32\drivers (TAL COM DEIA AQUESTA WEB) i havia l'arxiu A2NFw.usb (en el meu cas), i l'he copiat a l'escriptori.(abans ho feia amb l'A2DFw.usb el que no funcionava).

Llavors sí, al fer: sudo cp /home/(elmeuusuari)/Desktop/A2NFw.usb /usr/share/sane/gt68xx s'ha copiat al costat de l'altre i l'xsane ha funcionat sense problemes.

Una vegada més, gràcies per la vostra ajuda.

---

