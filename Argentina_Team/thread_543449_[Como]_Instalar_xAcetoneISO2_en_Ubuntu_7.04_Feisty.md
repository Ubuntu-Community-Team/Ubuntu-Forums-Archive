---
title: "[Como] Instalar xAcetoneISO2 en Ubuntu 7.04 Feisty Fawn"
date: 2007-09-05
forum: Argentina Team
---

### Post by LikeVinyl on 2007-09-05
Hola humanistas amigos!

Este tutorial explicará [Como] instalar xAcetoneISO2 en Ubuntu 7.04 Feisty Fawn

**¿Para que sirve xAcetoneISO2?**

xAcetoneISO2 es un programa para montar variedad de imágenes de disco sin necesidad de especificar un punto de montaje o destino.

Por otro lado, xAcetoneISO2 es un sub-proyecto para usuarios de Gnome/Gtk que se desprende del AcetoneISO2 disponible para usuarios Kde.

Dentro de sus características podemos encontrar:

    * Monta/Desmonta ISO, MDF, NRG, IMG, BIN (no requiere contraseña)
    * Muestra imágenes montadas en pantalla
    * Montaje automático, no requiere especificar destino
    * Convierte/Descomprime/Explora desde ISO: *.bin *.mdf *.nrg *.img *.daa *.cdi *.xbx *.b5i *.bwi *.pdi
    * Reproduce una pelicula DVD dentro de Kaffeine o VLC con descargador de carátulas
    * Genera un ISO desde una carpeta o unidad de CD/DVD
    * Genera/Verifica archivos de imágen codificados con MD5
    * Encripta/Desencripta imágenes
    * Divide/Une imágenes con el tamaño que deseemos
    * Comprime con alto nivel de compresión imágenes con formato *.7z
    * Copia un cd PSX a .bin para que funcione con emuladores epsxe/psx
    * Menú de servicio que puede integrarse en Konqueror.
    * Restaura ficheros perdidos CUE de imágenes .bin e .img
    * Formatea/Blanquea discos CD/DVD
    * Graba ISO/CUE a CD/DVD
    * Monta imágenes .dmg de Mac OS
    * Recupera información de una imagen
    * Soporta El-Torito para crear una imagen ISO de arranque
    * Monta imágenes .iso en una carpeta definida por el usuario
    * Crear ua base de datos de imágenes
    * Extrae imágenes de arranque de un CD/DVD o ISO.

**Antes de empezar**

xAcetoneISO2 se encuentra en fase BETA4. De todos modo su desarrollo está muy avanzado y es funcional en la mayoría de sus características quedando pendiente la función de encriptación.

Asumiremos que disponemos de Ubuntu 7.04 Feisty Fawn o cualquier distribución basada en Ubuntu 7.04 Feisty Fawn.

Como indicamos al comienzo, esta versión está destinada a usuarios que no deseen instalar librerías para el manejador de escritorio Kde o cualquier programa relacionado con Kde; De todos modos, instalaremos QT4 pero tendremos díalogos GTK y el soporte adecuado dentro de nautilus como así también su consola nativa. En otras palabras, no más programas relacionados con Kde.

Manos a la obra!

**Preparando el sistema**

Primero instalar las dependencias requeridas, dentro de una consola o terminal dentro de X, invocar el siguiente comando:

> $ sudo apt-get install fuse-utils libfuse2 mkisofs libqt4-core libqt4-gui libfuse-dev build-essential cdrecord cdrdao dvd+rw-tools p7zip-full gnupg coreutils libglib2.0-dev zenity gksu

**Descargando fuseiso**

Este paso es importante; El sitio oficial indica &#8220;Usuarios Ubuntu, no instalar fuseiso desde el repositorio oficial porque se encuentra desactualizado&#8221;.

Haremos caso a esta advertencia; Desde una consola o terminal dentro de X, invocar el siguiente comando:

> $ wget [http://download.tuxfamily.org/3v1deb/pool/feisty/3v1n0/fuseiso_20061017-0%7E3v1ubuntu0_i386.deb](http://download.tuxfamily.org/3v1deb/pool/feisty/3v1n0/fuseiso_20061017-0%7E3v1ubuntu0_i386.deb)


**Instalando fuseiso**

Desde una consola o terminal dentro de X, invocar el siguiente comando:

> $ sudo dpkg -i fuseiso_20061017-0~3v1ubuntu0_i386.deb

**Descargando xAcetoneISO2**

Desde una consola o terminal dentro de X, invocar el siguiente comando:
> 
$ wget [http://www.acetoneteam.org/Archivia/xAcetoneISO2-src_BETA4.tar.gz](http://www.acetoneteam.org/Archivia/xAcetoneISO2-src_BETA4.tar.gz)

**Instalando xAcetoneISO2**

Desde una consola o terminal dentro de X, invocar los siguientes comandos:
> 
$ tar -zxvf xAcetoneISO2-src_BETA4.tar.gz
$ cd xAcetoneISO2-src
$ sudo ./installer

Si todo es correcto, el instalador mostrará la siguiente salida:

Welcome to xAcetoneISO2, a gtk port of the KDE AcetoneISO2 software

checking write permissions
user has full permissions to write
installation will now start

3
2
1
Starting installation
please wait

intallation 100%

I will now do a quick test to check most important dependencies

zenity found OK
fusermount found OK
fuseiso found OK

You seem to be able to use most functions of xAcetoneISO2
Please dont forget to visit [http://www.acetoneteam.org/manual.html](http://www.acetoneteam.org/manual.html)

I suppose everything is OK
Please run xAcetoneISO2 as normal user typing acetoneiso2

The End

**Asignando permisos**

En algúnos casos, xAcetoneISO2 no asigna los permisos adecuados y esto no permite montar las imágenes; Desde una consola o terminal dentro de X, invocar los siguientes comandos:

> $ sudo chmod 4755 /usr/bin/fusermount
$ sudo chmod o+rw /dev/fuse
$ sudo adduser "usuario" fuse

    * Atención el usuario debe ir entre comillas ej. $ sudo adduser &#8220;likevinyl&#8221; fuse
[B]
Iniciando xAcetoneISO2[/B]

En la barra de herramientas de gnome, pulsar click sobre Aplicaciones->Accesorios->AcetoneISO2

Pulsar la solapa &#8220;convert&#8221; y pulsar el botón &#8220;convert image to ISO&#8221;

    * Este procedimiento es requerido una única vez para instalar poweriso

Una vez que finalice la descarga, mostrará una pantalla con el siguiente mensaje &#8220;PowersISO succesfully downloaded and installed Please click again on Convert button&#8221; tipear la contraseña de administrador cuando sea requerida.

Pulsar el &#8220;Help&#8221; situado en la barra de herramientas y seleccionar &#8220;Activate Fuseiso&#8221;

    * Este procedimiento es requerido una única vez

Listo para utilizar!

**Desinstalando xAcetoneISO2**

Si experimentamos dificultades y deseamos revertir los cambios, desde una consola o terminal dentro de X, invocar los siguientes comandos:

> $ sudo dpkg --remove fuseiso_20061017-0~3v1ubuntu0_i386.deb
$ sudo apt-get remove fuse-utils p7zip-full gnupg coreutils libglib2.0-dev zenity gksu libqt4-core libqt4-gui

    * Las dependencias para la desintalación difieren con la instalación porque suponemos hay paquetes importantes que son utilizados por otros programas.

> $ cd xAcetoneISO2-src
$ sudo ./uninstaller

**Notas finales**

El procedimiento describe la instalación de xAcetoneISO2 en su versión BETA4 y fué probado con éxito en un Intel Pentium 4 Dual Core 3.0ghz con 1gb de RAM y video nVidia GeForce XFX 5200 de 128mb.

**Fuentes:**
[http://www.acetoneteam.org/]("http://www.acetoneteam.org/")

::: LikeVinyl 2007 :::

Este documento es Copyleft, Miguel Angel Ríos, 2007
Tienes la Libertad de copiar, modificar y distribuir libremente esta documentación.

---

### Post by bulletxt on 2007-09-05
Just a very quick note. If you install fuseiso from trevino rep it is not needed anymore some dependencies.

These are the dependencies with fuseiso already installed:

fuse-utils libfuse2 mkisofs libqt4-core libqt4-gui cdrecord cdrdao dvd+rw-tools p7zip-full gnupg coreutils zenity gksu



bye!

---

### Post by faktorqm on 2007-09-05
Hola, está bueno el tuto, yo habia hecho uno hace muy poco pero este está mejor explicado, capaz tenés mas paciencia. :D gracias por el aporte y salu2!! :D

---

### Post by LikeVinyl on 2007-09-05
> **bulletxt said:**
> Just a very quick note. If you install fuseiso from trevino rep it is not needed anymore some dependencies.

These are the dependencies with fuseiso already installed:

fuse-utils libfuse2 mkisofs libqt4-core libqt4-gui cdrecord cdrdao dvd+rw-tools p7zip-full gnupg coreutils zenity gksu



bye!

Explains: this guide describe the installation of xAcetoneISO2 - port gnome/gtk- Please, [readme]("http://www.acetoneteam.org/acetoneiso-gnome.html"). 

"note: ubuntu users MUST not install fuseiso from original rep because it is old.
please install [this one for feisty users]("http://download.tuxfamily.org/3v1deb/pool/feisty/3v1n0/fuseiso_20061017-0%7E3v1ubuntu0_i386.deb")"

Thank you very much.

---

### Post by LikeVinyl on 2007-09-05
> **faktorqm said:**
> Hola, está bueno el tuto, yo habia hecho uno hace muy poco pero este está mejor explicado, capaz tenés mas paciencia. :D gracias por el aporte y salu2!! :D

Hola faktorqm!

Gracias :) recién acabo de leer tu post, básicamente dicen lo mismo ¿sincronicidad? :) En cuanto a la paciencia, somos usuarios GNU/Linux estamos todos quemados. Si, trabajé un tiempo redactando manuales técnicos. Un abrazo! 

Miguel.

---

### Post by por100pre1 on 2007-09-05
Las buenas ideas son cosa común en estos foros. ¡Gracias! :)

---

### Post by Mataca on 2007-09-05
La aplicación es excelente muy recomendable

---

### Post by demauk on 2007-10-02
Excelente guía. Muchas gracias!

---

