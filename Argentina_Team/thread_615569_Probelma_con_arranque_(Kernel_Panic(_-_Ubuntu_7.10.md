---
title: "Probelma con arranque (Kernel Panic( - Ubuntu 7.10"
date: 2007-11-17
forum: Argentina Team
---

### Post by matlnx on 2007-11-17
Buenos dias, les comento lo que me anda pasando ya que es muy raro, y google no supo informarme ;)

Tengo en mi pc tres SO (Ubuntu 7.10, XP y VIsta). Los dos windows son por un tema de juegos ;) aunque desde que tengo el cubo habilitado me divierto bastante jajaja (sisi me divierto barato)

El tema es que cuando inicio la pc, hay veces en las cuales durante el arranque se queda colgada y "titilan las luces del teclado de Mayuscula (bloq mayus) y Scroll Lock (¿?)", realmente insolito.

Hoy tratando de ingresar no habia forma por lo cual ingrese en modo seguro (Ubuntu Safe Mode) y veo que hace lo mismo con la diferencia que se cuelga en la parte que dice:
***[5.644000] Kernel Panic - not syncing: creation of kmalloc slab kmalloc_dmz-512 size=512 failed***
Vale acalrar que en ese momento tambien empiezan a titilar las mencionadas luces.

Desde ya muchas gracias.
Mati

---

### Post by Hei Ku on 2007-11-17
Eso parece un error de memoria. Proba a correrle un memtest, a ver q dice.

---

### Post by Mister X on 2007-11-21
Bueno, me acaba de pasar exactamente lo mismo despues de reiniciar...
Tengo la 7.10 desde hace casi un mes y es la primera vez que sucede.
Estube buscando en google y no encontre nada, vamos a ver si se repite...

---

### Post by matlnx on 2007-11-21
Hice un memTest pero nada, lo deje 6 horas corriendo (entre que me fui a la facu y volvi) y no detecto ningún problema.

Lo raro es que tengo Windows Vista y XP en la misma PC y arrancan sin ningún problema...

Si alguno tiene algun dato se agradece ;)

---

### Post by matlnx on 2007-12-03
> **matlnx said:**
> Buenos dias, les comento lo que me anda pasando ya que es muy raro, y google no supo informarme ;)

Tengo en mi pc tres SO (Ubuntu 7.10, XP y VIsta). Los dos windows son por un tema de juegos ;) aunque desde que tengo el cubo habilitado me divierto bastante jajaja (sisi me divierto barato)

El tema es que cuando inicio la pc, hay veces en las cuales durante el arranque se queda colgada y "titilan las luces del teclado de Mayuscula (bloq mayus) y Scroll Lock (¿?)", realmente insolito.

Hoy tratando de ingresar no habia forma por lo cual ingrese en modo seguro (Ubuntu Safe Mode) y veo que hace lo mismo con la diferencia que se cuelga en la parte que dice:
***[5.644000] Kernel Panic - not syncing: creation of kmalloc slab kmalloc_dmz-512 size=512 failed***
Vale acalrar que en ese momento tambien empiezan a titilar las mencionadas luces.

Desde ya muchas gracias.
Mati

a

---

### Post by matlnx on 2007-12-03
> **matlnx said:**
> a

Buenos dias, al fin de cuentas se soluciono elproblema. En el foro de ubuntu USA luego de mucho buscar una persona me comento que podía ser un problema al momento de actualizar mi version 7.04 de Ubuntu a la 7.10, con lo cual queme la nueva version en un CD y procedi a instalarla de cero. Luego de las actualizaciones y de dejarla como mi Ubuntu Anterior no volvio a aparecer dicho problema y arranca normalmente.

Un abrazo
MatLnx

---

### Post by User21 on 2007-12-03
AAAH! ok! :D

---

