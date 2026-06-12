---
title: "XP, partició..."
date: 2009-05-07
forum: Catalan Team
---

### Post by clydebam on 2009-05-07
M’explico: treballo amb Windows Xp. Per culpa d’un (suposat) virus, l’ordinador es reinicia just abans de la pantalla “Bienvenido”.
Per sort tinc un cd de l’Ubuntu i he pogut engegar. La meva intenció era particionar el disc dur per instal.lar l’Ubuntu (ara ho faig amb el LiveCD) i així mirar d’arreglar el Windows. Però el GParted em diu que “Minimum size” 76309mb i que “Maximum size” 76317mb, és a dir, que només em deixa 8mb!
Què puc fer??
Moltes gràcies.

---

### Post by socderafel on 2009-05-07
76317mb son 76 gb (Gigabytes)... però supose que serà una errata.
Abans de fer una partició nova, li has de llevar espai a un altra. 
Jo no he gastat el Gparted, però supose que serà alguna cosa del tipus resize o algo així...

---

### Post by torracastanyes on 2009-05-07
Tal com diu socderafel, has de reduïr la partició original per crear-ne una de nova, però no et descuidis de desfragmentar el disc avans de tocar res.

---

### Post by clydebam on 2009-05-07
El problema es que no puc entrar a Windows... A partir de l-Ubuntu, entro a la partici'o on hi ha Windows pero no puc fer res de res.
I ara es quan se m-acut la pregunta del mil.lio! Puc fer un resize d-on hi ha Windows, estan aquest ja instal.lat?
I acabo de veure que tinc el teclat totalment desconfigurat...
Gracies per les respostes!

---

### Post by socderafel on 2009-05-07
crec que mentre el disc o la partició on estigui windows no estigui montada, pots tocar-la... que algú em corregeixca si m'equivoque..

---

### Post by mcako on 2009-05-07
Per desfragmentar no cal que entris en el propi Windows, pots fer-ho amb el cd de instal·lació de Windows. Hi ha una opció en el menú del cd que es diu "Consola de recuperación", és una consola que té unes comandes especials i serveix precisament per fer coses així. 
Hi han comandes interessants com FIXMBR o FIXBOOT, que serveixen per reparar el sector d'arranc del sistema, però a mi fins ara no m'han funcionat mai per reparar errors com el que tu comentes.
Pots provar alguna d'aquestes comandes o també fer un check disk (CHKDSK) per corregir possibles errors del disc.
Per desfragmentar crec que la consola aquesta no porta la comanda, no ho recordo, de totes maneres sempre pots accedir al disc dur i anar a C:\WINDOWS\system32\ i executar la comanda "defrag". Has de tenir bastant d'espai lliure al disc per poder desfragmentar correctament.

---

### Post by clydebam on 2009-05-08
Res, no hi ha manera...
Quan faig doble click a defrag, ni s'immuta...
I el CD d'instal.lació de Windows, sincerament no se pas on para; tres anys i mig amb aquest ordinador i el CD a saber on el tinc... Crec que el que executaré, és una mesura dràstica. Formatejar!

---

### Post by quitus on 2009-05-08
> **clydebam said:**
>  Crec que el que executaré, és una mesura dràstica. Formatejar!


això, formateja i llença'l a les escombraries, el windows, es clar.

salut

---

### Post by torracastanyes on 2009-05-08
Si suposadament és un virus, jo miraría d'escanejar el disc amb un live-cd que porti algún antivirus potent.

---

