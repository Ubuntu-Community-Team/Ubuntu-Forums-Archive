---
title: "[SOLVED] El gestor de actualizaciones no funciona"
date: 2008-02-10
forum: Argentina Team
---

### Post by eduf on 2008-02-10
Buenas, busqué si había algún problema similar pero no lo encontré, al tratar de utilizar el gestor de actualizaciones me tira el siguiente fallo:
[B]No se ha podido inicializar la información de los paquetes

Ha ocurrido un problema imposible de corregir cuando se inicializaba la información de los paquetes.

Por favor, informe de ésto como un fallo en el paquete «update-manager» e incluya el siguiente mensaje de error:

'E:No se pudo tratar el archivo de paquetes /var/lib/apt/lists/ar.archive.ubuntu.com_ubuntu_dists_gutsy_universe_binary-i386_Packages (1), E:No se pudieron analizar o abrir las listas de paquetes o el archivo de estado.'[/B]
Desde ya agradecería una solución, ya que soy nuevo en linux ubuntu

---

### Post by faktorqm on 2008-02-11
ehhh todo apunta a que no tenes permisos de admin (eso es re de windows..., perdon, permisos de root) como lo estas ejecutando? no tenes ya un gestor de paquetes corriendo cuando haces eso? capaz lo tenes y no lo sabes, fijate. salu2!

---

### Post by eduf on 2008-02-11
faktorqm bueno ante todo gracias por responder, pero no creo que sea lo que me decis, dado que el problema lo tengo apenas prendo la pc, o sea no creo que tenga un gestor de actualizaciones corriendo, y lo ejecuto de la siguiente forma: sistema-->administración-->gestor de acctualizaciones. Si sabés de otra cosa que pueda estar pasando te agradeceria que me comentes, u otra persona se lo agradeceré mucho

---

### Post by Mauro22 on 2008-02-11
Hola, 

encontre esto en el foro de Debian. Supuestamente lo solucionó


> Hola a todos.

Me encuentro con el siguiente problema el cual es.

Cuando abro synaptic me aparece el siguiente error.
************************************************
E: No se pudo tratar el archivo de paquetes /var/lib/dpkg/status (1)
E: Las listas de paquetes o el archivo de estado no se pueden analizar sintácticamente o abrir.

*************************************************

**E: No se ha podido bloquear el directorio de listas**
** Este solo lo dice cuando le doy "recargar" a synaptic.


¿Entonces que puede estar pasando?. Nunca le eh movido el "source.list" todas las direcciones de repositorios las agrego desde synaptic. Pero ahora ya me quede sin paquetes que descargar que tanto me hacen falta.



////////////////////////////////////////////////////////

cd /por/si/te/pasa/lo/mismo

El problema estaba en el archivo "status" el que marca ahi. Lo solucione removiendo todo su contenido y guardando. despues me fui a la "consola" le di "sudo aptitude update" y listo.


Lo unico que en vez de  /var/lib/dpkg/status, en tu caso seria [B]/var/lib/apt/lists/ar.archive.ubuntu.com_ubuntu_di  sts_gutsy_universe_binary-i386_Packages



[/B]

---

### Post by faktorqm on 2008-02-11
Si no te funciona lo que posteó Mauro22, mira lo que recomende en este post, se que es mas para "ver" que para "solucionar", pero capaz nos da alguna luz sobre el problema.

[http://ubuntuforums.org/showthread.php?t=692183](http://ubuntuforums.org/showthread.php?t=692183)

salu2!

---

### Post by eduf on 2008-02-12
Bueno, ante todo muchas gracias a Mauro22 y faktorqm, les comento que pude solucionar el problema, les digo como, primero ingresé como usuario root en modo gráfico, acá les dejo el link "http://www.guia-ubuntu.org/index.php?title=Iniciar_la_Sesi%C3%B3n_como_Usuario_root"
luego, en vez de borrar el contenido del archivo en cuestión, tuve que eliminarlo y por último fui a la "consola" le di "sudo aptitude update" y listo.
Nuevamente gracias por preocuparse por mi tema, dado que soy nuevo en esto de linux.

:):):):)

---

### Post by Mauro22 on 2008-02-13
Para marcar como solved:


Justo arriba del primer post (el tuyo) del lado derecho hay tres links:

         
     
             [Thread Tools]("http://ubuntuforums.org/showthread.php?t=691489&nojs=1#goto_threadtools")          [IMG]http://ubuntuforums.org/images/uf/misc/menu_open.gif[/IMG]                                [Search this Thread]("http://ubuntuforums.org/showthread.php?t=691489&nojs=1#goto_threadsearch")              [IMG]http://ubuntuforums.org/images/uf/misc/menu_open.gif[/IMG]                                      [Display Modes]("http://ubuntuforums.org/showthread.php?t=691489&nojs=1#goto_displaymodes")          [IMG]http://ubuntuforums.org/images/uf/misc/menu_open.gif[/IMG]

Haces clic en el primero, Thread Tools y luego en Mark As Solved!

:guitar:

---

### Post by eduf on 2008-02-13
Mauro22, muchas gracias ya que no sabia que tenia que marcarlo como solved

---

