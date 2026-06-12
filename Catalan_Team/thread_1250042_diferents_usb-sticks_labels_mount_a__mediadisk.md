---
title: "diferents usb-sticks labels mount a  /media/disk"
date: 2009-08-26
forum: Catalan Team
---

### Post by ctw on 2009-08-26
Hola a tothom,

magradaria saber com puc configurar l'automuntage dels dispositius usb (pendrives, disc durs externs) que vinguin amb diferents noms, en els labels de cada dispositiu, i que automáticament es muntin dintre /media/disk.

Es a dir, a vegades em trobo un dispositu d'un client (memoria usb de 1Gb) que te el label de "miquel" i el automuntage que em fa l'ubuntu m'el fa a /media/miquel. M'agradaria que cada dispositiu usb que automunti  l'ubuntu el fes sempre a /media/disk .


Algú em pot donar un cop de mà? Gràcies.

---

### Post by papapep on 2009-08-26
[Aquí]("http://ubuntu-tutorials.com/2006/12/06/how-to-always-mount-removable-drives-in-the-same-place-ubuntu-6061-610/") en parlen. Tot i això, juraria que algú va obrir un fil explicant com ho feia amb l'udev (Patrick?), però no l'he sapigut trobar amb una cerca ràpida.

---

### Post by LitusMayol on 2009-08-26
> **papapep said:**
> [Aquí]("http://ubuntu-tutorials.com/2006/12/06/how-to-always-mount-removable-drives-in-the-same-place-ubuntu-6061-610/") en parlen. Tot i això, juraria que algú va obrir un fil explicant com ho feia amb l'udev (Patrick?), però no l'he sapigut trobar amb una cerca ràpida.

**Papapep**, pot ser que parlis d'[aquest]("http://ubuntuforums.org/showthread.php?t=617265&highlight=canviar+nom+usb") fil?

---

### Post by papapep on 2009-08-26
> Papapep, pot ser que parlis d'aquest fil? 

Nops, era un que parlava de l'[udev]("http://es.wikipedia.org/wiki/Udev") i de com configurar-lo per a muntar d'una manera predeterminada els dispositius d'emmagatzematge USB.

Gràcies per l'intent ;)

---

### Post by papapep on 2009-08-26
Ei! ja l'he trobat! No era aquí, era al wiki de l'equip (és el que té tenir tantes fonts d'informació, al final perds el fil d'on llegeixes què...):

[https://wiki.ubuntu.com/CatalanTeam/Recursos/Copies_de_seguretat](https://wiki.ubuntu.com/CatalanTeam/Recursos/Copies_de_seguretat)

L'article no és específicament de l'udev, però en parla per a fer-lo servir.
Un molt bon article d'en Patrick, que de tant en tant ens en deixa anar un d'especial ;)

---

### Post by PatrickVogeli on 2009-08-27
> **papapep said:**
> Un molt bon article d'en Patrick, que de tant en tant ens en deixa anar un d'especial ;)

Em faras posar vermell i tot.. :D

Amb l'udev es pot fer, si. Ara mateix no se massa com, però he mirat una mica per sobre l'enllaç que t'han passat i sembla ser el que busques. Si vols, ja m'ho miraré amb més calma i t'intentaré orientar una mica més.

Salut

---

### Post by CarlesOriol on 2009-08-29
Em sembla que el tema udev a canviat força a la darrera versio'. Algu' pot confirmar que això que diu en papapep funciona?

---

### Post by ctw on 2009-09-23
gracies per l'ajuda

---

