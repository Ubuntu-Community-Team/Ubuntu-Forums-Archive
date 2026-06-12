---
title: "problemes amb permissos"
date: 2007-07-05
forum: Catalan Team
---

### Post by browly on 2007-07-05
Hola! Soc nou a ubuntu, i com tots els nous tinc ganes de aprendre i també molts problemes, jejeje. 

Us explico el problema a veure si algu hem pot ajudar, ho agrairé moltisim! 

Tinc un portatil d'un company amb el sistema operatiu windows rebentat degut a un virus. No puc entrar de cap de les maneres. Per sort, les imatges i els documents d'interés estaven a una altra partició de disc. El que he fet ha sigut executar ubuntu 7.04 desde el cd per veure si els arxius estaven en condicions. Els arxius estaven en condicions!

Problema, ara vull copiar aquests arxius al usb i no hem deixa. Hem diu que el disc usb nomes te permis de lectura. I no li puc cambiar el permís a escritura!! El dics el veig perfectament i hem deixa llegir correctament, pero no esciure.

Algu se li acut alguna cosa?? o potser us falta més informació!

---

### Post by CarlesOriol on 2007-07-05
Deus tenir l'usb formatejat en NTFS. I l'arrencada en mode live no carrega els controladors de lectura / escriptura.

Formateja la clau en fat.

---

### Post by ernestux on 2007-07-06
Un dispositiu de memòria es pot re formatejar a FAT32  o  fins i tot a ext3 sense problema ?
Igualment per un disc dur extern de 120 GB ? Sempre serà millor passar-lo a fat que tenir-lo en NTFS, no?

Gràcies

---

### Post by CarlesOriol on 2007-07-06
No, no... no ho passis a ntfs.

El sistema fat no és resistent a errors i com més gran sigui el disc i més l'utilitzis menys trigaras a tenir problemes.

Per SDs o memories USB de poques gigues que usem com a transport és perfecte per que sabem segur que ens funcionarà en qualsevol sistema però per discs externs millor formatejar-lo en el sistema amb el que pensis usar-lo principalment.

Tingues en compte les limitacions de cada sistema:

 fat - Inestable, limitat en espai, no diferencia en arxius en minúscules i majúscules i això pot produir-te problemes al copiar arxius. Compatible amb la majoria de dispositius i sistemes.

 ntfs - Estable, si comprimeixes sols pots usar-lo en windows, cal ntfs-3g per poder escriure-hi. Lent en l'ús en linux. No diferencia en arxius en minúscules i majúscules i això pot produir-te problemes al copiar arxius.

 ext3 - Estable. Calen controladors especials per usar-lo en windows. Perfecte per totes les operacions en gnu/linux. 

En l'ubuntu pots realitzar totes les operacions en gnome amb el programa gparted.

---

