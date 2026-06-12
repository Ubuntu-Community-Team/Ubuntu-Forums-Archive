---
title: "Error en Synaptic"
date: 2007-06-17
forum: Catalan Team
---

### Post by ealbert on 2007-06-17
Al intentar obrir el Synaptic  hem diu:

S'ha produït un error
Es proveeixen els detalls següents:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

La última cosa que he fet ha estat intentar instal-lar noves fonts i possiblement l'he espifiat.

Soc un nou vingut, que esta força verd i per tant  agrairé una "bona" ajuda

---

### Post by crazyserver on 2007-06-17
Doncs llegint es va a Roma!
Prova:
Obrir un terminal i fer
sudo dpkg --configure -a

---

### Post by ealbert on 2007-06-17
Crazyserver, gràcies. ;)
Ara ja puc entrar de nou al Synaptic, tot i que al fer-ho m'indica que:

Teniu 1 paquet trencat al vostre sistema!
Utilitzeu el filtre «Trencats» per a trobar-lo

he anat a synaptic > paràmetres > filtres > trencat
hem surt la finestra "filtres",  i en la pestanya estat figura seleccionat "trencat"
però, a partir d'aquí no se que tinc de fer? la alternativa "suprimeix" es la correcta?

---

### Post by ealbert on 2007-06-17
Ja està arreglat. tot era qüestió d'anar-ho provant

Molt agraït!

---

### Post by crazyserver on 2007-06-17
Suprimeix o reinstala, depen del que vulguis fer;)

De res home! estem per això!

---

