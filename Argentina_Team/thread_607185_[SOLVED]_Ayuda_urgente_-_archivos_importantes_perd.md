---
title: "[SOLVED] Ayuda urgente - archivos importantes perdidos"
date: 2007-11-08
forum: Argentina Team
---

### Post by lopulus on 2007-11-08
Hola Gente: Como veran en el titulo estoy un poco desesperado. Perdi un monton de informacion, Fotografias familiares y mucho mas. 
El tema es el siguiente: 
Tenia/tengo un disco de 80 G que era de mi epoca en windows y contenia la info que antes detalle. El tema es que me mande una ****** terrible con el gparted pensando que me iba a poder ayudar a utilizar espacio libre en dicho disco. La ****** me la mande cuando pedi que trabajara con "crear tabla de particiones. "
Cuando me doy cuenta de la macana, abro windows y me habia desaparecido el disco....!!!!!
si estos datos sirven para que me ayuden, mejor si no veo que mas puedo aportar.

Ayudenme por favor!!!!!

---

### Post by margori on 2007-11-08
Como ya muchas veces se ha dicho en toda instalación de cualquier sistema operativo "antes de instalar, realize una copia de seguridad de todos sus datos". Algunas otros lugares dicen "No hay garantias de exito".

Me paso algo parecido alguna vez, pero con información mucho menos importantes. Lo que hice es poner la información de la tabla de partición tal cual la tenia en un principio. Sin formatear, intente ver la información y me funciono.

Lo otro es acceder al disco directamente a sus cilindros, pistas, sectores y caras, pero la verdad seria como buscar una aguja en un pajar. Se puede hacer perfectamente ya que no has roto realmente el disco, la información esta. Un profesional lo puede realizar, pero te puede salir un poco salado.

---

### Post by Mauro22 on 2007-11-08
No entiendo, al iniciar el disco desapareció?? No esta en Mi PC??


Eso significa tres cosas (que pueden ocurrir)

*No esta instalado correctamente
*No esta jumpeado correctament
*No tiene formato (o formato no compatible con M$)


* Si tocaste la tabla de particion, la info esta. 
Hay que conectarlo (jumpearlo) como esclavo, y sacar la info usando Ubuntu (que "ve" todo tipo de particion)

---

### Post by lopulus on 2007-11-08
> **Mauro22 said:**
> 
* Si tocaste la tabla de particion, la info esta. 
Hay que conectarlo (jumpearlo) como esclavo, y sacar la info usando Ubuntu (que "ve" todo tipo de particion)

Como hago para ver la info desde ubuntu, supuestamente ese dico era esclavo desde un principio...

y gracias por la rapida respuesta..

Una ultima pregunta...    Que significa "first beans... " y todas esas cosas que aparecen debajo de los alis de cada uno?


Gracias

---

### Post by lopulus on 2007-11-08
> **margori said:**
> Como ya muchas veces se ha dicho en toda instalación de cualquier sistema operativo "antes de instalar, realize una copia de seguridad de todos sus datos". Algunas otros lugares dicen "No hay garantias de exito".. 

Es que no pensaba que me iba a traer demasiados problemas.... :(
> **margori said:**
> Me paso algo parecido alguna vez, pero con información mucho menos importantes. Lo que hice es poner la información de la tabla de partición tal cual la tenia en un principio. Sin formatear, intente ver la información y me funciono.

como hago para ver la info de la tabla de particion?   :confused: Obviamente no lo formatie

gracias che!!! :lolflag:

---

### Post by juanman on 2007-11-08
Hay algunas herramientas (software) para recuperar particiones... Una es [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk"), q es soft libre, funciona en varias plataformas, tiene manuales en español...

PD: No me hago responsable por los daños q pueda causar el uso de este soft :D

---

### Post by User21 on 2007-11-09
> **lopulus said:**
> 
Una ultima pregunta...    Que significa "first beans... " y todas esas cosas que aparecen debajo de los alis de cada uno? 

   ** What's the deal with coffee cups/beans and the funny titles?** 
    Beans are posts. The post/bean count can be turned off by the user if so desired. 
 There tends to be a close connection between geeks and coffee, so that's where the theme came from. Yes, we know not everyone likes coffee, but it's just a silly thing. 
The images, their colors, and the changing icons don't have any special meaning. They simply change as time goes by. You will see (among other things) green coffee beans, roasted (brown) coffee beans, various sorts of coffee cups and mugs and so on. Like the titles, nothing specific is implied by the presence of specific images or titles (in almost all cases that is...staff, admins and banned users are some of the exceptions). These items are for fun, and are not serious. They are not a rank of any kind. They don't tell anyone how long you've been here nor how many posts you've made. The sayings and the images are a semi-random feature we have to provide a little kick. There is some structure to it, but only on the implementation side. We did this on purpose - because it was fun and whimsical. 
There isn't a list of what you get, and when, because that's not the point. The reason for the secrecy was/is this: while we want to reward people who participate in these forums with titles and changing symbols we really don't want them to become some sort of gauge that people use to determine whether someone is speaking with more/less authority on a support topic. Other forums use the title/icon system that way and more power to them. However, there are people here with less than 20 posts who can code circles around much of the staff and are capable of giving amazing and useful responses to support questions...and there are some of us here with thousands of posts who might get lucky with a good and helpful reply on occasion. The fear is that people might use post count and titles/symbols as a means of judging the validity of a post's content rather than the content itself. We had a long discussion about this in the forums when they were first started and this subject has been revisited among the staff several times. Some forum members and staff wanted to eliminate the post count and title/icon system completely, some have gone the other way wanting a complete ranking system that is clear and gives honorific titles with great meaning to those with higher post counts (that particular group is in the extreme minority). The current system is a compromise that has been working pretty well for a while. With the compromise of meaningless titles/icons, post count can be hidden in UserCP. Anyway, this is why we don't publish how many posts are necessary for a change in title/icon...it's just a silly reward. The post numbers needed for title changes is something that is easy to modify so it gets modified on occasion, when the admins don't have better things occupying their time, merely to maintain the surprise factor. Bottom line: it just a trivial, whimsically amusing little thing. Don't read too much into it...it really isn't worth the slightest emotional involvement. 

CADA "BEAN" es un post. Cuantos mas Beans tengas, es por que has hecho demasiados posts, tanto respondiendo como preguntando. Con esa cantidad, se hace una especie de ranking divertido, como lo explica arriba. No tiene nada que ver con experiencia ni jerarquias. Podes poner 10000 posts, y los mismos solo dicen pavadas. Como hago yo! :D 

Extraido de [Forum FeedBack and Help]("http://ubuntuforums.org/announcement.php?f=48")


No se entiende ?  Bue,  estoy fiaca pa traducirlo!

---

### Post by sharkg on 2007-11-09
ami me paso algo parecido hace un tiempo.. pero use el programa filerecover, es una aplicaciones de M$, deberias llevar tu disco a otra compu y lo pasas, hay una opcion q dice recuperar despues de un formaro, para q lea la info y recupera casi todo, no te digo todo porq si mal no recuerdo no me encontro unas cosas, pero si casi el 90% o + .
bueno espero q te sirva el dato.

---

### Post by lopulus on 2007-11-11
Gente querida: Quiero agradecerles su gran aporte. Mi problemas esta solucionado gracias a un lindo programa, que lo recomiendo, que se llama "R-studio". yo lo hice correr bajo Wniduos xp, y es rapido y sencillo. 

agradezco infinitamente!

:popcorn::):lolflag::mrgreen::-({|==D>:lol::-)

---

