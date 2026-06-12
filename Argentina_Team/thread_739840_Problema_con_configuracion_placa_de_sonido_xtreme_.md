---
title: "Problema con configuracion placa de sonido xtreme gamer sound blaster en Kubuntu"
date: 2008-03-26
forum: Argentina Team
---

### Post by sebastianpnts on 2008-03-26
hola a todos 
Acabo de instalar ubuntu 64b
Mi primer problema es q la targeta de sonido una sound blaster xtreme gamer no funciona.
Baje los supuestos drivers para la targeta pero aqui vienen los problemas.
1ro Tengo q usar un terminal como root y no puedo porq no me reconose el password
Authentication failure.El punto es q cuando lo instale no me pidio ningun passowrd para el root  no como en mandriva u otro distro.
Si alguien lo ha instalado porfavor q me expliquen como hacerlo estare agradecido
PD soy totalmente nuevo ni siquera se q es compilar los codigos fuente q dice q debo hacer segun en la web de sound blaster.
Gracias :(

---

### Post by guisheca on 2008-03-26
Bueno, vamos por partes. En primer lugar ubuntu trae desactivado el usuario root por defecto, por cuestiones de seguridad. Para utilizar el terminal como administrador tenés que anteponer "sudo" al comando que queres ejecutar como administrador, después de eso, te va a pedir tu contraseña de usuario, dásela, y listo va a ir el comando como si fuera root.
Hacelo así y contá como te fué.

---

### Post by faktorqm on 2008-03-26
Hola, empecemos de a poco.
Primero instalate la version de 32 bits, y te vas a ahorrar muuuuchos dolores de cabeza, creeme. Una vez que aprendas, si queres despues te pasas a 64.
Lo de la terminal como root, es un peligro potencial, como bien dijo aca el señor guisheca si queres hacer algo como root antepones la palabra sudo al comando.
.-*NO ABRIS LA TERMINAL COMO ROOT, USAS SUDO, OK?*-.
ejemplo: sudo mount /dev/hdd /media/cdrom0
Cuando te pide el password, tenes que ingresar el mismo que ingresaste cuando arrancaste la compu.
Para compilar, no necesitas saber "mucho", te las podes arreglar perfectamente preguntandonos a nosotros o leyendo BIEN el manual de los de creative, pero basicamente son 3 comandos con mas o menos parametros. No te asustes ni te des por vencido por que es una papa.
Nos vemos, y te esperamos mas seguido. Salu2!!

---

### Post by MaReaDo^ on 2008-03-27
cuando instalas ubuntu te crea un usuario y te pide una clave, esa clave, que es con la que logueas en el OS, es la que tenes que usar cuando pones sudo
fijate de que si tenes que formatiar, tener una particion aparte para el home y la raiz, no se si  o abras hecho antes, pero esto te ahorra configuraciones y perder archivos a la hora de reinstalar o instalar otro linux
yo soy relativamente nuevo en ubuntu y el otro dia actualice todos los drivers del sonido porque me hacia dramas y tenia mal sonido, y es bastante facil, hay muchos tutorials en la web, son 2 o 3 comandos
cualquier cosa como te dijeron arriba podes preguntar aca y te ayudamos en lo que podamos

---

### Post by sebastianpnts on 2008-03-27
Hola  de nuevo 
Antes q nada gracias por la ayuda, para ser honesto me sentia un poco solo con esto de linux sin tener a quien acudir 
Muchas gracias chicos.
Para mostrar mejor mi situacion les dire lo q hice.
Cuando instale kubuntu lo instale de forma automatica le di una particion de 16g y luego elegi el login y demas supongo q las particiones de root y todo eso lo habra hecho por defecto.
Lo segundo es q me decidi instalar el de 64b porq sound blaster no hace driver para 32b, he leido en paginas de gente q conciguio hacer funcionar la sound blaster, pero hablan de cosas q no tengo ni idea
lo de ni idea recalcado.
Soy nuevo en linux y la maxima experiencia q tengo es instalar una geforce de 250M en mandrake 10, baje el driver, sali de las x y luego como root hice lo q decia nvida
sh NVblablablabla. y funciono.
volviendo al caso de sounblaster tipie en el terminal lo q dice el fichero q baje y me dice lo siguiente.
THIS PRODUCT ONLY SOPPORT  64-BIT OPERATING SYSTEM.
THE SETUP WILL NOW EXIT.
$
lo tipico 
q cualquier nobato piensa instale uno de 32, estoy casi seguro q no porq revise la imagen q baje de kubuntu para verificar si era el de 64 y lo es, no se q puede ser, lo q si es q en el fichero de README      dice q debo primero tener fully configured source for the Linux kernel :shock::shock:
q es eso???
me dio con un valde de agua fria en la cara,
Debe ser dificil y un grand dolor de cabeza ayudar a alguien q no tiene ni papa idea como yo,
Como ya les dije antes gracias por cualquier consejo o ayuda q me den tratare de buscar algun libro de bolsillo q exlique un poco lo basico de linux para no andar en el aire.

---

### Post by faktorqm on 2008-03-27
Hola, bueno entonces te vamos a ayudar en tus dolores de cabeza :KS

Para instalar  lo que te piden, tenes que escribir el siguiente comando:

```
sudo apt-get install linux-headers-`uname -r` build-essential
```

Esto significa que, instale como administrador las cabeceras del kernel de la version actual (la version actual te la da el comando uname -r) y aparte que instale el soporte para compilar cosas.

De paso, pasame el link del driver que estas intentando compilar asi leo el readme y te guio mejor. Salu2!!

---

### Post by sebastianpnts on 2008-03-27
gracias por la ayuda faktorqm voy a hacer lo q me dices y el enlace del driver es este
[http://uk.europe.creative.com/support/downloads/download.asp?MainCategory=209&nRegionFK=&nCountryFK=&nLanguageFK=&sOSName=Linux&region=3&Product_Name=X-Fi+Xtreme+Gamer&Product_ID=15853&modelnumber=&driverlang=1033&OS=12&select=0&x=31&y=23](http://uk.europe.creative.com/support/downloads/download.asp?MainCategory=209&nRegionFK=&nCountryFK=&nLanguageFK=&sOSName=Linux&region=3&Product_Name=X-Fi+Xtreme+Gamer&Product_ID=15853&modelnumber=&driverlang=1033&OS=12&select=0&x=31&y=23)
es la pagina de sound blaster [www.soundblaster.com](www.soundblaster.com) pero para q no andes buscando lo dejo aca al readme no es muy largo.
  Sound Blaster X-Fi Linux x86_64 Beta Driver Readme File

  September 2007

====================================================================

The purpose of this document is to describe how the X-Fi Linux device 
driver is built, packaged, and released.




Quick install

=============


1) You must have the fully configured source for the Linux kernel and 
   ALSA which you
 want to use for this device driver. Partial installed 
   kernels (e.g. From distribution makers) may be unusable for this 
   action.



2) Run one of the following commands as root in the terminal:



   ./installer
   


   OR


   ./installer --with-alsainc=<ALSA_include_directory>



  * ALSA Source Tree


   
   On 2.6 kernels, the location of the ALSA source include directory

      is parsed automatically from the running kernel.

      If it is not in the standard place, specify the path via
   
   --with-alsainc=<ALSA_include_directory>.

 
   
  On 2.4 kernels, the location of the ALSA source include directory

      must be specified via --with-alsainc=<ALSA_include_directory>.



  * Note
      If integrated ALSA is to be used to build, --with-alsainc option

      must not be specified.






Uninstall

=========


In the terminal,


1) Change directory to /opt/Creative/XFiDrv_Linux_US-1.04



2) Run the following command as root


   ./configure

   make uninstall



 * Note

      For GNOME users, You may need to close the Volume Control
      applet before uninstalling. Right-click the Volume icon on the
      GNOME panel and select "Remove From Panel"



3) Manually delete all files in /opt/Creative/XFiDrv_Linux_US-1.04








Copyright (c) 2007 Creative Technology Ltd. All rights reserved.

====================================================================

  End of Readme File

====================================================================

---

### Post by faktorqm on 2008-03-28
El readme dice: 

1) Vos debes tener completamente configurado el fuente del kernel de linux y el de alsa para poder utilizar este driver. Los kernel's parcialmente instalados (ejemplo: los que son de creadores de distribuciones) pueden no ser utiles para esto.

para eso corre el comando que t puse antes.


2) Ejecuta uno de los siguientes comandos con permisos de root en una terminal:

./installer

o sea, tenes que escribir ```
sudo ./installer
```


El comando que te dice despues (./installer --with-alsainc=<ALSA_include_directory>) no sirve por que tenemos kernel 2.6 y la ruta es la estandard, si por casualidad lo llegas a necesitar, escribi en una terminal "whereis alsa" y ahi te dice la ruta en la cual esta. (no se si los includes)

bueno lo vamos viendo. Salu2!!

---

### Post by sebastianpnts on 2008-03-28
ejecute los comandos como me dijistes.
fue todo bien pero cuando ejecute el instaler lo mismo de antes
This product only support 64-bit Operating Systems
Setup will now exitGracias por la mano faktorqm

---

### Post by faktorqm on 2008-03-29
ahora me estoy bajando el paquete, lo miro y t aviso

---

### Post by sebastianpnts on 2008-03-30
:confused:
Probe instalar  la targeta de sonido y nada,
porfa no me dejen colgado no quiero volver a win por no tener sonido

---

### Post by Hei Ku on 2008-03-30
data, necesitamos data para poder ayudarte.

En esta seccion hacemos hechizos, no milagros. Si no sabemos q ubuntu tenes, y que tarjeta de sonido, no podemos hacer nada. :D

---

### Post by --Lutari-- on 2008-03-30
Lamentablemente Ayer se me Rompio la Bola de Cristal así que los Poderes de Adivinación se fueron xD Mas información please

---

### Post by sebastianpnts on 2008-03-30
hola hei ku
deje en otro post mi situacion por eso no lo puse de nuevo 8-[
Lo comento de nuevo 
instale kubuntu 64 bit, la targeta de sonido es una xtreme gamer sound blaster.
baje los drivers de la web, decidi instalar el de 64b porq sound blaster no hace drivers para so de 32b.otro miembro me dijo q instale los headers 
creo q asi se llaman, el asunto es q cuando intento instalar el driver dice q soporta solamente sistemas de 64b, revise la imagen q baje por si  era el de 32b  el q me baje, pero no la imagen es de 64b.Esa es mi situacion, soy nuevo usando linux, fue facil instalarlo pero claro los problemas vienen cuando tenes q instalar la targeta de sonido y la de video si no tienes experiencia en esto, Me gusta como camina la computadora tiene mejor rendimiento y es estable por eso no quiero volver a win como de seguro le pasa a muchos.aca dejo el readme del fichero q baje de soundblaster.
no se q otro data debo poner asique si hace falta mas datas diganme y los pongo en el post.
  Sound Blaster X-Fi Linux x86_64 Beta Driver Readme File

  September 2007

====================================================================

The purpose of this document is to describe how the X-Fi Linux device 
driver is built, packaged, and released.




Quick install

=============


1) You must have the fully configured source for the Linux kernel and 
   ALSA which you
 want to use for this device driver. Partial installed 
   kernels (e.g. From distribution makers) may be unusable for this 
   action.



2) Run one of the following commands as root in the terminal:



   ./installer
   


   OR


   ./installer --with-alsainc=<ALSA_include_directory>



  * ALSA Source Tree


   
   On 2.6 kernels, the location of the ALSA source include directory

      is parsed automatically from the running kernel.

      If it is not in the standard place, specify the path via
   
   --with-alsainc=<ALSA_include_directory>.

 
   
  On 2.4 kernels, the location of the ALSA source include directory

      must be specified via --with-alsainc=<ALSA_include_directory>.



  * Note
      If integrated ALSA is to be used to build, --with-alsainc option

      must not be specified.






Uninstall

=========


In the terminal,


1) Change directory to /opt/Creative/XFiDrv_Linux_US-1.04



2) Run the following command as root


   ./configure

   make uninstall



 * Note

      For GNOME users, You may need to close the Volume Control
      applet before uninstalling. Right-click the Volume icon on the
      GNOME panel and select "Remove From Panel"



3) Manually delete all files in /opt/Creative/XFiDrv_Linux_US-1.04








Copyright (c) 2007 Creative Technology Ltd. All rights reserved.

====================================================================

  End of Readme File

====================================================================

---

### Post by leo_rockway on 2008-03-30
Un título descriptivo en el post hace que más gente pueda ayudarte.

---

### Post by sajnox on 2008-03-30
Hola,

Te edite el titulo del post para que puedas recibir un poco mas de ayuda.

Saludos

---

### Post by Hei Ku on 2008-03-30
el paquete que tener instalado es el linux-headers-2.6.22-14-generic

Eso son los headers de librerias para los programas que necesitan instalar algo del kernel.
Ahora, hay un problema para instaladores viejos, que me parece que es lo que te esta pasando a vos. Anteriormente, el kernel era distinto de acuerdo a si la arquitectura era 32 o 64 bits. Hoy esta todo junto, porque se dieron cuenta que habia gran duplicacion de codigo, y solo ciertas partes son particulares de cada arquitectura.
Asi que me parece que el problema debe estar en como verifica el script que el kernel es de 64 bits.

La manera mas facil de ver eso es abrir el script y buscar el mensaje de error, justo antes de eso debe estar la verificacion de 64 bits. Podes postearlo aca, a ver si te ayudamos?

(todo esto suma puntos para la tarjeta de geek)

---

### Post by sebastianpnts on 2008-03-30
Esto es el script?:?:
root@64bit:/home/carlos/download/XFiDrv_Linux_US-1.04# ./installer
This product only support 64-bit Operating Systems
Setup will now exit
root@64bit:/home/carlos/download/XFiDrv_Linux_US-1.04#

---

### Post by faktorqm on 2008-03-31
[SIZE="4"]para que abris 3 threads preguntando lo mismo?!?!?[/SIZE]

aca tenes el installer parcheado, al parecer tiene un pequeño bug cuando averigua la arquitectura, que en lugar de devolverte algo "esperado" (x86 o algo) devuelve "unknown" y entonces interpreta que no tenes ni 32 ni 64 bits y sale. Para solucionarlo, forcé a que sea 64bits, (vos me dijiste que tenias eso).

SI realmente tenes 64 bits y ubuntu 64 bits, y estas super seguro, instala este instalador parcheado. 

sajnox/marianom:

[http://ubuntuforums.org/showthread.php?t=739840](http://ubuntuforums.org/showthread.php?t=739840)
[http://ubuntuforums.org/showthread.php?t=740729](http://ubuntuforums.org/showthread.php?t=740729)

guias sobre bash scripting:

[http://www.alkon.com.ar/foro/linux.25/467132-guia_bash_mi_mejor_amigo_completa/](http://www.alkon.com.ar/foro/linux.25/467132-guia_bash_mi_mejor_amigo_completa/)
[http://linux.byexamples.com/archives/category/symbol/pipeline/](http://linux.byexamples.com/archives/category/symbol/pipeline/)
[http://www.ss64.com/bash/index.html](http://www.ss64.com/bash/index.html)
[http://www.gnu.org/software/bash/manual/bashref.html](http://www.gnu.org/software/bash/manual/bashref.html)

y asi sucesivamente. Salu2!

---

### Post by sajnox on 2008-03-31
> **faktorqm said:**
> [SIZE="4"]para que abris 3 threads preguntando lo mismo?!?!?[/SIZE]

sajnox/marianom:

[http://ubuntuforums.org/showthread.php?t=739840](http://ubuntuforums.org/showthread.php?t=739840)
[http://ubuntuforums.org/showthread.php?t=740729](http://ubuntuforums.org/showthread.php?t=740729)



Si bien nuestro amigo faktor_qm no es un experto en la suavidad, tiene razon en sus comentarios.

El ultimo thread fue borrado y con el segundo hice un merge con este thread. Gracias faktor por comentarlo.

sebastianpnts no te hagas mucho problema, estas cosas pasan cuando uno es nuevo en el foro, segui posteando tranquilo y cualquier duda que tengas respecto a como postear y otras cosas podes mandarme un mensaje privado que con gusto te doy una mano. 

Comentanos si te sirvio la mano que te dio faktor y no te olvides del click en la medallita de agradecimiento que realmente se lo merece

---

### Post by sebastianpnts on 2008-03-31
hola chicos 
bueno  primero pido disculpas si puse a alguien nervioso no era mi intesion, es q puse otro post porq alguien dijo q no tenia la bola magica para saber mi situacion y como el post quedo muy atras pense q no lo hiban a leer.
segundo gracias a todos por haberme tirado un cable especialmente a faktorqm se JUGO pasando el installer, gracias de verdad. voy a probar a ver si habla la sound blaster luego les comento q paso.

---

