---
title: "ubuntu 14.04 no mostra la unitat de CD / DVD"
date: 2015-04-15
forum: Catalan Team
---

### Post by silviacmorales on 2015-04-15
Hola!

He provat de moltes maneres, però les unitats de CDDVD no apareixen de cap manera al meu ordinador. Tinc instal·lada una unitat de DVD de LG i ara no hi puc accedir, ni tan sols surt a la llista de discos de l'explorador. Vaig provar amb una unitat lectora portàtil de CD per si era cosa de la LG i tampoc funciona. 

Mirant diferents fils de gent amb problemes semblants vaig provar de fer a la terminal un "dmesg | grep CD"  i surt aquest texte:

[    4.904296] scsi 11:0:0:0: CD-ROM            TSSTcorp CDDVDW SE-208DB  TS01 PQ: 0 ANSI: 0
[    4.927904] cdrom: Uniform CD-ROM driver Revision: 3.20
[    4.928017] sr 11:0:0:0: Attached scsi CD-ROM sr0

està detectant alguna cosa? ... a partir d'aquest punt ja no sé qué fer...el fil que parlava d'això no continua,...algú em pot ajudar?

---

### Post by wgarcia on 2015-04-16
Una pregunta tonta: Li poses un CD a dins, oi? Perquè sols ho munta si hi ha un CD a dins...

---

### Post by silviacmorales on 2015-04-16
Sí, sí...   ;)
he provat també diferents CDs, per si de cas

---

### Post by wgarcia on 2015-04-16
Tens un USB d'instal·lació de l'Ubuntu? Pots provar una sessió iniciant l'ordinador amb aquest USB, i provar la unitat de CD/DVD des de la sessió d'USB?

---

### Post by silviacmorales on 2015-04-16
Merci, ho provaré. A veure qué passa

---

