---
title: "Algunas preguntas/problemas"
date: 2008-04-22
forum: Argentina Team
---

### Post by madelaki on 2008-04-22
Antes que nada, por favor entiendan que instale ubuntu esta semana, sin saber nada de Linux y ya busque en Ayuda y Soporte.

1) Cuando selecciono "Vista 3D de Ajedrez" en el ajedrez de Ubuntu, me tira este error. 

[http://img257.imageshack.us/img257/9477/pantallazo12vh1.png](http://img257.imageshack.us/img257/9477/pantallazo12vh1.png)

Me doy cuenta de que el problema con OGL es serio, pero no tengo idea de como solucionarlo. 

2) Alguien me puede vincular a una guia o explicarme bien como llegar al setup de archivos .bz2, .tar.bz2, .tar.gz y .run? Lo que hay en Ayuda y Soporte no me sirvio, porque tiene en cuenta conocimiento previo que yo no tengo. Por ejemplo, abro la terminal, tipeo cd y la direccion del archivo, pero despues me dice que tengo que ejecutar un .sh, y no se como. Si lo hago en la interfaz grafica (doble click al icono), no pasa nada, pero en la terminal no se cual es el comando para hacerlo.

3) Cual es el mejor emulador de Windows? Muchas veces depende de para que lo voy a usar. Lo usaria solo para videojuegos, mas que nada FPSs. Cedega parece bastante bueno, y en el 90% de las imagenes esta corriendo un FPS, pero igual quiero estar seguro antes de descargar. 

Esos son los tres problemas que me mantienen un poco lejos de Ubuntu, si alguien me ayuda y los puedo solucionar ya voy a poder dejar Windows sin problemas.

---

### Post by tzulberti on 2008-04-22
> **madelaki said:**
> Antes que nada, por favor entiendan que instale ubuntu esta semana, sin saber nada de Linux y ya busque en Ayuda y Soporte.

1) Cuando selecciono "Vista 3D de Ajedrez" en el ajedrez de Ubuntu, me tira este error. 

[http://img257.imageshack.us/img257/9477/pantallazo12vh1.png](http://img257.imageshack.us/img257/9477/pantallazo12vh1.png)

Me doy cuenta de que el problema con OGL es serio, pero no tengo idea de como solucionarlo. 

Puede ser que tengas una placa Nvidia o Ati y no te instalastes los drivers propietarios?

> **madelaki said:**
> 
2) Alguien me puede vincular a una guia o explicarme bien como llegar al setup de archivos .bz2, .tar.bz2, .tar.gz y .run? Lo que hay en Ayuda y Soporte no me sirvio, porque tiene en cuenta conocimiento previo que yo no tengo. Por ejemplo, abro la terminal, tipeo cd y la direccion del archivo, pero despues me dice que tengo que ejecutar un .sh, y no se como. Si lo hago en la interfaz grafica (doble click al icono), no pasa nada, pero en la terminal no se cual es el comando para hacerlo.

Porque queres instalar un programa desde tar.gz cuando tenes el apt-get. Fijate si encontras ese programa usando apt-get search palabraClave, y de la lista luego haces sudo apt-get install nombrePrograma.

> **madelaki said:**
> 
3) Cual es el mejor emulador de Windows? Muchas veces depende de para que lo voy a usar. Lo usaria solo para videojuegos, mas que nada FPSs. Cedega parece bastante bueno, y en el 90% de las imagenes esta corriendo un FPS, pero igual quiero estar seguro antes de descargar. 

Esos son los tres problemas que me mantienen un poco lejos de Ubuntu, si alguien me ayuda y los puedo solucionar ya voy a poder dejar Windows sin problemas.

El Wine funcionaba bastante bien las ultimas veces que lo probe (como hace 3 años :) ).

---

### Post by madelaki on 2008-04-22
Leiste lo que dije antes de preguntar? 

> Puede ser que tengas una placa Nvidia o Ati y no te instalastes los drivers propietarios?

No me sirve que me respondas a una pregunta con otra. Explicame que son, como se hace, etc. 

> Porque queres instalar un programa desde tar.gz cuando tenes el apt-get. Fijate si encontras ese programa usando apt-get search palabraClave, y de la lista luego haces sudo apt-get install nombrePrograma.

Gracias, pero y los .bz2, .tar.bz2 y .run?

---

### Post by tzulberti on 2008-04-22
> **madelaki said:**
> 
No me sirve que me respondas a una pregunta con otra. Explicame que son, como se hace, etc. 


El problema es el siguiente: los drivers libres, tanto el de ATI como el de Nvidia, no te dan acelareacion OpenGL. Sino me equivoco, ese juego la necesita. Para poder instalar el driver correspondiente, anda a System -> Admin -> ZZZ (algo que tiene que ver con drivers propietarios, no me acuerdo como es el nombre de la opcion.

> **madelaki said:**
> 
Gracias, pero y los .bz2, .tar.bz2 y .run?


Antes de instalar un programa usando .bz2, tar.bz2, .run, etc... Lo que haria es buscarlo usando "apt-cache search". Por darte un numero no muy errado: los repositorios de ubuntu, es decir en donde el apt busca el programa, tiene cerca 20.000 programas. Por lo tanto seria bastante raro que quieras instalar algo y que el mismo este en los repositorios.

---

### Post by madelaki on 2008-04-22
Me dice que el driver esta habilitado y en uso (en Controladores de Hardware).

---

### Post by InsektO on 2008-04-22
Tanto los drivers de ATI como nVidia traen soporte para aceleración 3D. Pero con respecto al Ajedrez, el problema no es ese, si no simplemente un "bug" (falta instalar algunas dependencias).

Si ya tenés los drivers de tu placa correctamente instalados (según lo que vos decís), debería solucionarse tu problema con:

```
sudo apt-get install python-opengl python-gtkglext1
```

Saludos!

PD: Por cierto, el Ajedrez en 3D se ve h0rr1bl3, así que sinceramente no vale la pena... :D

---

### Post by madelaki on 2008-04-22
Sep, funciono. Gracias che. 

Antes de que le de SOLVED falta esto: 
> 
2) Alguien me puede vincular a una guia o explicarme bien como llegar al setup de archivos .bz2, .tar.bz2, y .run?

---

### Post by sajnox on 2008-04-22
A ver si me sale la explicacion: Los archivos que vos describis generalmente son las fuentes del programa, en castellano los archivos escritos en el lenguaje de programacion para que vos los transformes en binarios (archivos ejecutables), por lo que entiendo esto pasa por varios motivos.

1) Si sabes programar podes modificar el programa a tu gusto o analizar que es lo que programa hace exactamente en tu computadora.  En windows esto poco comun ya que siempre nos manejamos con los .exe, rara vez ponen al alcance del usuario comun el archivo con las fuentes (pocas personas le pueden dar uso real)

2) Al haber tantas distribuciones "versiones" de Linux es muy dificil generar un arhcivo instalador para cada una. Generalmente hay para las mas conocidas, debian y basados en debian usan .deb (Ubuntu esta basado en Debian) estan los rpm de red hat y algun otro que no me acuerdo. Con esto te quiero decir que si ves para descargar siempre busca el .deb que es el que esta hecho para ubuntu.


Antes de intentar instalar cualquier cosa al estilo windows (bajar de alguna pagina y ejecutar un exe) busca el programa en el repositorio de Ubuntu (repositorio = base de software al que podes acceder para descargar programas y actualizaciones del SO)

¿Como buscar en el repositorio?

En administracion del sistema tenes el gestor de paquetes synaptic en el cual podes elegir las aplicaciones que queres instalar o desinstalar y buscar programas que quieras descargar

Si aun asi necesitas instalar desde las fuentes, te paso lo que para mi es la forma mas facil de hacerlo.

En primer lugar necesitas que el archivo que hayas descargado sea comprimido en tar.gz (si no es asi lo descomprimis y lo volves a comprimir en ese formato)

1) Instalas el comando alien

```
sudo apt-get install alien
```

2) Convertir el archivo que bajaste a .deb (lo mas parecido a un exe en windows)

```
sudo alien "nombre del archivo tar.gz"
```

3) Doble click en el archivo .deb que se genero

No siempre el programa que instales te va agregar un acceso por lo que tal vez precisas de crearte el lanzador.

Creo que con esto tenes para divertirte un rato, cualquier duda postea.

---

### Post by MeduZa on 2008-04-23
si no te queres complicar con la consola usa synaptics o add remove del menu

---

### Post by madelaki on 2008-04-23
> **sajnox said:**
> A ver si me sale la explicacion: Los archivos que vos describis generalmente son las fuentes del programa, en castellano los archivos escritos en el lenguaje de programacion para que vos los transformes en binarios (archivos ejecutables), por lo que entiendo esto pasa por varios motivos.

1) Si sabes programar podes modificar el programa a tu gusto o analizar que es lo que programa hace exactamente en tu computadora.  En windows esto poco comun ya que siempre nos manejamos con los .exe, rara vez ponen al alcance del usuario comun el archivo con las fuentes (pocas personas le pueden dar uso real)

2) Al haber tantas distribuciones "versiones" de Linux es muy dificil generar un arhcivo instalador para cada una. Generalmente hay para las mas conocidas, debian y basados en debian usan .deb (Ubuntu esta basado en Debian) estan los rpm de red hat y algun otro que no me acuerdo. Con esto te quiero decir que si ves para descargar siempre busca el .deb que es el que esta hecho para ubuntu.


Antes de intentar instalar cualquier cosa al estilo windows (bajar de alguna pagina y ejecutar un exe) busca el programa en el repositorio de Ubuntu (repositorio = base de software al que podes acceder para descargar programas y actualizaciones del SO)

¿Como buscar en el repositorio?

En administracion del sistema tenes el gestor de paquetes synaptic en el cual podes elegir las aplicaciones que queres instalar o desinstalar y buscar programas que quieras descargar

Si aun asi necesitas instalar desde las fuentes, te paso lo que para mi es la forma mas facil de hacerlo.

En primer lugar necesitas que el archivo que hayas descargado sea comprimido en tar.gz (si no es asi lo descomprimis y lo volves a comprimir en ese formato)

1) Instalas el comando alien

```
sudo apt-get install alien
```

2) Convertir el archivo que bajaste a .deb (lo mas parecido a un exe en windows)

```
sudo alien "nombre del archivo tar.gz"
```

3) Doble click en el archivo .deb que se genero

No siempre el programa que instales te va agregar un acceso por lo que tal vez precisas de crearte el lanzador.

Creo que con esto tenes para divertirte un rato, cualquier duda postea.

Posteate algo. SOLVED, gracias.

EDIT: Que pasa? No aparece Mark this thread as SOLVED en Thread Tools O_o

EDIT2: Oh, ya lei lo de que movieron el foro.. y ahora como es lo de SOLVED?

---

