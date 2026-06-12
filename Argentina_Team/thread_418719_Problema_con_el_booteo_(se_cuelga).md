---
title: "Problema con el booteo (se cuelga)"
date: 2007-04-22
forum: Argentina Team
---

### Post by LJM on 2007-04-22
¡Hola! Vengo con un problema desde hace como dos meses, pero por más que ya intenté varias cosas, sigo sin poder solucionarlo.

Resulta que básicamente cada vez que prendo la máquina se cuelga en diferentes fases del proceso de booteo, o sea antes de que empiece a cargar Ubuntu.

Sólo logro que cargue Ubuntu y empezar a utliizar la máquina normalmente luego de varios (hasta seis o siete) reseteos (lo cual sospecho tarde o temprano me va a hacer pelota la máquina).

El primer punto en el que se suele colgar es cuando muestra

>Verifying DMI Pool Data...

Si sortea este obstáculo, entonces se suele colgar con

>GRUB loading, please wait... X [segundos]  (X puede ser 2, 1 o 0)

A veces me pone 

>CMOS checksum error -- Defaults loaded
>Warning! CPU has been changed.
>Please Enter CPU Speed CMOS Setup and Remember to Save before Exit!

aunque el BIOS no lo toqué, o a lo sumo lo volví a poner en default (¡cuando no se me cuelga dentro del BIOS mismo!)

Otras veces carga el GRUB como pantalla de comando nomás y de ahí booteo de vuelta porque no sé qué más hacer.

Hace unos días, mientras chequeaba el disco luego de 30 veces de ser montado, me puso que dos "nodos i" estaban múltiplemente compartidos. Esto lo arreglé pasándole fsck en la terminal en modo seguro.  Pero igual el problema original sigue como siempre.

¿Alguien tiene idea dónde puede estar el problema y qué puedo probar hacer para ver si lo soluciono? 

Desde ya, muchas gracias.

---

### Post by felipelerena on 2007-04-22
Ese problema es de la bios, no tienen nada que ver con Ubuntu

---

### Post by jayflower on 2007-04-22
> **felipelerena said:**
> Ese problema es de la bios, no tienen nada que ver con UbuntuCambiale la pila. Otra es resetear la bios desde el jumper que esta en el mother

---

### Post by LJM on 2007-04-22
Agrego un dato más sobre el problema porque tal vez sea relevante.

Una vez que la máquina carga Ubuntu y todo empieza a funcionar normalmente, si ahí reinicio la compu nunca falla el booteo. Pero cuando la prendo al otro día, se vuelve a colgar.

¿Esto es un signo de algo?

¡Gracias!

---

### Post by beuno on 2007-04-23
> **LJM said:**
> Agrego un dato más sobre el problema porque tal vez sea relevante.

Una vez que la máquina carga Ubuntu y todo empieza a funcionar normalmente, si ahí reinicio la compu nunca falla el booteo. Pero cuando la prendo al otro día, se vuelve a colgar.

¿Esto es un signo de algo?

¡Gracias!

Definitivamente es la pila.
La pila sirve para guardar la informacion cuando la PC no tiene electricidad, osea, cuando la apagas.

---

### Post by sebas.rhcp on 2007-04-23
¿No corre riesgo de que la rom se ***** asi? ¿O me equivoco?

---

### Post by jayflower on 2007-04-23
No, la informacíon de la configuración se mantiene guardada gracias a la pila (discos que hay instalados, tipo de procesador, que unidad de disco arraca, etc), por eso es posible que no arranque...Se le borro esa info y no sabe ni quien es esa PC. :)

---

### Post by sebas.rhcp on 2007-04-23
Entendido :)

PD: Perdon por el vocabulario utilizado, no me di cuenta.

---

### Post by LJM on 2007-04-26
Hoy le cambié la pila. Todavía no me animo a decir si el problema se arregló o no, pero al menos cuando la prendí luego del cambio se siguió colgando un par de veces como siempre. (La configuración del BIOS y CMOS no parecen haberse perdido.)

¿Se supone que tengo que hacer algo más luego de cambiarle la pila?

Por ahora voy a probar unos días a ver cómo se sigue comportando.

---

### Post by jayflower on 2007-04-26
tendrías que configurar correctamente la bios y guardar los cambios, luego ver que pasa

---

### Post by sebas.rhcp on 2007-04-27
Hacele un MemTest

---

### Post by LJM on 2007-04-28
Lamentablemente, luego del cambio de pila, la compu sigue con el mismo problema. O sea, se sigue colgando cuando la prendo. 

Alguien (no sé si acá o en otro lado)  mencionó algo sobre un "jumper". ¿Qué es eso? ¿Está adentro de la compu? ¿Puede ser que tocar eso sea lo que me falta hacer?

---

### Post by LJM on 2007-04-28
¿Te referís al comando fsck?

---

### Post by jayflower on 2007-04-28
Yo hablé de un Jumper, pero primero seria interesante que describieras bien que problemas ves o como es la secuencia de errores. Algo está pasando que el bootloader de la bios no sabe como arrancar ni de donde. 
La seguimos en otro lado porque este problema es de hardware y me parece que este no es el lugar. pm pliz

---

