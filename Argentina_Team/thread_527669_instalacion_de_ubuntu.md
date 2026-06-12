---
title: "instalacion de ubuntu"
date: 2007-08-16
forum: Argentina Team
---

### Post by edd12river on 2007-08-16
miren, se q a algunos poray les moleste mi pregunta, pero ahi va:
intente unstalar, pero en la parte de particionar no supe q opcion elegir, puse la primera q es como q reparticionaba, pero nose bien q onda, mi disco es de 30gb y decia particion nueva: 22.4gb (82%), puse esa, y me creo un disco q decia sistema de archivos, pero no de los 7gg masomenos q tendria q ser, sino de 724,b y no me dejaba instalar el ubuntu...q tengo q hacer? trate con las otras opciones pero nada, yo tengo una sola particion en el disco q son los 30gb!


desde ya muchas gracias..... Ëdd...

---

### Post by sajnox on 2007-08-16
Edd,

Creo que la opcion que te dio Ubuntu es tomar todo el espacio que quedaba libre en tu disco, pero la verdad que no es muy claro lo que nos explicas.

Aca te dejo un link con un manual de instalacion para Ubuntu (es muy claro)

[http://linux-es-libre.org/moodle/mod/resource/view.php?id=125](http://linux-es-libre.org/moodle/mod/resource/view.php?id=125)

Otra pregunta, vos tenes instalado Windows o alguna otra cosa en tu disco ?? hiciste algun backup de tus datos antes de la instalacion ?? 
No sea suicida mi amigo, haga backup....

Si no te sirve el manual que te pase trata de tirarnos un poco mas de data de lo que estas haciendo.

Saludos y conta como fue

---

### Post by edd12river on 2007-08-16
> **sajnox said:**
> Edd,

Creo que la opcion que te dio Ubuntu es tomar todo el espacio que quedaba libre en tu disco, pero la verdad que no es muy claro lo que nos explicas.

Aca te dejo un link con un manual de instalacion para Ubuntu (es muy claro)

[http://linux-es-libre.org/moodle/mod/resource/view.php?id=125](http://linux-es-libre.org/moodle/mod/resource/view.php?id=125)

Otra pregunta, vos tenes instalado Windows o alguna otra cosa en tu disco ?? hiciste algun backup de tus datos antes de la instalacion ?? 
No sea suicida mi amigo, haga backup....

Si no te sirve el manual que te pase trata de tirarnos un poco mas de data de lo que estas haciendo.

Saludos y conta como fue


si tengo xp...me fijo y trato...encima me creo 2 particiones, una era el 2% del disco y el otro decia %..sisi esta bien lo q escribi, el signo % solo.... depues cuento q onda...

---

### Post by facundocorradini on 2007-08-17
> miren, se q a algunos poray les moleste mi pregunta, pero ahi va:

Por supuesto que tu pregunta no molesta, la comunidad está para ayudarse entre sí.

>  encima me creo 2 particiones, una era el 2% del disco y el otro decia %..sisi esta bien lo q escribi, el signo %

Eso es porque el sistema necesita dos particiones para funcionar: una es el sistema de archivos en sí, la otra es la swap (al que funciona "parecido" a la memoria virtual del windows), pero que tiene la gran ventaja de esta en un lugar fijo.


Para poder instalar ubuntu, deberías elegir "cambiar el tamaño de la particion y utilizar el espacio libre" (o algo por el estilo). Te va a aparecer una barra, desplazala y estarás achicando el tamaño a windows y dandole espacio a ubuntu.

Te recomiendo que minimo MINIMO le dejes 6 o 7 GB...

Un saludo

---

### Post by edd12river on 2007-08-17
> **facundocorradini said:**
> Por supuesto que tu pregunta no molesta, la comunidad está para ayudarse entre sí.



Eso es porque el sistema necesita dos particiones para funcionar: una es el sistema de archivos en sí, la otra es la swap (al que funciona "parecido" a la memoria virtual del windows), pero que tiene la gran ventaja de esta en un lugar fijo.


Para poder instalar ubuntu, deberías elegir "cambiar el tamaño de la particion y utilizar el espacio libre" (o algo por el estilo). Te va a aparecer una barra, desplazala y estarás achicando el tamaño a windows y dandole espacio a ubuntu.

Te recomiendo que minimo MINIMO le dejes 6 o 7 GB...

Un saludo


grax, voy a tratar, si tengo libres 10gb para linux...ahor atrato y les cuento como me fue...grax! :)

---

### Post by ecodina22 on 2007-08-28
[CENTER][B]Necesitarian que me respondan una preguta:

necesito saber donde encontrar documentacion actualizada de la instalacion de UBUNTU. yo deseo poder tener ambos sistemas (win y UBUNTU) y antes de meter la pata necesito la bibliografia adecuada.
Alguien me puede ayudar?
:confused::confused::confused::confused::confused: [/B][/CENTER]

---

### Post by facundocorradini on 2007-08-28
> **ecodina22 said:**
> [CENTER][B]Necesitarian que me respondan una preguta:

necesito saber donde encontrar documentacion actualizada de la instalacion de UBUNTU. yo deseo poder tener ambos sistemas (win y UBUNTU) y antes de meter la pata necesito la bibliografia adecuada.
Alguien me puede ayudar?
:confused::confused::confused::confused::confused: [/B][/CENTER]

Pues hay montones de guías, por ejemplo: [http://www.guia-ubuntu.org/index.php?title=Instalaci%C3%B3n_est%C3%A1ndar](http://www.guia-ubuntu.org/index.php?title=Instalaci%C3%B3n_est%C3%A1ndar)

resumiendo, bootea desde el liveCD, inicia ubuntu, haz clic en install, sigue los siete pasos y listo!

La única consideración especial que debes hacer es cuando te pregunta como particionar el disco, elegir "usar el espacio libre ...", allí aparecerá una barra de desplazamiento mediante la cual podrás elegir cuanto espacio dejar a win y cuando a ubuntu.
Además, es aconsejable desfragmentar el disco y hacer un scandisk desde windows antes de comenzar a instalar ubuntu. 

Luego de la instalación, cuando arranque la maquina te aparecerá un menú para elegir a que sistema operativo ingresar.

---

