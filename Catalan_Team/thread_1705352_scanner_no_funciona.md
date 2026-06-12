---
title: "scanner no funciona"
date: 2011-03-12
forum: Catalan Team
---

### Post by josep-maria on 2011-03-12
Tinc l'ubuntu 10.10.  He canviat la impressora multifunció HP deskjet F2280 a una HP deskjet 1050, i ara ja no funciona l'escaner. Fins ara sí que funcionava. He posat la impressora actual com a predeterminada. Surt un avís que diu: 'ha fallat l'escaneig, no s'ha pogut connectar a l'escàner'. He mirat a escaneig > document > preferències i em sembla que tot està bé. Suposo que la impressora funciona bé, perquè sí que imprimeix i fa fotocòpies. No he vist cap post igual que aquest.

---

### Post by kukat on 2011-03-14
Amb el Google m'ix de seguida:

[http://web.archiveorange.com/archive/v/g6UmoFWD43zKgWqJJmS8](http://web.archiveorange.com/archive/v/g6UmoFWD43zKgWqJJmS8)

---

### Post by josep-maria on 2011-03-16
Per descarregar el driver que calgui, he entrat a [http://hplipopensource.com](http://hplipopensource.com)
i m'ha dit que l'ubuntu 10.10 ja té els programes de suport hplip 3.10.11 per la meva impressora.

A sistema>administració>impressió, servidor>nou>impressora, hi diu tots els controladors que tinc, i el de la hp 1050 sí que hi és. Pot ser que el driver que tinc serveixi per imprimir però no per escanejar?

Fins ara tenia la HP F2280 i funcionava des del primer dia sense que hagués de fer res.

---

### Post by josep-maria on 2011-03-17
He intentat fer com diu en Narla Naga, però quan obro l'arxiu
/usr/share/hplip/data/model/models.dat
no em deixa fer-hi cap canvi, diu que és 'només lectura'.
Què haig de fer per editar-lo?

---

### Post by wgarcia on 2011-03-18
Pots fer per exemple Alt-F2 i entrar:

gksudo gedit /usr/share/hplip/data/model/models.dat

---

### Post by josep-maria on 2011-03-18
Ho he fet i surt una finestra però en blanc.

---

### Post by wgarcia on 2011-03-18
Potser al teu sistema no hi ha el fitxer "model.dat" a la ruta que dones o està en un altre lloc.

---

### Post by josep-maria on 2011-03-18
He fet sudo a un terminal i ja he pogut fer els canvis que diu en Narla Naga (io-mfp-mode=1 i scan-type=7). Però segueix sense funcionar.

---

### Post by kukat on 2011-03-20
Quin programari per a escanetjar utilitzes??

Pot ser la solució siga reinstal·lar eixe programa o instal·lar altre per provar.

---

### Post by josep-maria on 2011-03-23
Faig servir l' 'escaneig senzill' que ve amb l'ubuntu 10.10. També he descarregat el xsane, però tampoc no funciona. El xsane diu: 'no hi ha cap dispositiu disponible'.

Imprimir sí que ho fa bé, per tant, el driver està ben insta&#320;lat.

---

