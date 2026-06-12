---
title: "Arranc addicional"
date: 2009-11-27
forum: Catalan Team
---

### Post by dafaktor on 2009-11-27
Salutacions,

poso això aquí tot i que no estic segur que hi hagi d'anar.

A veure, resulta que tinc instal·lada la karmic amb un arranc dual del vista que venia preinstal·lat i que gairebé no faig servir.

La idea que fa un temps que porto al cap és tenir un disc extern amb diverses particions en les que anar instal·lant diferents distros o versions, p.ex. Linx Mint, Mandriva…

Doncs bé, ahir vaig cremar un LiveCD de la RC1 de la Linux Mint, vaig iniciar-la i vaig fer la instal·lació en una partició ext4 d’un disc extern (/dev/sdb1). Li vaig dir que instal·lés el grub en aquell disc (/dev/sdb) per por a carregar-me el que tinc ara a /dev/sda.

En iniciar, vaig dir-li a la BIOS que em mostrés el menú de selecció del dispositiu d’arranc i em mostrava el disc extern com arrancable, així que la selecciono i em salta al grub normal que està instal·lat en el disc intern del portàtil (/dev/sda). Pot ser que perquè el MBR apunta al grub de /dev/sda?

Vaig pensar que posats a arrancar la karmic normalment, faria un update-grub per a què la karmic detectés la Mint i posés la entrada corresponent al grub. I així va ser.

El problema és que en reiniciar i seleccionar l’entrada per arrancar la Linux Mint em mostra un missatge d’error que diu “no such device” i em dóna l’uuid. Vaig comprobar que aquest uuid fos correcte i ho és.

Això mateix ho vaig probar amb una instal·lació de la Mandriva One 2010 que tinc en un altre disc extern i el missatge és exactament el mateix però amb l’uuid de l’altre disc.

En canvi, si, a partir de l’opció de menú de la Karmic, creo un disc d’arrancada a partir de la iso de la Linux Mint, en una unitat flash de 8Gb, sí que funciona sense problema.

Algú sap perquè no funciona l’arranc des dels discos externs però sí que funciona des del pen-drive?

Merci.

---

### Post by SiscoGarcia on 2009-11-28
> **dafaktor said:**
> Algú sap perquè no funciona l’arranc des dels discos externs però sí que funciona des del pen-drive?

Sóc bastant neòfit en aquests temes, però potser que tingui a veure amb la configuració de la BIOS. Hi has mirat a "Boot Options" (o com ho digui la teua màquina) a veure si t'ofereix la possibilitat d'arrancar des d'altres dispositius?

---

### Post by dafaktor on 2009-11-28
Sisco, merci per contestar i sí, sí que ho he mirat i de fet ja comento que arrancant des d'un pen de 8Gb, la cosa funciona.

No ho vaig comentar però la màquina és un portàtil HP Pavilion DV7-1110es.

---

