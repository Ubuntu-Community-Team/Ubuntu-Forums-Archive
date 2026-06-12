---
title: "Desinstalar Ubuntu"
date: 2007-02-07
forum: Argentina Team
---

### Post by Biasoli on 2007-02-07
Hola!
Otra vez yo, pero esta vez vengo a consultar como desinstalar, no como instalar!
Bueno el tema es que mi disco es de 80 GB.
Al momento de asignarle el tamaño a la particion de Linux, mi idea era 15 GB para Linux y el resto para Windows.
El problema es que me salio al revez :lolflag:
Ahora lo que quisiera hacer es lo siguiente:

1) Desinstalar Linux.
2) Borrar (formatear) la particion de Linux.
3) Y por ultimo, asignar ese espacio sobrante a la particion de Windows.

Mis dudas son:

1) Como hacerlo (:mrgreen:)
2) Al hacer esto, corro el riesgo de perder la informacion de la particion de Windows?

Gracias!

---

### Post by beuno on 2007-02-07
Te diria que lo mas facil es conseguirte el "partition magic" y con eso lo editas casi sin riesgos.

---

### Post by Biasoli on 2007-02-07
Si lo que pasa es qie el partition magic ya me jugo una mala pasada (por el tuve que formatear hace unas 3 semanas).
Pero voy a intentar.
De todas maneras, si existe otro metodo, por favor no dudes en comentarmelo!

Gracias!

---

### Post by beuno on 2007-02-07
Es *posible* que desde windows, desde "herramientas administrativas" > "administrador de dispositivos" o algo asi, hace mucho que no uso win, puedas hacer click derecho y formatear tambien.

---

### Post by quaid on 2007-02-07
> **beuno said:**
> Es *posible* que desde windows, desde "herramientas administrativas" > "administrador de dispositivos" o algo asi, hace mucho que no uso win, puedas hacer click derecho y formatear tambien.

Es asi, y ahi vas a admin de discos logicos, eleguis la particion y le das formatear.

Para instalar Linux y q no te pase loq te paso de nuevo deberias de:

1- Antes q nada un fdisk /mbr (asi volas grub)
2- Format a la particion de 65  y la pones en ntfs
2- Fdisk (con disco de arranque) y eliminas la particion de 15 (no la formatees)
3- Instalas win en la de 65
4- cuando instalas ubuntu pone q use el espacio libre continuo mas grande (va a usar el de 15 q no tiene formato) y automaticamente te hace la swap y etc.
5- listo! Win en el de 65 y linux en el de 15

---

### Post by Biasoli on 2007-02-07
> Es *posible* que desde windows, desde "herramientas administrativas" > "administrador de dispositivos" o algo asi, hace mucho que no uso win, puedas hacer click derecho y formatear tambien.> Es asi, y ahi vas a admin de discos logicos, eleguis la particion y le das formatear.Hice eso, y elimine las particiones de Linux (una tenia 65 GB mas o menos y la otra 2 GB que supongo seria la swap).
Y me quedo esto:

[IMG]http://img103.imageshack.us/img103/1677/particionjpgeh5.jpg[/IMG]

Ahora mis dudas son:

1) ¿Como le asigno ese espacio libre a la particion de Windows?

>  Para instalar Linux y q no te pase loq te paso de nuevo deberias de:

1- Antes q nada un fdisk /mbr (asi volas grub)
2- Format a la particion de 65  y la pones en ntfs
2- Fdisk (con disco de arranque) y eliminas la particion de 15 (no la formatees)
3- Instalas win en la de 65
4- cuando instalas ubuntu pone q use el espacio libre continuo mas grande (va a usar el de 15 q no tiene formato) y automaticamente te hace la swap y etc.
5- listo! Win en el de 65 y linux en el de 15

Me viene bien para mas adelante, gracias!


Saludos!

---

### Post by beuno on 2007-02-07
Para unir dos particiones en una vas a necesitar si o si el partition magic.

---

### Post by Biasoli on 2007-02-07
Si no queda otra alternativa...
Esta bien.

Gracias!

---

### Post by Biasoli on 2007-02-07
Listo, ya pude redimenzionar la particion.

Muchas gracias!

---

