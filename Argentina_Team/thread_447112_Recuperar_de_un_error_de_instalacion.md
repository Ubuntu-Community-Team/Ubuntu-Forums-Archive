---
title: "Recuperar de un error de instalacion"
date: 2007-05-17
forum: Argentina Team
---

### Post by fetova on 2007-05-17
Hola!

Estaba instalando desde el .deb de virtualbox y se me trabo el gdebi... ahora no puedo instalar nada. Doy dpkg --configure -a y no pasa nada, doy sudo apt-get install -f y me da:  El paquete virtualbox necesita ser reinstalado, pero no se encuentra un archivo para éste.

Que puedo hacer :(

Gracias de antemano

---

### Post by lugonesjoaquin on 2007-05-17
No tengo idea, y tratas haciendo un

sudo dpkg -r virtualbox

No sé...Ni idea!

---

### Post by fetova on 2007-05-18
> **lugonesjoaquin said:**
> No tengo idea, y tratas haciendo un

sudo dpkg -r virtualbox

No sé...Ni idea!

dpkg: error al procesar virtualbox (--remove):
 El paquete está en un estado muy malo e inconsistente - debe reinstalarlo
 antes de intentar desinstalarlo.
Se encontraron errores al procesar:
 virtualbox

Nop :( no sirve

Pero gracias...

---

### Post by kalel on 2007-05-18
te fijaste en el synaptic los paketes rotos?

---

### Post by fetova on 2007-05-18
> **kalel said:**
> te fijaste en el synaptic los paketes rotos?

no puedo abrir synaptic

El paquete es virtualbox el .deb de la pagina, tuve que romper el gdebi pues no jalaba y desde ahi :( ya no se puede

---

### Post by Al_maverick on 2007-05-19
proba con: 

sudo dpkg --configure -a

tambien proba reinstalar el paquete .deb con:

sudo dpkg -i <nombre del .deb>

y despues, para removerlo:

sudo dpkg -r virtualbox

Cualquier error que te tire pone el mensaje completo.

---

### Post by fetova on 2007-05-21
> **Al_maverick said:**
> proba con: 

sudo dpkg --configure -a

tambien proba reinstalar el paquete .deb con:

sudo dpkg -i <nombre del .deb>

y despues, para removerlo:

sudo dpkg -r virtualbox

Cualquier error que te tire pone el mensaje completo.

```
federico@fetova:~/Desktop$ sudo dpkg -i VirtualBox_1.3.8_Ubuntu_feisty_i386.deb Seleccionando el paquete virtualbox previamente no seleccionado.
(Leyendo la base de datos ... 
dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`virtualbox', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.
 
92545 ficheros y directorios instalados actualmente.)
Preparando para reemplazar virtualbox 1.3.8_Ubuntu_feisty (usando VirtualBox_1.3.8_Ubuntu_feisty_i386.deb) ...
Desempaquetando el reemplazo de virtualbox ...
Configurando virtualbox (1.3.8_Ubuntu_feisty) ...
 * Starting VirtualBox kernel module vboxdrv                             [ OK ] 

federico@fetova:~/Desktop$ sudo aptitude purge virtualboxLeyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo información de estado... Hecho
Leyendo la información de estado extendido       
Inicializando el estado de los paquetes... Hecho
Construir la base de datos de etiquetas... Hecho
Se ELIMINARÁN automáticamente los siguientes paquetes:
  virtualbox{p} 
Se ELIMINARÁN los siguientes paquetes:
  virtualbox{p} 
0 paquetes actualizados, 0 nuevos instalados, 1 para eliminar y 0 sin actualizar.
Necesito descargar 0B de ficheros. Después de desempaquetar se liberarán 25.8MB.
¿Quiere continuar? [Y/n/?] Y
Escribiendo información de estado extendido... Hecho
(Leyendo la base de datos ...  
93090 ficheros y directorios instalados actualmente.)
Desinstalando virtualbox ...
 * Stopping VirtualBox kernel module vboxdrv                             [ OK ] 
Purgando ficheros de configuración de virtualbox ...
```

:D

Gracias!!!

Probe hasta con poner:
```
dpkg-reconfigure -a
```
Y no, descubri hasta como configurar el nivel con el que te pregunta el sistema: critico, bla, bla, bla. :)

---

