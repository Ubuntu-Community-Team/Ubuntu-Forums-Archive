---
title: "Instalación en un segundo disco rígido"
date: 2007-11-02
forum: Argentina Team
---

### Post by aregnando on 2007-11-02
Hola a todos, bueno luego de probar los live cd de Ubuntu y de Kubuntu me he decidido a instalar este segundo.
La consulta que quería realizar es la siguiente:
En mi méquina tengo cargado el sistema operativo de las ventanas ya que a mi esposa e hija les resulta mas sencillo para utilizar pero en mi caso no quiero saber nada con estas ventanas del señor Bill, la idea es instalar un segundo disco rígido y dedicarselo por entero a Kubuntu.
La pregunta sería como hacer en el momento de la instalación para que Kubuntu se cargue en este disco y me deje intacto el que usan mi esposa e hija?
Desde ya muchas gracias.

---

### Post by Hernán-Amaya on 2007-11-02
en la instalación podes elegir donde y como lo queres instalar a kubuntu,
solo tenes que elegir el disco en donde no esta instalado el m$ winbug y listo, es sensillo. igual recomendación hacer backup

un enlace siempre copado es [www.guia-ubuntu.org](www.guia-ubuntu.org)

para la instalación fijate el slides que hizo felipe en la charla que dio en el cafeconf

[http://www.cafeconf.org/2007/modules/myconference/viewspeech.php?sid=62&cid=1](http://www.cafeconf.org/2007/modules/myconference/viewspeech.php?sid=62&cid=1)

suerte!
cualquier cosa chiflanos

---

### Post by aregnando on 2007-11-02
Muchas gracias Hernán, se que mi pregunta es muy básica pero realmente soy un novato total en este mundo de linux.
Luego les cuento como me fué con la instalación.
Saludos.

---

### Post by sajnox on 2007-11-02
> **aregnando said:**
> Muchas gracias Hernán, se que mi pregunta es muy básica pero realmente soy un novato total en este mundo de linux.
Luego les cuento como me fué con la instalación.
Saludos.

Dale para adelante y cualquier duda posteala que seguro tendras alguna respuesta

Saludos

---

### Post by pablo0469 on 2007-11-03
En un momento te va a aparecer el dialogo de donde queres instalar Kubuntu, usa la 2ª opcion "Guiado-Utilizar todo el Disco), donde abajo te tienen que aparecer los 2 DR que tenes en la PC.

Tilda el DR (hda1 o hda2, eso solo vos lo sabes) donde queres poner Kubuntu, y dale para Adelante.

No es dificil, pero cualquier duda, postea.

Saludos.

---

### Post by leonardo83 on 2007-11-04
yo te recomendaria para no tener inconvenientes sacar el rigido, instalar el nuevo cosa de que sepas que es el unico rigido que tenes que elegir, y despues si, lo sacas y conectas todo con los cables IDe como master, slave bla bla bla.
Pero sino hacelo como te dicen aca los muchachos.
Saludos! :)

---

### Post by vk-cdg on 2007-11-05
> **leonardo83 said:**
> yo te recomendaria para no tener inconvenientes sacar el rigido, instalar el nuevo cosa de que sepas que es el unico rigido que tenes que elegir, y despues si, lo sacas y conectas todo con los cables IDe como master, slave bla bla bla.
Pero sino hacelo como te dicen aca los muchachos.
Saludos! :)


El problema de hacer esto que recomendás vos, es que la instalación de *Ubuntu detecta que está "solito" en el sistema y no instala las opciones de arranque del grub. Después (al menos para nosotros los novatos) es mas complicado modificar el grub para agregar la opción de arranque de Win.

---

### Post by aregnando on 2007-11-06
> **pablo0469 said:**
> En un momento te va a aparecer el dialogo de donde queres instalar Kubuntu, usa la 2ª opcion "Guiado-Utilizar todo el Disco), donde abajo te tienen que aparecer los 2 DR que tenes en la PC.

Tilda el DR (hda1 o hda2, eso solo vos lo sabes) donde queres poner Kubuntu, y dale para Adelante.

No es dificil, pero cualquier duda, postea.

Saludos.

Pablo, gracias por tu respuesta al igual que a todos los que me han contestado, la duda que me surge es si al marcar esta opción de utilizar todo el disco no formateará el disco en el cual tengo cargado el otro OS?
¿Que pasa si le pongo instalar en el espacio restante disponible?
Lo que omití decir en algún momento es que ya traté de instalarlo en el disco que tengo actualmente, el mismo tiene 80 Gb. de los cuales tengo ocupados 56 Gb. y traté de hacerlo con la opción de utilizar el espacio restante disponible a lo cual obtuve la respuesta de que el espacio no era suficiente. ¿es esto posible???
Como verán tengo muchas dudas.
Gracias.

---

### Post by pablo0469 on 2007-11-07
Decime que tipo de discos tenes: IDE o SATA, y si son de diferente marca o espacio, esto puede ayudar mucho a identificar donde poner Kubuntu.

Te doy el ejemplo de mi PC: tengo 2 DR de 80 GB IDE, al esclavo le saque el jumper trasero, y son de diferente marca (Western Digital y Samsung), asi se que el primario va a ser siempre hda1, y elesclavo siempre hda2, y como el instalador de Ubuntu/Kubuntu me los identifica hasta por nombre y apellido, y se donde tengo metido el XP, jamas lo voy a borrar, me explico o te he mareado?

Si son SATA, creo que Primario (hda1) y Esclavo (hda2), los tenes que determinar en la BIOS.

Saludos y repito, espero no haberte mareado.

---

### Post by pablo0469 on 2007-11-07
Perdon, me comi la otra duda :).

Si, la instalacion en el DR que tenes ahora es posible, pero...

1) fijate muy bien que el boton de la barra te marque los 56 GB que tenes con el Windows, y para no anularlo y no poder seguir guardando cosas en el, desplaza ese boton a la derecha y asignale un par de gigas más (que te quede minimo 60 GB), y despues dale para adelante que Kubuntu se te va a instalar en los 15 GB reales que te quedan por detras (ojo que un disco de "80 GB" tiene una capacidad real de aprox. 75).

2) como tenes la particion Win bastante cargada y te queda poco espacio libre, en tu lugar esperaria a instalarle el 2º DR o limpiaria bastante la particion Win.

Algo mas respecto a los SATA: mi placa madre tiene identificado los 2 puertos como SATA 1 y 2, creo que asi se asignan directamente como Primario y Eslavo.

Saludos, y cualquier cosa, postea de nuevo.

---

### Post by angelqpro on 2007-11-10
> **pablo0469 said:**
> Decime que tipo de discos tenes: IDE o SATA, y si son de diferente marca o espacio, esto puede ayudar mucho a identificar donde poner Kubuntu.

Te doy el ejemplo de mi PC: tengo 2 DR de 80 GB IDE, al esclavo le saque el jumper trasero, y son de diferente marca (Western Digital y Samsung), asi se que el primario va a ser siempre hda1, y elesclavo siempre hda2, y como el instalador de Ubuntu/Kubuntu me los identifica hasta por nombre y apellido, y se donde tengo metido el XP, jamas lo voy a borrar, me explico o te he mareado?

Si son SATA, creo que Primario (hda1) y Esclavo (hda2), los tenes que determinar en la BIOS.

Saludos y repito, espero no haberte mareado.

Amigo. Con los discos SATA, ya no existe diferenciacion entre master y slave, ya que no comparten canal. Son todos master, con controladoras separadas. No tienen ya jumpers

---

