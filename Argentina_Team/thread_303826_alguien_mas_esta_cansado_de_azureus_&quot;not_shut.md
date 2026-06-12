---
title: "alguien mas esta cansado de azureus &quot;not shutting down tidily&quot;???"
date: 2006-11-20
forum: Argentina Team
---

### Post by ariel on 2006-11-20
Alguien encontró una solución? 

Hace dos años que me pase a Linux, y hace dos años que veo los cartelitos de azureus  cada vez que prendo la maquina. Ya es hora de encontrar una solución (digo, una que no sea hacer File > Quit en azureus antes de apagar :-) )

Se ve que no es tan facil, mucha gente viene preguntando esto una y otra vez.

[http://ubuntuforums.org/showthread.php?t=71112](http://ubuntuforums.org/showthread.php?t=71112)

Chasgracias

---

### Post by beuno on 2006-11-20
Nunca me paso, pero por lo que veo es porque apagas la PC sin cerrar vos manualmente el Azureus.
¿Porque?

---

### Post by kalel on 2006-11-20
yo cuando empeze a usar torrent hace 3 años  que todavia no era conocido como ahora, empeze con el azureus, y hasta hace unos meses seguia, pero me hincho las bolas el tema de java, se hace pesado el cliente y encima no tiene opcion de buscar, cosa  que otros clientes mas livianos si tienen.

yo la opcion ke te doy es que pruebes estos 2 clientes

ktorrent

deluge



los dos son livianos, bajan muy bien y tienen buscador.

---

### Post by Nemesis Teufel on 2006-11-20
a me pasaba con dapper y no tiene nada que ver como apagues tu pc.. apenas abrias el azureus aparecia ese cartel que era imposible de cerrar (aunque cierres el programa) y estaba siempre "On top" hagas lo q hagas..
cuando instale edgy y azureus el problema no aparecio..
yo postie en este foro lo que me pasaba y nadie sabia.. hasta en un foro de azureus en aleman y nadie sabia nada.

---

### Post by beuno on 2006-11-21
> **Nemesis Teufel said:**
> a me pasaba con dapper y no tiene nada que ver como apagues tu pc.. apenas abrias el azureus aparecia ese cartel que era imposible de cerrar (aunque cierres el programa) y estaba siempre "On top" hagas lo q hagas..
cuando instale edgy y azureus el problema no aparecio..
yo postie en este foro lo que me pasaba y nadie sabia.. hasta en un foro de azureus en aleman y nadie sabia nada.

Era un problema en Dapper con el azureus.
Esta es la solucion:  [http://www.kbglob.com/gnulinux/ubuntu/azureus-usable-en-ubuntu-dapper/](http://www.kbglob.com/gnulinux/ubuntu/azureus-usable-en-ubuntu-dapper/)

(obviamente tarde, pero por ahi a alguno le sirve)

---

### Post by cocotapioca on 2006-11-21
odio el azureus, yo quiero algo que sea igual o mejor que el uTorrent ...

---

### Post by spg76 on 2006-11-21
> **cocotapioca said:**
> odio el azureus, yo quiero algo que sea igual o mejor que el uTorrent ...

Como a mi tampoco me convence, estoy usando la combinación Wine+uTorrent que me funciona mejor que cualquier cliente nativo.
Un proyecto interesante que funciona bastante bien es Deluge ([http://deluge-torrent.org/trac]("http://deluge-torrent.org/trac")). Lamentablemente no está soportado por muchos trackers (sobre todo privados).

---

### Post by cocotapioca on 2006-11-21
yo uso la misma combinacion o el cliente default de bt

---

### Post by tzulberti on 2006-11-21
Yo uso el bittornado... aunque no es lo mejor que ahi porque casi siempre cuando se lo cierra aparece un mensaje de que ha sido cerrado incorrectamente, que reportes un bug (creo que el proyecto esta abandonado, o esta cerca de abandonarse)

---

### Post by ariel on 2006-11-21
> **beuno said:**
> Nunca me paso, pero por lo que veo es porque apagas la PC sin cerrar vos manualmente el Azureus.
¿Porque?

Siempre configuro System>Preferences>sessions para que azureus y amule se carguen solitos al inicio de sesion. Y normalmente apago la pc con el iconito de la puerta de salida. Sé que si cierro azureus y despues apago la pc el problema no se da, pero nunca me acuerdo de hacerlo.

Una alternativa es hacer killall java, en alguno de los scripts de shutdown, antes que the cierre gdm, lo que no se bien es en cual script, algun guru dice que lo hizo andar pero no contó qué script hay que modificar.

uso azureus mas que nada por costumbre, desde hace muchos anios, fue el primer cliente bittorrent que me gusto, cuando todavia tenia dual boot. Hace poco lei sobre deluge, parace que va a estar muy bueno pero todavia debe estar medio verde, no parece estar en las repos / synaptics.

Me gustaria probar deluge, pero igual no tengo nada contra java; con azureus bajando a 4mbps promedio, java se lleva 50MB de ram (sobre un 1GB) y menos de 1% de cpu, y es ultra estable (doy fe :) )

---

### Post by leo1a0 on 2006-12-01
>  
Era un problema en Dapper con el azureus.
Esta es la solucion: [http://www.kbglob.com/gnulinux/ubunt...ubuntu-dapper/](http://www.kbglob.com/gnulinux/ubunt...ubuntu-dapper/)

(obviamente tarde, pero por ahi a alguno le sirve)
Gracias, funciona perfecto.

---

