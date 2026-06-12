---
title: "Instalacion Ubuntu junto con Win XP"
date: 2007-07-18
forum: Argentina Team
---

### Post by Pabliich on 2007-07-18
[COLOR="DarkRed"]**Hola a todos.. acabo de entrar en el mundo de linux y quiero instalar ubuntu en mi PC, yo tengo Windows XP y el disco es de 160gb. Me estube informando y tengo entendido que tengo qe particionar mi disco por que yo quiero instalar ubuntu junto con windows XP..Me dijieron que ponga 60 y 100. Pero el problema es el siguiente no se como se particiona oi de el partcion magic pero tengo miedo de que se me borre todo lo de Win XP... Antes quiero informarme bien.. espero que me puedan ayudar de como se hace todo.. muchas gracias!...**:)[/COLOR]

---

### Post by benjaminwr on 2007-07-18
Buenas,

Pues en realidad es una tarea muy sencilla, instalate el partitionmagick y reduce el tamaño de la particion actual de windows (te pedira que reinicies antes de aplicar los cambios porque no puede cambiar tamaño de particion con windows andando) hasta dejar como minimo 10gb libres al final del disco, si los dejas al comienzo puedes estropear la particion de XP al moverla.

Esto dejara un espacio sin particionar en tu disco que al arrancar la instalacion de ubuntu, el solo particionara lo que necesita para linux.

Un saludo
Espero haber sido de ayuda

---

### Post by Pabliich on 2007-07-18
**aaa.. entonces con el particion magic pongo la ultima parte del disco por ej. tengo 160gb pongo 40gb y no se me modifica nada del windows XP? es que tengo miedo de que se borren las cosas.. muchas gracias por responder!!.. **

---

### Post by Oktubre on 2007-07-18
Hacelo tranquilo que el PartitionMagic funciona bien. Igual deja el espacio libre y luego el Ubuntu - al instalrse - te crea las particiones necesarias.

Saludos

---

### Post by Pabliich on 2007-07-18
che disculpa que sea tan artante pero mira esto.. jeje :$ 
me podes decir si voy bien?..

[IMG]http://img387.imageshack.us/img387/9771/dibujoto1.jpg[/IMG]


perdon.. es que estoy loco por instalar ubuntu

---

### Post by spg76 on 2007-07-18
En realidad, deberías redimensionar la partición existente y usar ese espacio para instalar Ubuntu.
En la mayoría de los casos, esto lo puede hacer perfectamente el mismo instalador de Ubuntu.
En el instalador te aparece así:

[IMG]https://help.ubuntu.com/community/GraphicalInstall?action=AttachFile&do=get&target=6.png[/IMG]

Ahí elegis el tamaño de la partición que queres para Ubuntu y listo.
Espero que te sirva.
Saludos.

---

### Post by Thalskarth on 2007-07-18
> **Pabliich said:**
> che disculpa que sea tan artante pero mira esto.. jeje :$ 
me podes decir si voy bien?..

[IMG]http://img387.imageshack.us/img387/9771/dibujoto1.jpg[/IMG]


perdon.. es que estoy loco por instalar ubuntu
No... primero tenes que seleccionar la particion C:, luego clickear donde dice "redimensionar la particion" y ahi achicas la particion C: para que quede espacio vacio al final de todo...

fijate que dice algo como "espacio libre al final" y diria 0.. ahi le pones el espacio que queres liberar para luego use Ubuntu...entonces la capacidad de C: se va a achicar y va a quedar espacio libre... ejemplo... si le pones 100gigas como espacio libre al final, enontces... C: pasará a tener 60 gigas de capacidad todal en tu disco de 160

Suerte

---

### Post by Pabliich on 2007-07-18
**:O muchisimas gracias che.. voy a ver si puedoo.. jeje**

---

### Post by Pabliich on 2007-07-18
[B]disculpen si soy muy estupido. , muy artante.. es que quiero asegurarme de hacerlo bien..
estoy bien asi?[/B]

[IMG]http://img255.imageshack.us/img255/3765/dibujotg2.jpg[/IMG]

---

### Post by spg76 on 2007-07-18
> **Pabliich said:**
> [B]disculpen si soy muy estupido. , muy artante.. es que quiero asegurarme de hacerlo bien..
estoy bien asi?[/B]
No, ahi tenes que poner el nuevo tamaño de la partición que estás redimensionando.
Si tenes un disco de 160 GB, tenes que poner 100GB y te va a dejar un espacio de 60GB  que es el que tenes que usar para instalar Ubuntu.

---

### Post by Pabliich on 2007-07-18
entonses en el cuadrado marcado con rojo en la imagen pongo 100gb.. claroo recien entiendoo.. y va a sobrar 60 gb para el ubuntu.. jaja.. qe bruto soy.. **pero es seguro?no quiero que se me borre nada..**.. gracias por responder che

---

### Post by sebas.rhcp on 2007-07-18
Yo que vos haria backup de tus cosas

---

### Post by Thalskarth on 2007-07-18
> **Pabliich said:**
> entonses en el cuadrado marcado con rojo en la imagen pongo 100gb.. claroo recien entiendoo.. y va a sobrar 60 gb para el ubuntu.. jaja.. qe bruto soy.. **pero es seguro?no quiero que se me borre nada..**.. gracias por responder che
Si es justo como vos decis. Perdona que yo te lo dije al revez... cuando me fije tengo la version 8 yo y se ve que cambiaron ese cuadro :P

Con respecto a lo seguro... siempre es 99% seguro... yo con el PartitionMagic 7 lo hice unas 2 o 3 veces y nunca tuve dramas... con la version 8 lo he hecho miles de veces y nunca tuve problemas de ningun tipo... lo unico, antes de hacerlo... siempre es buen consego defragmentar esa particion antes...

PD:Yo soy usuario de ubuntu desde el domingo, asi que justo ese dia hice este mismo proceso con el PartitionMagic :P

---

### Post by valucha on 2007-07-18
[COLOR="DarkOrchid"]NO TE OLVIDES DE DESFRAGMENTAR ANTES EL DISCO!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!1
SINO PUEDE QUE SE TE PIERDAN COSAS.[/COLOR]

---

### Post by Pabliich on 2007-07-19
**wenasss de nuevoo... consegii el manual del ubuntuu y vi qe puedo particionar mi disco facilmente desde el live cd osea.. entro a administracion editor de particiones de Gnome.. pero cuando achico el disco C para que me sobre espacio para el ubuntu no se borra nada?... como es eso de defragmentar el disco?..**

---

### Post by Pabliich on 2007-07-19
HOLAAAA! muchisimaa graciass por todoo salioo todo perfectooo.. gracias... ahora lo que no se es como hacer para que me quede asi la pc [http://www.youtube.com/watch?v=xC5uEe5OzNQ](http://www.youtube.com/watch?v=xC5uEe5OzNQ) con todos esos efectos.. lei algo sobre beryl alguien me puede decir algo por favor.. gracias chauu..

---

### Post by marianom on 2007-07-19
Te recomiendo que pongas beryl en el buscador del este subforo y recorras un poco los posts que hay al respecto así te vas interiorizando en el tema. Después alguien que use Beryl con seguridad te va a poder asistir con las dudas puntuales que te surjan.

---

