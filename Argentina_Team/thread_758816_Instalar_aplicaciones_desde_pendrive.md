---
title: "Instalar aplicaciones desde pendrive"
date: 2008-04-18
forum: Argentina Team
---

### Post by rbarbe on 2008-04-18
Buenas, quiero saber si algún tutorial para instalar aplicaciones en Ubuntu desde un pendrive.

La conexión a internet en la máquina es dial-up, por lo que me conviene bajar los paquetes en el trabajo y llevarlos en un pendrive.

Pero luego viene la complicación de la instalación, ¿me pueden dar una mano? :confused:

Muchas gracias

---

### Post by AzureSky07 on 2008-04-18
Mira yo no tengo internet en mi casa y ante la consulta de como agregar aplicaciones me respondieron esto:

Otra opcion para instalar paquetes en tu maquina sin coneccion a internet es desde Synaptic, seleccionas los paquetes normalmente como si estuvieras conectado y te vas al menu Archivo -> Generar script de descarga de paquetes
, eso te genera un archivo que llevas a una maquina con coneccion a internet, los descargas y los incorporas en tu maquina desde Synaptic en la opcion de abajo del menu. Lo bueno de esto es que synaptic te resuelve automaticamente las dependencias de los paquetes y no tenes que hacerlo a mano.


espero que te sea de ayuda.

Saludos AzureSky

---

### Post by User21 on 2008-04-18
Lo mas sencillo que hay es bajar aplicaciones desde [www.getdeb.net]("http://www.getdeb.net") o desde [packages.ubuntu.com]("http://packages.ubuntu.com") .
Lo que quizás es necesario que tengas en cuenta, son las dependencias. Por ejemplo, X programa, depende de la libreria "YLIB", por ende, antes hay que instalarse la librería "YLIB", que se pude conseguir en el mismo sitio, o en sitios externos. 
Te doy un ejemplo concreto: instalar el [reproductor exaile desde packages.ubuntu.com]("http://packages.ubuntu.com/gutsy/exaile") , requiere de ciertas librerías, que alli se detallan. Algunas las tenés por defecto, otras necesitan ser instaladas. 

Sino, te vas al amigo Synaptic, elegís lo que querés instalar, y en el menú Archivo encontrás la fabulosa opción "Generar un script de descarga de paquetes". Eso te ayudara a descargar los paquetes luego, desde otra locación.

---

### Post by tzulberti on 2008-04-18
> **User21 said:**
> 
Sino, te vas al amigo Synaptic, elegís lo que querés instalar, y en el menú Archivo encontrás la fabulosa opción "Generar un script de descarga de paquetes". Eso te ayudara a descargar los paquetes luego, desde otra locación.

Sino me equivoco esa otra locacion necesita que tengas ubuntu o estoy mal? (supongo que en otras distros que usen el apt tambien funcionaria).

---

### Post by Mister X on 2008-04-18
> **tzulberti said:**
> Sino me equivoco esa otra locacion necesita que tengas ubuntu o estoy mal? (supongo que en otras distros que usen el apt tambien funcionaria).

Lo que hace es generar un script de bash que usa el wget para bajar automaticamente todos los paquetes seleccionados, obviamente se puede ejecutar en cualquier linux con wget instalado. Inclusive se puede usar desde win usando un gestor de descargas.

---

### Post by faktorqm on 2008-04-18
> **rbarbe said:**
> Buenas, quiero saber si algún tutorial para instalar aplicaciones en Ubuntu desde un pendrive.

La conexión a internet en la máquina es dial-up, por lo que me conviene bajar los paquetes en el trabajo y llevarlos en un pendrive.

Pero luego viene la complicación de la instalación, ¿me pueden dar una mano? :confused:

Muchas gracias

Hola, a ver, donde esta la dificultad en la instalacion de paquetes? O sea, pones el pendrive, y ejecutas uno por uno y los instalas "a mano" eso es todo.
Si tu pregunta iba orientada a "no quiero instalarlos a mano", tenes 2 opciones, agregar el pendrive en origenes del software, o correr un script que te liste los archivos de un determinado directorio y ejecutarlos uno atras del otro. 
Algo asi: "sudo dpkg -i archivoi.deb -y" con 1 < i < N siendo N el numero de archivos .deb en la carpeta. en realidad queria poner menor o igual pero puse menor. No tengo ningun tuto de bash a mano, pero es una papa, la funcion que te lista los directorios es una paponia y haces un for hasta EOF y de paso ya te queda para la proxima. Salu2!

---

