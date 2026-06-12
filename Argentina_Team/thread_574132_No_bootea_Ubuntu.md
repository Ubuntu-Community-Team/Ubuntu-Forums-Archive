---
title: "No bootea Ubuntu"
date: 2007-10-12
forum: Argentina Team
---

### Post by angelqpro on 2007-10-12
Luego de desistir de instalar Ubuntu en un array RAID 0, opté por agregar un tercer disco SATA.
Instalé Ubuntu, el gestor de arranque en el C  (o), pero no funciona.
El C tiene un doble boot entre Vista y XP, de Moco$oft, y sospecho que el problema pasa por ahi. pero no se como resolverlo.
Y no puedo optar por establecer orden de arranque con ese disco. la bios no me da opcion. Solo Hard Disk. Y no es una BIOS reudcida, ya la mobo  es una Asus M2N 32 SLI De Luxe Wi Fi

Desde ya muchas gracias, amigos. En otro equipo con un solo disco todo fue 10 puntos.

---

### Post by tzulberti on 2007-10-12
Pregunta simple: que mensaje te aparece cuando intentas de bootear ubuntu? O ni siquiera te aparece el grub?

Saludos,
TZ

---

### Post by angelqpro on 2007-10-12
No aparece el grub. Solo la opcion de boot desde Windows, comno estaba inicialmente. Es decir, no tengo forma de optar. Supongo que si desconecto los dos discos que integran el RAID funcionaría, ya que bajo las actualizaciones y esta dentro de ese disco. Pero no es la solucion

---

### Post by Mauro22 on 2007-10-12
tendrias que modificar los jumpers de los disco, dejando como master el q bootea con el grub...

Salu2

---

### Post by angelqpro on 2007-10-12
El hecho de ser master o slave no influye en eso. De hecho, trabajo con otra maquina con un carry para discos, y booteo en forma indistinta de cualquiera. Claro esta, todos con Windows. Aunque podria funcionar perfectamente con cualquier SO. No probe el Ubuntu porque ese equipo no se lo banca.

De todas maneras, los tres discos de esta son SATA II.
En la interfase Serial ATA, no existen los slave. Todos son master. Es mas: estos discos ya no tienen jumpers (Salvo los Seagate 7200.10 que utilizo. pero es para configurar SATA I o II)
Aqui tengo dos discos de 320 como master en un array RAID  (en paralelo), mas el tercero de 250 que agregue, tambien master, y una grabadora de DVD SATA, tambien master.
Sucede que esta placa tiene 8 púertos serial ATA II mas uno externo, en el panel trasero. Y todos ellos se utilizan como master.

Lo que me sucede es que no funciona el grub, y yo no estoy nada canchero en Linux. Podria aseverarse que en esto soy un principiante, aunque con  muchas ganas de aprender......para poder compartir la filosofia Linux, y Ubuntu en especial (Humanidad para los demas).

Gracias por su ayuda. espero poder retribuirla

---

### Post by angelqpro on 2007-10-13
Creo que el problema es el mismo por el cual no puedo instalarlo en el RAID principal, y es que Ubuntu no reconoce el array. Toma ambos discos de 320 en forma individual, y no como conjunto RAID 0.
La pregunta ahora es: ¿Como se hace para configurar RAID 0 en Ubuntu?.
Para instalar Windows, hay que utilizar un disquette con drivers RAID, si no quiero utilizar los de Win.
¿hay algo asi con Ubuntu?
Aclaro que en la BIOS esta declarado el RAID, y funciona normalmente en ambos entornos Windows, XP y Vista.
Gracias por su tiempo, amigos

---

### Post by angelqpro on 2007-10-15
Lamento decir que al no tener una solucion sencilla para un array RAID, Ubuntu aun esta verde para su implementacion masiva. No me queda mas remedio que permanecer en el entorno Moco$oft, muy a pesar mio. No puede ser que no haya una forma facil de implementar esto. No lo entiendo. Y este foro no me ha sido de ninguna ayuda. Gracias de todos modos a quienes contestaron
:mad::(

---

### Post by faktorqm on 2007-10-18
hola, perdoname, te hago una pregunta que no tiene nada ke ver con tema original. decis que usas sata 2 seagate 7200.10, si me haces el favor, te fijarias en la etiqueta que procedencia tienen? si son chinos, o de singapore? mil gracias. salu2!

---

### Post by Mataca on 2007-10-18
Esto te paso con la 7.04 ??? si es así, proba con el 7.10 que hay mucho mas soporte para SATA y raid.
No necesitas instalar ningun driver desde un diskette en teoria, te lo reconoce de una.

Yo solucione mi problema de lectora SATA cuando instale la nueva version del kernel. 

Mucho mas que eso no te puedo ayudar.

---

### Post by josedamico on 2007-10-18
UNa solución, a medias obvio, para poder arrancar ubuntu es botear con un disquete que tenga el SUPER DISK GRUB ( o super grub disk, no me acuerdo el orden). Es un soft que te crea una imagen de disquete y al botear desde alli, te permite con qué sistema operativo arrancar la maquina. No modifica el mbr salvo que se lo indiques y te permite tambien corregir el grub. Tiene muchas aplicaciones. Es bueno. Yo lo uso porque tuve problemas para la instalcion de grub en un disco IDE, la maquina tiene en un SATA master el winxp y en el IDE puse el ubuntu. Como no me dio bola con el grub le boteo con ese disquete. Me va bien. Espero que te sirva este truquito

---

### Post by clasificado on 2007-10-18
> Para instalar Windows, hay que utilizar un disquette con drivers RAID

A mi impresión, es como si el RAID que está armando tu equipo no sigue configuraciones estándar.

Por lo que, para hacer que funcione en windows, necesitas un driver que el FABRICANTE proporciona.

Yo creo que es el mismo fabricante el que debería proporcionarte un driver equivalente (o un modulo de kernel) para linux.

Clasificado

---

