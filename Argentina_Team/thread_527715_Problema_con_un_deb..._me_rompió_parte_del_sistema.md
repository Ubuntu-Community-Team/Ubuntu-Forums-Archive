---
title: "Problema con un deb... me rompió parte del sistema"
date: 2007-08-16
forum: Argentina Team
---

### Post by Mafber on 2007-08-16
Hola a todos!!! tengo un problemita. 
Resulta que intenté instalar el juego Alien Arena desde un paquete deb. Cuando traté de instalar el alien-arena-data me tiró un error, que no me acuerdo que decía. Cada vez que intento reinstalarlo me tira el siguiente error: “El paquete podría estar dañado, o puede que usted no tenga permisos para abrir el archivo. Revise los permisos” y también me da este error con cualquier deb. No es un problema de permisos porque lo ejecuté siendo root y me tira lo mismo. También lo descargué 3 veces, y no se soluciona.
Pero el problema verdadero no es el juego, sino que no me deja actualizar ubunto ni abrir synaptic. 
Dan este error y se cierran:
“E: El paquete alien-arena-data necesita ser reinstalado, pero no se encuentra un archivo para éste.

E: Error interno al abrir el caché (1). Por favor informe de este error.”

Bien, ya probé con:
1.- sudo dpkg-reconfigure alien-arena-data

respuesta:  /usr/sbin/dpkg-reconfigure: alien-arena-data está roto o no está totalmente instalado


2.- sudo apt-get install alien-arena-dataLeyendo 
lista de paquetes... Hecho

Creando árbol de dependencias       

Leyendo información de estado... Hecho

E: El paquete alien-arena-data necesita ser reinstalado, pero no se encuentra un archivo para éste.


3.- sudo apt-get -f install

Leyendo lista de paquetes... Hecho

Creando árbol de dependencias       

Leyendo información de estado... Hecho

E: El paquete alien-arena-data necesita ser reinstalado, pero no se encuentra un archivo para éste.


4.-  sudo aptitude  purge alien-arena-dataLeyendo lista de paquetes... Hecho

Creando árbol de dependencias       

Leyendo información de estado... Hecho

Leyendo la información de estado extendido      

Inicializando el estado de los paquetes... Hecho

Construir la base de datos de etiquetas... Hecho

Se ELIMINARÁN automáticamente los siguientes paquetes:

  alien-arena-data{p} 

Se han retenido los siguientes paquetes:

  libvorbis0a libvorbisenc2 libvorbisfile3 

Se ELIMINARÁN los siguientes paquetes:

  alien-arena-data{p} 

0 paquetes actualizados, 0 nuevos instalados, 1 para eliminar y 3 sin actualizar.

Necesito descargar 0B de ficheros. Después de desempaquetar se usarán 0B.

¿Quiere continuar? [Y/n/?] y

Escribiendo información de estado extendido... Hecho

dpkg: error al procesar alien-arena-data (--purge):

 El paquete está en un estado muy malo e inconsistente - debe reinstalarlo

 antes de intentar desinstalarlo.

Se encontraron errores al procesar:

 alien-arena-data


Y algunos otros comandos pero no resultaron. 
Alguna idea ????? lo que busco es lo contrario de lo que haría en xp (reinstalar) 

Desde ya GRACIAS!!!!!

---

### Post by lavaramano on 2007-08-17
no te llegue a preguntar, pero hiciste:

dpkg -i alien-etcetc.deb
dpkg -r alien-etcetc.deb

bue. segui posteando cualquier cosa

---

### Post by Mafber on 2007-08-17
Hola lavaramano!!!! gracias!! funcionó lo que me dijiste.  Muchas gracias!!!! :)

---

### Post by MeduZa on 2007-08-18
je, eso que te paso es normal, se te rompio un pakete porque instalaste otro que era dependiente,
te vas a synaptics y donde dice broken ahi desinstalas los que aparezcan y solucionado el problema, o instalas el pakete que te esta faltando en este cado alien data.
Pasa siempre que instalas un deb que depende de otros!

---

### Post by Mafber on 2007-08-20
Hola MeduZa!!! te comento que no me dejaba abrir synaptic. Me tiraba un error y cuando ponía aceptar se cerraba synaptic. 
Cuando trataba de actualizar sencillamente se limitaba a decirme que tenia que reinstalar primero el archivo roto. Si intentaba reinstalarlo no me dejaba y me volvía a decir que lo tenia que reinstalar.
Supongo que se arreglo con "dpkg -r" pero funcionó por varios motivos (ya lo había intentado de entrada y no me había funcionado).
Así que gracias para  lavaramano y a quasar que me dieron una mano para solucionar el problema :)

---

