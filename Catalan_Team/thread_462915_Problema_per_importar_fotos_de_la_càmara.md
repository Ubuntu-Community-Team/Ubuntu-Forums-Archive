---
title: "Problema per importar fotos de la càmara"
date: 2007-06-03
forum: Catalan Team
---

### Post by cortsenc on 2007-06-03
Al conectar la càmara de fotos (amb USB) em posa aquest error:

[COLOR="DimGray"]An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.[/COLOR]


Fins ara podia sense problemes.

---

### Post by papapep on 2007-06-03
Ostres i, entre que anava i ara, no has instal·lat o desinstal·lat res?? Sembla extrany que s'hagi espatllat així espontàniament, no?

---

### Post by cortsenc on 2007-06-04
Doncs si, de fet es a l'ordinador del meu germà que falla... i diu que no ha toca res (típic).

No se, ho posava aquí perquè potser per l'error algú em diu, doncs reinstal·la aquest paquet o tal altre...

---

### Post by orestesmas on 2007-06-04
Comprova els permisos. Executa el gphoto2 com a usuari normal i com a root.

(gphoto2 -P et baixa totes les fotos)

---

