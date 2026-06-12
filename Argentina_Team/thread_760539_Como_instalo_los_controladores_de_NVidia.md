---
title: "Como instalo los controladores de NVidia ??"
date: 2008-04-20
forum: Argentina Team
---

### Post by leonardo83 on 2008-04-20
Que tal gente,como sabran estoy dando los primeros pasos en ubuntu 7.10, desde que se decidio a funcionar bien en mi modesta pc.
Siguiendo con lo mismo, les comento que tengo una placa de video nvidia riva tnt 2, y ubuntu me dice que no la tengo habilitada, me dice que no se encontraron controladores legacy algo (perdon, estoy tipeando esto y no tome nota :( ).
Entonces me fije en posts anteriores y parece que tengo que instalar los controladores de mi placa, que me parece son [COLOR="Magenta"][estos]("http://www.nvidia.com/object/linux_display_x86_96.43.01.html")[/COLOR].
Bueno no se, los baje a mi escritorio y no se como se instala, googleando encontre que puede ser desde consola escribiendo 
```
sudo apt-get install nvidia-glx-legacy
```
pero me dice que no se encontraron esos controladores, no se si se instala asi porque tambien lei que se puede hacer desde synaptic.... estoy bastante mareado como veran :confused:
Tengo los archivos, o sea, mi idea es instalar esto para ver los efectos de las ventanas y despues ver si le puedo instalar beryl o compiz (que creo que ya viene en esta version de ubuntu, no se bien).
Si me pueden ayudar se los agradeceria, saludos.

---

### Post by SLA_leandrin on 2008-04-20
Tenés que abrir la consola en donde bajaste el archivo, y escribir:

```
sudo sh NVIDIA-Linux-x86-96.43.01-pkg1.run
```

Y ahí tendría que instalarse bien...

---

### Post by leonardo83 on 2008-04-20
Gracias man, pero disculpame no te entiendo, como que abra la consola donde baje el archivo?

Lo tengo que guardar en alguna carpeta en especial, home, o alguna otra?

Yo el archivo lo deje en el escritorio, la consola la abro desde un acceso directo que tengo ahi tambien....... :confused:

Lo probe abriendolo ahi y me dice

sh: can't open NVIDIA-Linux-x86-96.43.01-pkg1.run

---

### Post by SLA_leandrin on 2008-04-20
Claro, abrite la consola desde donde sea, y andá al escritorio, o sea:

```
cd ~/Desktop
```

y ahí recién vas a estar en el escritorio, porque cuando abrís la consola seguramente se te abre en el home... y ahí probá tipeando lo que te dije mas arriba.

PD: fijate que el nombre del archivo que bajaste sea igual al que te puse, sino ponele el que corresponde.
Suerte, avisá...

---

### Post by leonardo83 on 2008-04-20
Bueno, sucedio lo siguiente, coloque

cd ~/Escritorio (pequeño detalle, esta en spanish el mio :) )

aparece en el escritorio, aplico lo que me dijiste y se cargan archivos, aparece una pantalla de nvidia, pero antes este codigo:


verifying archive integrity....ok
uncompressing NVIDIa acelerated graphics driver for linux x86 96.43.01 ..............................................................
............................................................ 
ahi aparece la pantalla azul que me dice que desactive primero los x (??) , un par de cosas mas y me dice que no se instalo nada y que me fije el log, que pego a continuacion

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sun Apr 20 13:23:18 2008

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  force tls               : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
WARNING: The NVIDIA RIVA TNT2 Model 64/Model 64 Pro GPU installed in this
         system is supported through the NVIDIA legacy Linux graphics drivers. 
         Please visit [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) for more
         information.  The 96.43.01 NVIDIA Linux graphics driver will ignore
         this GPU.
WARNING: You do not appear to have an NVIDIA GPU supported by the 96.43.01
         NVIDIA Linux graphics driver installed in this system.  For further
         details, please see the appendix SUPPORTED NVIDIA GRAPHICS CHIPS in
         the README available on the Linux driver download page at
         [www.nvidia.com](www.nvidia.com).
-> The file '/tmp/.X0-lock' exists and appears to contain the process ID '8680'
   of a runnning X server.
ERROR: You appear to be running an X server; please exit X before installing. 
       For further details, please see the section INSTALLING THE NVIDIA DRIVER
       in the README available on the Linux driver download page at
       [www.nvidia.com](www.nvidia.com).
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

mmmmm... y ahora? :(

---

### Post by SLA_leandrin on 2008-04-20
Claro, los tenés que instalar sin la interfaz gráfica, o sea sin el servidor X.
Durante el booteo seleccioná la opción de modo texto solamente, y ahi hacés lo que veniamos haciendo. 
Ahí debería poder instalarlo todo bien, después la reiniciás y listo...

---

### Post by leonardo83 on 2008-04-20
ahora que fui a la pagina de nvidia, lei que el archivo que baje no es compatible como me dijeron ahi parece, pero entonces, cual es?
Lei el read me de nvidia y vi que el anterior soporta placas riva tnt, asi que me lo estoy bajando,... despues cuento que paso.
Pero alguna idea de eso de loso X ? espero se instale solo y ya no tenga mas problemas, gracias por la ayuda

EDIT: escribi esto y no vi tu respuesta, espero que desde texta reconozca que tengo ese archivo en el escritorio!!!

Pruebo y posteo, GRACIAS !!!

---

### Post by leonardo83 on 2008-04-20
Paso lo siguiente, cerre la sesion, ingrese de nuevo y en sesion me aparece para elegir:
* ultima sesion
* ejecutar script Xclient
*GNOME
*GNOME a &#341;ueba de fallos
*terminal a prueba de fallos

creo que la que me decis es la ultima, asi que entre de esa manera, hice los mimsos pasos, me aparece el mensaje de NVIDIa que ahora no me dice que el archivo no es compatibel, es decir, es correcto, pero me dice el mensaje
```
ERROR: You appear to be running an X server; please exit X before installing.
For further details, please see the section INSTALLING THE NVIDIA DRIVER
in the README available on the Linux driver download page at
www.nvidia.com.
ERROR: Installation has failed. Please see the file
'/var/log/nvidia-installer.log' for details. You may find suggestions
on fixing installation problems in the README available on the Linux
driver download page at www.nvidia.com.
```

Parece que hay que deshabilitar eso de los X, o sera que elegi mal o hay que deshabilitar antes eso? 
Saludos

---

### Post by sajnox on 2008-04-20
Perdon, pero por que no probas con envy (es un script para instalar los drivers ati y nvidia)

Lo podes bajar de aca [www.albertomilone.com](www.albertomilone.com)

Saludos

---

### Post by ariel on 2008-04-21
> **leonardo83 said:**
> Paso lo siguiente, cerre la sesion, ingrese de nuevo y en sesion me aparece para elegir:
* ultima sesion
* ejecutar script Xclient
*GNOME
*GNOME a &#341;ueba de fallos
*terminal a prueba de fallos

creo que la que me decis es la ultima, asi que entre de esa manera, hice los mimsos pasos, me aparece el mensaje de NVIDIa que ahora no me dice que el archivo no es compatibel, es decir, es correcto, pero me dice el mensaje
```
ERROR: You appear to be running an X server; please exit X before installing.
For further details, please see the section INSTALLING THE NVIDIA DRIVER
in the README available on the Linux driver download page at
www.nvidia.com.
ERROR: Installation has failed. Please see the file
'/var/log/nvidia-installer.log' for details. You may find suggestions
on fixing installation problems in the README available on the Linux
driver download page at www.nvidia.com.
```Parece que hay que deshabilitar eso de los X, o sera que elegi mal o hay que deshabilitar antes eso? 
Saludos

Yo te recomendaria no hacer la instalacion manual, salvo que tengas en claro que es muy posible que algo salga mal y te quedes sin interfaz grafica, y tengas que arreglarlo desde una consola de texto.

Si aun asi queres intentarlo, el problema es que para terminar la sesion de gnome antes de correr el instalador de nvidia tenes que hacer:

Alt-F1 (ir a una consola de texto, y loggearte con tu username)

sudo /etc/init.d/gdm stop

Y despues, ejecuta el instalador de nvidia. Te repito, es muy facil que el proceso salga mal y pierdas tu GUI, y lo tengas que arreglar a mano. 

Ademas noto que estas tratando de instalar un driver de nvidia muy viejo.

---

### Post by faktorqm on 2008-04-22
Hola, yo tengo una gf-4 mx. Olvidate de todo lo que hiciste, lo que tenes que hacer es bajar el envy, e instalar la version 71.XX del driver. Te digo esto por que yo ya probe todo lo que podes llegar a hacer con placas viejas, y encontre la solucion a todos los problemas. Si instalas la version 7X.XX con el envy, podes jugar a los jueguitos (Quake i,ii,iii, unreal tournament, etc) PERO no podes tener compiz. Es decir, podes pero anda leeeeeeeeento como de la rua. Si instalas la version 9X.XX del driver podes tener compiz corriendo bien pero no podes jugar a ningun juego. En windows tampoco, asi que no creas erroneamente (Como yo :P) que en windows andan los juegos con el driver 9X.XX de nvidia. (al menos es mi caso digamos)

Ahora bien, te vas a acordar de mi familia cuando actualices el kernel y no puedas ver nada en tu escritorio... Lo que tenes que hacer cuando actualizas el kernel, es esperar a que te tire el error, ir a la consola, hacer 

```
sudo nano /etc/X11/xorg.conf
```

Ir a la linea donde dice "driver", sacar "nvidia" y poner "vesa". Grabar y salir. Escribir 

```
sudo /etc/init.d/gdm restart
```

Ahi te levanta "feo" sin drivers ni nada, corres de vuelta el envy como si nunca hubieras instalado nada y listo!!!
Espero no haber perdido mañanas, tardes y noches enteras y que me digas que te sirvio. Salu2!!

---

### Post by leonardo83 on 2008-04-27
Primero que nada disculpen por la demora pero tuve parcial en la facu y no tuve tiempo de "jugar" un rato con linux ni postear aca .
Lescomento que descargue el archivo de la pagina de NVidia pero segui unos pasos que vi por internet y pude instalar los controladores!!!

Paso a indicarles lo que hice:

* fui a origenes de software y vi que no estaba nada tildado asi que tilde TODOS, todas las fuenets descargables de internet
* entonces ipso facto, fui de nuevo a activar la placa desde elo gestor de controladores, como estaba conectado a internet se descargo solito el archivo y para terminar me pidio reiniciar
* al reiniciar mi pantalla se ve medio rara, es decir, se ve muy grande pero no lo puedo configurar mas pues desaparecieron pantallas como 1024 x etc, solo tengo dos pero no problem! ah y un mensaje en la barra de gnome que dice "controlador restringido activado" y me aparace que el controlador de nvidia esta activoooo

Peeeeero (siempre hay un pero) si por ejemplo desde efectos eligo cualquiera, sea normal o extra, me aparece el mensaje
Code:

desktop effects could not be loaded

Que pasa? pense que activando esto ya estaria, porque si instalo beryl o compiz lo voy a tener que activar de ahi, falta hacer algo?

Bueno gracias, espero me ayuden, como dije me demore y recien este finde volvi a atacar con ubuntu, que se me va a demorar unos meses en que lo tenga todo configurado como quiera, pero no importa, me gusta jajaj
Saludos

---

