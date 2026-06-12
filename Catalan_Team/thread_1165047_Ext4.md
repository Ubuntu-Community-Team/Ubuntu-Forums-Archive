---
title: "Ext4"
date: 2009-05-20
forum: Catalan Team
---

### Post by PatrickVogeli on 2009-05-20
Hola gent,

obro aquest fil a veure si comenteu les vostres experiències amb el nou sistema de fitxers ext4.

Pels comentaris que he llegit, sembla que n'hi ha alguns que n'esteu molt contents, altres dubteu, d'altres de moment espereu..

No tenia pensat provar-lo, pero al llegir que es pot passar d'un a l'altre sense perdre dades i tal... doncs potser ho provo. Com es fa? Un cop passat a ext4, es podria tornar a ext3?

En fi... a veure que me'n sabeu dir.

Salut!

---

### Post by papapep on 2009-05-20
> Com es fa?

[Aquí]("http://extralinux.net/?q=node/209") en parlo.

>  Un cop passat a ext4, es podria tornar a ext3?

Nops...això ja seria massa meravellós... ;)

---

### Post by marteljorge on 2009-05-20
Crec que seria com voler passar d'ext3 a ext2...
Peró, si voldries tornar arrere, només has de fer un còpia de seguretat.

---

### Post by PatrickVogeli on 2009-05-20
bé, m'he llançat a la piscina amb les instruccions del papapep... i de moment el pc ha arrancat, que ja es molt!

Salut!!

EDITO: gracies papapep!!

---

### Post by papapep on 2009-05-20
> **marteljorge said:**
> Crec que seria com voler passar d'ext3 a ext2...

El canvi de [Ext2]("http://es.wikipedia.org/wiki/Ext2") a [Ext3]("http://es.wikipedia.org/wiki/Ext3") no és gaire més que afegir-hi el [journaling]("http://es.wikipedia.org/wiki/Journaling"). Fixa't si és així, que un ext3 es pot muntar com a ext2 (sense journaling) sense gaires mals de cap.

El canvi de Ext3 a Ext4, en canvi, és un profund canvi d'estructura interna i de [multitud de funcionalitats]("http://ext4.wiki.kernel.org/index.php/New_ext4_features") que intenten millorar àmpliament el rendiment i fiabilitat d'ext2 i ext3.

> 
Peró, si voldries tornar arrere, només has de fer un còpia de seguretat.

En Patrick es refereix "literalment" a desfer la modificació del sistema de fitxers d'ext3 a ext4, no a recuperar les dades i reformatar la partició. I això, per ara i tant, no és possible :)

---

### Post by prostata on 2009-05-21
Doncs les meves impressions sobre EXT4 fins a dìa d'avui son molt bones, res a dir, és estable i molt, va força més ràpid...merevellos...!!! si de cas pot ser actualitzar al Grub2 però això ja son figues d'altre...

Salutacions

---

### Post by sianeu on 2009-05-22
Jo puc explicar que tinc un ordinador ubuntu jaunty i ext4 amb el /home en un altre partició i ext3 funcionant, de moment, molt bé. Com es un ordinador antic, li he afegit el escritori xubuntu com explica el papapep en un altre fil
> sudo aptitude install xubuntu-desktop
i ara funciona molt millor.

Salut

---

### Post by jaume69 on 2009-05-22
Jo també he posat **ext4** però ho he fet manualment desde l´instalador d´Ubuntu,perque em sembla que si no l´hi dius t´ho monta amb **ext3** per defecte.
Vaig provar de passar de ext3 a ext4 de no sé quina web i no em va anar bé,em vaig quedar sense boot,o algo així.Anava reiniciant continuament i fen les proves del HD.
I vaig formatar de nou...,els "retrasats"  ho hem de fer així.

I efectivament va força més bé,en arrencada i tancada de l´ordinador.El sistema va una mica més ràpid,també.
Llàstima que el **HD** que tinc ja l´he formatat unes quantes vegades,sino podria veure més clarament la diferència entre **ext3 i ext4**.

---

### Post by akyra on 2009-05-25
Jo vaig formatejar la partició a ext4 "/" quan vaig instal·lar el 9.04, i el que puc dir que el temps d'arancada s'ha reduït entorn dels 30 segons.

Tinc la particio /home, amb ext3 i voldria convertirla a ext4, però aquí tinc dades que no voldria perdre.

Si algú ho ha probat i pot dir que tal li ha anat li agrairia.

Adeu.

---

### Post by oriolsbd on 2009-05-25
El Papapep ha enviat en una resposta anterior un enllaç al seu blog on explica com fer-ho: [http://extralinux.net/?q=node/209](http://extralinux.net/?q=node/209) :-)

Salut!

---

### Post by akyra on 2009-05-25
Gracies ho probaré.

---

### Post by PatrickVogeli on 2009-05-25
el cas d'arrancar rapid el pc pse... ara que ho tinc en ext4 no noto diferencia de quan ho tenia en ext3. Pero en ambdos casos el sistema arrancar moltissim més ràpid que el 8.10 i el 8.04, suposo que degut a la feina que han fet amb l'upstart.

---

