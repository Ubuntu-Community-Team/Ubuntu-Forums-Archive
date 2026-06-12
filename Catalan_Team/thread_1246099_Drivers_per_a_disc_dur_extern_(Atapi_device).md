---
title: "Drivers per a disc dur extern (Atapi device)"
date: 2009-08-21
forum: Catalan Team
---

### Post by giorgio73 on 2009-08-21
Hola a tothom,

Fa poc he adquirit un nou disc dur multimedia extern, un EMTEC MOVIE MEDIA s800 de 880 GB, enllaç: 

[http://www.emtec-international.com/es/produit.php?categorie=STMOB&gamme=DISQUES%20DURS&ss_gamme=S800](http://www.emtec-international.com/es/produit.php?categorie=STMOB&gamme=DISQUES%20DURS&ss_gamme=S800)

Però al connectar-lo en Ubuntu té problemes, he mirat l'aplicació DEVICE MANAGER i sembla que sí que el reconeix:

Mass Storage Drive
Model: ATAPI Device
Vendor: 811 ATA
Device File: /dev/sdb
Serial number: 811_ATA._ATAPI_Device-0:0
Connection: USB (evidentment)
Drive capacity: 0,0 KB (0 bytes)
Partitioning: -

Però no tinc els coneixements adeqüats per a posar-lo en marxa, algú em pot ajudar, sisplau?. :confused:

El meu ordinador es un Pentium Celeron 1,7 GB (com un P IV), 1 GB RAM, 500 GB HD, la versió d'UBUNTU es la última (9.0.6?).
[B]Gràcies!!! :lolflag:
[/B]

---

### Post by papapep on 2009-08-21
Benvingut al fòrum, Giorgio73.

És possible que el disc no estigui formatat? de ser així, no te'l mostra per que no el pot muntar. Si vas a Sistema > Administració > Editor de particions, hauries de veure el dispositiu /dev/sdb, com està particionat i si té algun sistema de fitxers o no.

Si no trobes l'editor de particions al menú, amb un:

```
sudo aptitude install gparted
```

l'instal·les.

---

