---
title: "WD sata"
date: 2007-06-15
forum: Argentina Team
---

### Post by Apipote on 2007-06-15
tengo un wd sata 250, y segun veo en hdparm, no esta activado el modo udma5.
Como puedo hacer?
Gracias.

---

### Post by Apipote on 2007-06-19
Ahhhh bueno gracias !!!!!!!

---

### Post by Al_maverick on 2007-06-19
podrias explicar con mas detalle que es lo que intentas hacer? Siendo un SATA los datos de la interfaz SATA tambien pueden ser de utilidad.

Y el sarcasmo es una buena forma de descargarse, pero no de pedir ayuda. ;)

---

### Post by Apipote on 2007-06-19
No se mucho Maveric solo que cuando ejecuto hdparm, no estan activados los udma. He leido que  hdparm no sirve para sata y que el kernel lo setea bien.
El punto es, remover hdparm de "services" para ganar recursos.
Gracias por contestar
;)

---

### Post by Al_maverick on 2007-06-19
> **Apipote said:**
> No se mucho Maveric solo que cuando ejecuto hdparm, no estan activados los udma. He leido que  hdparm no sirve para sata y que el kernel lo setea bien.
El punto es, remover hdparm de "services" para ganar recursos.
Gracias por contestar
;)

Esta thread tiene informacion sobre el tema. [http://ubuntuforums.org/showthread.php?t=400356](http://ubuntuforums.org/showthread.php?t=400356)

Pero me parece que no lo podes dar de baja de servicios, aunque no busque en profundidad.

---

### Post by clasificado on 2007-06-19
este link tiene algo de info

[http://webpacifica.blogspot.com/2006/05/por-fin-udma5-en-mi-linux.html](http://webpacifica.blogspot.com/2006/05/por-fin-udma5-en-mi-linux.html)

No es sata, pero el zanguango agrega como parametro del grub, un ide0=ata66. Por ahi haya un equivalente para sata

Clasificado

---

### Post by Apipote on 2007-06-20
Se agradece !

---

