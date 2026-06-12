---
title: "Mal Update de kernel"
date: 2006-12-14
forum: Argentina Team
---

### Post by cocotapioca on 2006-12-14
Hoy a la mañana puse a bajar unos updates que habia. Cuando vuelvo ya se instalaron , me dice de rebootear , lo hago y nunca mas pudo iniciar mas ubuntu.Los errores que me da al iniciar son de uqe  no encuentra el archivo /lib/modules/2.6.17-10-386/module.dep
la cuestion q iniciando un una imgen 2 generaciones pasadas(la anterior me da otro error ahora algo con el /etc/mdadm/mdadm.conf) llego al shell porque las x no me andan mas x el driver. Efectivamente el archivo no esta e incluso la estructura del dir es distinta a las de las otras versiones.

Aalguno le paso? el update fue incorrecto? mañana voy a conseguir un cd de ubuntu y lo vamos a reinstalar en el disco secundario ...

---

### Post by spg76 on 2006-12-14
No sos el único.
Aparentemente es un problema con drivers de Nvidia según dice la [pagina principal del foro]("http://ubuntuforums.org/index.php").
Abrieron [este thread]("http://ubuntuforums.org/showthread.php?t=318206") con respecto a este incoveniente.

---

### Post by cocotapioca on 2006-12-16
ya esta, la unica solucion que funciono fue reinstalar ubuntu ....

---

### Post by felipelerena on 2006-12-16
> ya esta, la unica solucion que funciono fue reinstalar ubuntu...
no!!! eso fue innecesario.
la proxima vez que te pase algo asi hace esto:
```
w3m www.ubuntuforums.org
``` y te fijas si hay gente con el mismop problema.
cuando viene mal un update viene mal para mucha gente.
hace algunos meses paso que un update de Xorg le cago al PC a todos los que tenian el repo de backports abierto (y eso es MUUUUUUCHA gente) por suerte estaban muchos desarrolladores reunidos no se en donde y le arreglaron el problema a todo el mundo en un pedo.

CONSEJO: cuando veas que hay un paquete del kernel, de xorg o de drivers de video espera un dio o dos para actualizarlos.

---

