---
title: "AWN y Papelera (Trash), mal funcionamiento"
date: 2008-05-06
forum: Argentina Team
---

### Post by smrdelj on 2008-05-06
Buenas.

Como comenté en un thread, mi papelera anda mal en la barra awn. Lo que hice fue agregarla como applet desde el administrador de awn, y la verdad que no camina :S

Tiene varios inconvenientes:

-Primero, no cambia su icono cuando está llena. Es decir que, a la vista, siempre permanece vacia.

-Segundo, al darle click derecho "vaciar", no sucede nada. Es por esto que, para vaciarla, debo ingresar y allí concretar el borrado; lo que resulta muy impractico.

-Tercero y por ultimo, no me deja cambiar el ícono a discresion como si fuera un "acceso directo" cualquiera.

Un usuario me sugirió borrar la papelera de awn y directamente colocarla en la barra gnome; pero lo que yo busco es la solusion a tener en awn :S

Espero alguien sepa cómo lidiar con esto.

Muchas gracias. Saludos

---

### Post by fgl82 on 2008-05-06
A mí me pasa lo mismo con el applet de papelera en los 2 awn que soportan applets, es decir, el bzr y el trunk.

No encontré solución.

Me sumo al pedido de ayuda del amigo, ya que buscando soluciones yo arruiné más aún mi awn, al punto de que ahora es imposible que me muestre los separadores :S

---

### Post by Mauro22 on 2008-05-06
Estuve buscando sobre el tema y encontre esto:

Al parecer en hardy heron el directorio de Trash se cambio de:

/home/usuario/.Trash 

a

/home/usuario/.local/share/Trash.


Entonces segun esto:

```

           [FONT=monospace]I can confirm that Hardy is now using ~/.local/share/Trash as it's trash dir.
 Freedesktop Spec for Trash: [http://www.ramendik.ru/docs/trashspec.html](http://www.ramendik.ru/docs/trashspec.html)
 It should be: $XDG_DATA_HOME/Trash
 Work around: **You can manually set the directory used by Trasher in gConf. avant-window-****navigator/****applets/****Trasher/ trash_dirs**

```


Hay que ejecutar gconf-editor (alt+f2) y cambiar la ruta de Trash.





[/FONT]

---

### Post by _kAz_ on 2008-05-06
> **smrdelj said:**
> Buenas.

Como comenté en un thread, mi papelera anda mal en la barra awn. Lo que hice fue agregarla como applet desde el administrador de awn, y la verdad que no camina :S

Tiene varios inconvenientes:

-Primero, no cambia su icono cuando está llena. Es decir que, a la vista, siempre permanece vacia.

-Segundo, al darle click derecho "vaciar", no sucede nada. Es por esto que, para vaciarla, debo ingresar y allí concretar el borrado; lo que resulta muy impractico.

-Tercero y por ultimo, no me deja cambiar el ícono a discresion como si fuera un "acceso directo" cualquiera.

Un usuario me sugirió borrar la papelera de awn y directamente colocarla en la barra gnome; pero lo que yo busco es la solusion a tener en awn :S

Espero alguien sepa cómo lidiar con esto.

Muchas gracias. Saludos

Me sumo... Tengo el mismo problema que es mas bien una inconveniencia.

Respecto al icono lo podes cambiar manualmente si no tenes el default en /home/usario/.icons/places.

Aprovecho con su permiso para realizar una pregunta que versa también sobre AWN:

Desde anoche que NO funciona el applet del clima y no se por qué. Actualice un monton de veces y nada. Encima como no anda ni para atrás me empieza a ralentizar todo el sistema. La pregunta? QUE C*RAJ* PASA???

Me sale el logo de "The Weather Channel" todo el tiempo y me dice "Fetching weather data". El mapa se ve cuando quiero acceder, a veces aparece tambien el pronóstico, pero la informacion necesaria ni noticias.

---

### Post by Mauro22 on 2008-05-06
> **_kAz_ said:**
> 
Desde anoche que NO funciona el applet del clima y no se por qué. Actualice un monton de veces y nada. Encima como no anda ni para atrás me empieza a ralentizar todo el sistema. La pregunta? QUE C*RAJ* PASA???

Me sale el logo de "The Weather Channel" todo el tiempo y me dice "Fetching weather data". El mapa se ve cuando quiero acceder, a veces aparece tambien el pronóstico, pero la informacion necesaria ni noticias.


A mi se me colgo el screenlet (weather screenlet) se quedo en "no wheater information available"

Lo tengo configurado en Ezeiza, asi que si vos tambien. Es problema de ellos.

---

### Post by _kAz_ on 2008-05-06
> **Mauro22 said:**
> A mi se me colgo el screenlet (weather screenlet) se quedo en "no wheater information available"

Lo tengo configurado en Ezeiza, asi que si vos tambien. Es problema de ellos.

Me deja más tranquilo si es así. Ya estaba empezando a cambiar los iconos que había puesto la otra vez, en ese momento no me los reconocía porque tenía que ponerles "solo lectura", pero ahora taba todo bien. A esperar entonces... igual un bodrio no tener esa *****...

---

### Post by Mauro22 on 2008-05-06
Lo peor es que queda para el ****, porque lo ven los demas y te dicen, "para que lo tenes ahi, si no muestra nada?"


:lolflag:

---

### Post by _kAz_ on 2008-05-06
> **Mauro22 said:**
> Lo peor es que queda para el ****, porque lo ven los demas y te dicen, "para que lo tenes ahi, si no muestra nada?"


:lolflag:

JAJJAJAJAJA totalmente!!! Estaba pensando exactamente eso...

Yo que ando presumiendo por todos lados con mi Ubuntu tuneado, mis superefectos de compiz y mandando prints a todos los contactos para mostrar... ahora me pasa esto, no es justo :(

---

### Post by valucha on 2008-05-06
[COLOR="DarkOrchid"]Usen Conky (L) y dejen los screenlets y las **** de la avant de lado que encima de que quedan feas, son inestables y todo eso :)[/COLOR]

---

### Post by _kAz_ on 2008-05-06
> **valucha said:**
> [COLOR="DarkOrchid"]Usen Conky (L) y dejen los screenlets y las boludeces de la avant de lado que encima de que quedan feas, son inestables y todo eso :)[/COLOR]

Es que mi Conky es cualquier cosa... ni sé como configurarlo; no sé por donde empezar.

Ahhhh a VOS te quería preguntar justo eso. Estoy usando el Elegant Brit tanto en decoración como en iconos. Vi que tenías el Conky con ese tema justamente, como hiciste??? Lo quise bajar de aca [http://ubuntuusers.de/paste/58458/]("http://ubuntuusers.de/paste/58458/") pero ni idea que hay que hacer ni donde ponerlo. Presumo que tengo que crear un archivo .conkyrc, pero pa donde agarro? ;)

---

### Post by smrdelj on 2008-05-06
Sí, no hay problema, les regalo el thread para que charlen de lo que quieran...

Jajaja :P

Nah, fuera de ****, lo de la papelera no me calienta, ya la fleté pa' el gnome y listo, fuera de mi awn.

Saludos, el thread is yours!

---

### Post by _kAz_ on 2008-05-06
> **smrdelj said:**
> Sí, no hay problema, les regalo el thread para que charlen de lo que quieran...

Jajaja :P

Nah, fuera de joda, lo de la papelera no me calienta, ya la fleté pa' el gnome y listo, fuera de mi awn.

Saludos, el thread is yours!

Probaste la solución de Mauro????

---

### Post by spg76 on 2008-05-06
Como dice Mauro, el problema de la papelera es porque en Hardy cambio el directorio de Trash. Esto es porque cambiaron el sistema de archivos virtual de GNOME (antes era GVFS y ahora es GIO) lo cual complica bastante arreglar esta cuestión sin generar otro problema en versiones anteriores (Gutsy, Feisty, etc)
La solución que plantea Mauro me parece que solo funciona para el applet Stacks Trasher. Yo lo arreglé borrando el directorio .Trash y haciendo un enlace simbólico a ~/.local/share/Trash/files. Para hacer esto, pueden escribir en una terminal:
```
rmdir ~/.Trash
ln -s ~/.local/share/Trash/files ~/.Trash
```

Con respecto a lo del applet del clima, el problema surgió porque Weather Channel cambió algo y esto hizo que dejará de funcionar. Hoy publicaron un [fix]("http://bazaar.launchpad.net/~awn-extras/awn-extras/trunk/revision/477"), así que ni bien actualicen el repositorio (o si tienen la versión bzr) debería volver a funcionar.

---

### Post by _kAz_ on 2008-05-07
> **spg76 said:**
> Como dice Mauro, el problema de la papelera es porque en Hardy cambio el directorio de Trash. Esto es porque cambiaron el sistema de archivos virtual de GNOME (antes era GVFS y ahora es GIO) lo cual complica bastante arreglar esta cuestión sin generar otro problema en versiones anteriores (Gutsy, Feisty, etc)
La solución que plantea Mauro me parece que solo funciona para el applet Stacks Trasher. Yo lo arreglé borrando el directorio .Trash y haciendo un enlace simbólico a ~/.local/share/Trash/files. Para hacer esto, pueden escribir en una terminal:
```
rmdir ~/.Trash
ln -s ~/.local/share/Trash/files ~/.Trash
```

Con respecto a lo del applet del clima, el problema surgió porque Weather Channel cambió algo y esto hizo que dejará de funcionar. Hoy publicaron un [fix]("http://bazaar.launchpad.net/~awn-extras/awn-extras/trunk/revision/477"), así que ni bien actualicen el repositorio (o si tienen la versión bzr) debería volver a funcionar.

Lo de la papelera funcionó...

Lamentablemente lo del applet del clima no sólo que no funcó, sino que terminó siendo peor :?
Ahora ni siquiera aparece el icono del Weather Channel sino que hay en lugar de eso UNA LINEA BLANCA ](*,)
Para aclarar: tengo la version bzr y cambié el weather.py tanto del directorio usr/lib/awn/applet/weather y del /home/.config/awn/applet/weather.

Intenté volver a como estaba antes, pero la línea blanca sigue apareciendo...
Alguna sugerencia???

---

### Post by spg76 on 2008-05-07
> **_kAz_ said:**
> Lo de la papelera funcionó...

Lamentablemente lo del applet del clima no sólo que no funcó, sino que terminó siendo peor :?
Ahora ni siquiera aparece el icono del Weather Channel sino que hay en lugar de eso UNA LINEA BLANCA ](*,)
Para aclarar: tengo la version bzr y cambié el weather.py tanto del directorio usr/lib/awn/applet/weather y del /home/.config/awn/applet/weather.

Intenté volver a como estaba antes, pero la línea blanca sigue apareciendo...
Alguna sugerencia???

Para actualizar no tenes que modificar nada manualmente. Tenes que bajar la actualización del repositorio (cuando salga, la última versión versión que salió es la 473 y el arreglo está en la versión 477), o hacer "bzr update" si compilaste desde trunk.

---

### Post by phxnd on 2008-05-07
como hago entonces para agregar la papelera al awn? tengo gusty

que es lo uqe pongo el campo de "lugar" , por que facilmente podria ejecutar nautilus con esa direccion ( osea /home/usuario/.Trash ) pero no se me pone el icono de la papelera, sino el de el nautilus :S

---

### Post by _kAz_ on 2008-05-07
> **spg76 said:**
> Para actualizar no tenes que modificar nada manualmente. Tenes que bajar la actualización del repositorio (cuando salga, la última versión versión que salió es la 473 y el arreglo está en la versión 477), o hacer "bzr update" si compilaste desde trunk.

Ya lo modifiqué... y ahora no lo puedo deshacer #-o

Que recomiendan??? Se solucionará si reinstalo el paquete de applets bzr??? (Solucion mínima, me conformo con que vuelva a aparecer el logo de Weather Chanel)

Perdon por la ignoracia, pero que sería compilar "desde trunk".

---

### Post by _kAz_ on 2008-05-07
> **phxnd said:**
> como hago entonces para agregar la papelera al awn? tengo gusty

que es lo uqe pongo el campo de "lugar" , por que facilmente podria ejecutar nautilus con esa direccion ( osea /home/usuario/.Trash ) pero no se me pone el icono de la papelera, sino el de el nautilus :S

No... no pongas un Launcher, utilizá el applet (Trash).

---

### Post by spg76 on 2008-05-07
> **_kAz_ said:**
> Ya lo modifiqué... y ahora no lo puedo deshacer #-o

Que recomiendan??? Se solucionará si reinstalo el paquete de applets bzr??? (Solucion mínima, me conformo con que vuelva a aparecer el logo de Weather Chanel)

Podés probar reinstalando, que creo que debería solucionarlo.
Anda a Synaptic y busca el paquete "awn-core-applets-bzr", hace clic derecho y selecciona reinstalar.

> **_kAz_ said:**
> Perdon por la ignoracia, pero que sería compilar "desde trunk".

En líneas generales, el trunk vendría ser la versión de desarrollo. Cada cosa que se arregla o agrega va a ese versión. Cuando se cumplen ciertas metas (agregado de nuevas funciones, arreglo de bugs y de funcionalidades, etc.) sale una versión estable del programa. Con está versión, te aseguras tener siempre lo último de lo último, aunque también podés experimentar ciertos problemas. Yo lo compilo porque modiqué un poco el tamaño de la barra tocando el código fuente, algo que no puedo hacer si instalo los paquetes. Si queres más info sobre como compilar desde trunk podés ir a [http://wiki.awn-project.org/InstallingFromSource](http://wiki.awn-project.org/InstallingFromSource).
Lo más sencillo para no instalar un montón de dependencias es usar el repositorio que igual arman los paquetes desde trunk sin esperar versiones estables. En este momento, el repositorio tiene la misma versión de Awn que el trunk.

---

### Post by _kAz_ on 2008-05-08
Bueno, reinstale y al menos volvio el icono ese que no dice nada. Ahora a esperar a que solucionen el problema, ojalá sea rapido!!!

---

### Post by phxnd on 2008-05-08
> **_kAz_ said:**
> No... no pongas un Launcher, utilizá el applet (Trash).

pero como lo agrego? tengo que bajar el applet de internet? por que si es asi no lo encuentro =S

---

### Post by _kAz_ on 2008-05-08
> **phxnd said:**
> pero como lo agrego? tengo que bajar el applet de internet? por que si es asi no lo encuentro =S

Andá a Origenes del Software>Software de terceros>Añadir y agregas:

```
deb http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
```

Después a terminal:

```
sudo apt-get update
sudo apt-get install awn-core-applets-bzr
```

Ojo que posiblemente se te instalen los applets y se te desaparezca el awn-manager. No desespereis. Andá a synaptic e instala el awn manager versión bzr como los applets.

---

### Post by phxnd on 2008-05-09
> **_kAz_ said:**
> Andá a Origenes del Software>Software de terceros>Añadir y agregas:

```
deb http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
```

Después a terminal:

```
sudo apt-get update
sudo apt-get install awn-core-applets-bzr
```

Ojo que posiblemente se te instalen los applets y se te desaparezca el awn-manager. No desespereis. Andá a synaptic e instala el awn manager versión bzr como los applets.

y por que es bzr? que diferencia tiene?

yo tengo la awn comun :P, no ta el applet para esta?

---

### Post by spg76 on 2008-05-09
> **phxnd said:**
> y por que es bzr? que diferencia tiene?

Son diferentes versiones. La que instalas desde el repositorio de Hardy es la última versión estable, y la versión bzr está armada con los útlimos cambios en el desarrollo del programa.

> **phxnd said:**
> yo tengo la awn comun :P, no ta el applet para esta?

No, en los repositorios de Hardy no existe el paquete con los applets.
Tenés dos formas de instalarlos: compilarlo desde el código fuente o hacer lo que te recomienda _kAz_.

---

### Post by phxnd on 2008-05-09
> **spg76 said:**
> Son diferentes versiones. La que instalas desde el repositorio de Hardy es la última versión estable, y la versión bzr está armada con los útlimos cambios en el desarrollo del programa.



No, en los repositorios de Hardy no existe el paquete con los applets.
Tenés dos formas de instalarlos: compilarlo desde el código fuente o hacer lo que te recomienda _kAz_.

joyaa gracais loco,,,, igual tengo gusty todavia,,, xD,,, no creo que me corra bien hardy,,, tengo una amd 2.2+ con 384 de ram xD

---

### Post by llove on 2008-05-10
hola con respecto al link de weather, en vez de agregar *&link=xoap* intenten borrando de ese mismo url *&prod=xoap* nose con el applet de awn, pero con el screenlet se soluciono. espero les sirva. saludos

---

### Post by spg76 on 2008-05-10
> **llove said:**
> hola con respecto al link de weather, en vez de agregar *&link=xoap* intenten borrando de ese mismo url *&prod=xoap* nose con el applet de awn, pero con el screenlet se soluciono. espero les sirva. saludos

El applet del clima ya se arregló en la última actualización de Awn extras.
Igual muchas gracias por la sugerencias.

---

