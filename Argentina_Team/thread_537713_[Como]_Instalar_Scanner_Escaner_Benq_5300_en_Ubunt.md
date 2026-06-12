---
title: "[Como] Instalar Scanner Escaner Benq 5300 en Ubuntu Kubuntu Xubuntu 7.04"
date: 2007-08-29
forum: Argentina Team
---

### Post by LikeVinyl on 2007-08-29
Hola humanistas amigos!

Hoy vamos a aprender [Cómo] instalar correctamente un scanner Benq 5300u y cualquier scanner que utilice el backend snapscan para SANE. Para verificar la lista de compatibilidad con el backend sane, ir al final de este documento.

Manos a la obra!

**Preparando el sistema**

Lo primero que haremos será instalar xsane y dependencias necesarias.

Un método sencillo:

$ sudo aptitude install xsane

Un método para mentes brillantes:

$ sudo apt-get install libieee1284-3 libsane sane-utils xsane xsane-common

Recomiendo utilizar el método sencillo, es más útil a la hora de mantener el sistema.

**Seleccionando el firmware correcto**

Ahora será necesario identificar el firmware que utiliza nuestro scanner, para ello, podemos utilizar dos procedimientos:

   1. Descargar el siguiente script [http://snapscan.sourceforge.net/acerfirm](http://snapscan.sourceforge.net/acerfirm) y ejecutar con acerfirm -q (este script identifica modelo y firmware necesario).
   2. Observar la siguiente tabla: [http://snapscan.sourceforge.net/](http://snapscan.sourceforge.net/) buscar el modelo de nuestro scanner y verificar el firmware que utiliza. Para este ejemplo, basado en un scanner Benq 5300u, utilizaremos el firmware u254v042.bin.

    * En este caso, solo observaremos la tabla utilizando el método número 2, es una práctica para el uso del sentido común ya que no necesitamos un script; De todos modos, vale la intención del desarrollador. 

**¿Dónde consigo el firmware para mi scanner?**

El firmware se encuentra, por lo general, en el disco de controladores para window$ proporcionado por el fabricante del scanner. No explicaré cómo buscarlo, solo explorar el contenido del cd y buscar el fichero que corresponde, para este ejemplo, el fichero tiene el nombre u254v042.bin

**Instalación**

En este punto, copiaremos el firmware en el siguiente directorio:

$ sudo cp u254v042.bin /usr/share/sane/snapscan/

**Configuración**

En este punto, indicaremos al archivo de configuración snapscan.conf dónde buscar el firmware que copiamos en el paso anterior.

Para ello, editar el archivo que se encuentra en el directorio /etc/sane.d/ con el siguiente comando:

$ sudo gedit  /etc/sane.d/snapscan.conf

Dentro del fichero,  agregar el nombre del fichero que corresponde al firmware -normalmente en la línea número 5- de todos modos, para una mejor referencia la línea que debemos modificar tiene color rojo.

Una vista rápida del archivo snapscan.conf

#------------------------------ General -----------------------------------
 
# Change to the fully qualified filename of your firmware file, if
# firmware upload is needed by the scanner
[COLOR="Red"]firmware /usr/share/sane/snapscan/u254v042.bin[/COLOR]

# If not automatically found you may manually specify a device name.
 
# For USB scanners also specify bus=usb, e.g.
# /dev/usb/scanner0 bus=usb
 
# For SCSI scanners specify the generic device, e.g. /dev/sg0 on Linux.
# /dev/sg0
 
#---------------------------------------------------------------------------
# No changes should be necessary below this line
#---------------------------------------------------------------------------

**Probando el scanner**

Navegar el menú Gráficos -puede variar según nuestro manejador de escritorio y/o manejador de ventanas- seleccionar “Programa de escaneo de imágenes Xsane” este realizará una comprobación de dispositivos y si encuentra más de uno, nos pedirá que seleccionemos el que deseamos utilizar.

**Desinstalación**

Si deseamos quitar Xsane y los archivos de configuración, ejecutamos el siguiente comando:

$ sudo aptitude purge xsane

**Notas finales**

Probado en mi equipo P4 3.2 1GB de RAM, Xfce, Gnome y Enlightenment e17. -El equipo es bueno pero mi escaner es barato-

Unicamente para el modelo Benq 5300u, basado en mi experiencia con dos escáneres que utilizan el mismo firmware:

En algunos casos, luego de iniciar la “previa” de escaneo, es posible que el escaner quede colgado cuando la lámpara regresa al punto de inicio, en ese caso, pulsar el botón “scan” aguardar unos minutos y éste se reiniciará -notaremos que parpadean las luces frontales- Esperar que regrese la lámpara al punto de inicio y eso es todo, ya podemos trabajar normalmente. 

Aquí finalizamos, a digitalizar!

Fuentes y más información:
[http://snapscan.sourceforge.net/](http://snapscan.sourceforge.net/)

Este documento es Copyleft, LikeVinyl, 2007 
Tienes la Libertad de copiarlo y distribuirlo libremente.

---

