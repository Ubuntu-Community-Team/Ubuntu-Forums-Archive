---
title: "Mover linux a otra pc"
date: 2006-12-23
forum: Argentina Team
---

### Post by quaid on 2006-12-23
La cosa es asi:

Con edgy siempre q hago una instalacion nueva en esta pc tengo quilombos. Mas q todo con el sonido.

El amrtes tengo la oportunidad de hacer el cambiazo de un disco rigido neuvo a mi pc.
La verdad no tengo ganas d einstalr todo de 0 proque tengo q instalar mil cosas , mas updates y etc.

Mi pregunta es esta:
Existe manera de mover linux ? osea copiar tal cual esta ahora y meterlo en otro disco (misma pc).
O alguna manera de q haga un registro de todo lo q hay asi el nuevo lo baja e instala. 

Q recomiendan 64  o 32bits? si tengo q instalarlo de 0 de nuevo digo

---

### Post by elgatogordo on 2006-12-23
> **quaid said:**
> 
Q recomiendan 64  o 32bits? si tengo q instalarlo de 0 de nuevo digo
[COLOR="Red"]no soy un experto asi que tomá con pinzas esto que te voy a decir.[/COLOR] por lo que lei en algunos foros (www,ubuntu-es.org) te conviene  32 bits porque hay cosas que en la de 64 no andan, por ejemplo automatix y el plugin flash. de todas maneras todo es prueba y error

---

### Post by DuckMan on 2006-12-23
creo q pasando tu carpeta /home/USUARIO guardarias la configuracion de TODO, pero tendrias q instalar los paquetes... porq no los guarda asi

desconosco otra manera por ahora :S

---

### Post by tzulberti on 2006-12-23
> **elgatogordo said:**
> [COLOR="Red"]no soy un experto asi que tomá con pinzas esto que te voy a decir.[/COLOR] por lo que lei en algunos foros (www,ubuntu-es.org) te conviene  32 bits porque hay cosas que en la de 64 no andan, por ejemplo automatix y el plugin flash. de todas maneras todo es prueba y error

La respuesta es que si y no: Hay programas que son mas dificiles que hacerlos andar: w32codecs, flash, acrobat reader, wine (basicamente todos los propietarios). Sin embargo, es facil instalarlos dentro de un chroot... Dentro de este foro, habia un post con un script para hacer eso:
[http://ubuntuforums.org/showthread.php?p=904320#post904320](http://ubuntuforums.org/showthread.php?p=904320#post904320)

Lo que se tiene que hacer con esos programas, es instalarlos dentro de un chroot... No es para nada complicado...

Si queres una recomendacion: el de 64...

---

### Post by beuno on 2006-12-23
Te diria usar la version 32 bit para mantener todo bien compatible.
Por otro lado, sacas el disco duro tal cual como esta, y lo colocas en la PC nueva y sale andando.
Linux, al contrario que Windows, reconoce todo el hardware de vuelta cada vez que arranca.
Lo unico que quizas tengas problema es la placa de video, cosa que solucionas ejecutando:
```
sudo dpkg-reconfigure xorg-xserver
```
Le he hecho muchas veces.

suerte!

---

### Post by jpmorelli on 2006-12-23
COmo dijeron antes, con guardar tu home estaría todo configurado y en cuanto a los paquetes, si tenes la posibilidad de grabar o copiar desde tu disco rigido anterior copia todo lo que esta en la carpeta  /var/cache/apt/archives al disco nuevo ( una vez que ya instalaste edgy obvio ) en el mismo destino, y recien ahi haces sudo apt-get update
La maquina te va a decir algo tipo:

Hay 45 paquetes para descargar, necesito descargar 0/81000Kb para actualizar, entonces va rapidísimo !!! y te evitas el bajar de internet.
Pequeños trucos que hacia cuando no tenía banda ancha y en el laburo bajaba todas las actualizaciones y traía a mi casa en un regrabable.

---

### Post by quaid on 2006-12-23
Bueno el miercoles o martesa hago eso y listo, y si me parece q me quedo con el de 32bits x ahora despues vere q hago

---

### Post by Benji86 on 2006-12-24
Automatix funciona en 64 bits.
Ademas, en los sub-foros **Faqs,Howto...** y en **64 bits** tenes guias para hacer funcionar aplicaciones de 32 bits.
En mi caso el unico problema fue el plugin de flash, que lo habia sacado andando y ahora se murio (no hay version de 64 bits)

---

### Post by quaid on 2006-12-29
Al final me quede con el de 32 , instale de 0 y listo.
El de 64 me trajo mil problemas, repositorios q no se xq no andaban, el driver nvidia andaba perfecto apenas lo instalaba y reiniciaba gdm, reseteaba la pc y chau X .

Supongo q algun dia lo instalare bien con mas tiempo ahora queria cambiar el disco.

---

