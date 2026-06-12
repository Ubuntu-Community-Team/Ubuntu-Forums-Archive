---
title: "Driver sound Toshiba Satellite A205 S4617"
date: 2008-04-02
forum: Argentina Team
---

### Post by santisantermer on 2008-04-02
Hi, I've just installed ubuntu 7.10 in my laptop Toshiba Satellite A205 S4617  but I've no sound. It´s realteck high definition Audio 6.0.1.5371, the brand is Harman/Kardon.
Your help is appreciated!

---

### Post by Hei Ku on 2008-04-02
Por empezar, postea que te sale al poner lspci

EN CASTELLANO, que este es el foro argentino. :D

---

### Post by santisantermer on 2008-04-04
Hola, muchas gracias por la ayuda.
La redacción en inglés se debe a que cuando entré al foro me redireccionó a uno en el cual todos los mensajes estaban escritos en ese idioma. Por otra parte tuve que crear nuevamente el usuario, por lo que, obviamente pensé que me habían linkeado a algún foro de habla inglesa. Pero me alegra enormemente ver que hay un foro en español, eso facilita mucho las cosas.
Tengo un problemita para ejecutar el comando que me sugeriste y es que luego de instalar ubuntu tuve que reinstalar vista y me desactivo la opcion de buteo en la que elegía entre ambos sistemas operativos, entrando por default en windows. Tenés idea de cómo puedo solucionar eso?
De nuevo, muchas gracias por tu ayuda,
Santiago.

---

### Post by atatiducken on 2008-04-04
busca en el foro o en san google "reinstalar grub" o "recuperar grub" hay varios posts sobre ese tema, saludos

---

### Post by sajnox on 2008-04-04
La solucion para tu problema la podes encontrar aca: [http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB](http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB)

La podes encontrar facilmente escrbiendo en google "ubuntu como recuperar el grub"

Contanos como te funciono

---

### Post by santisantermer on 2008-04-08
Hola, muchas gracias. Ya pude solucionar el tema del grub y butea perfectamente.
Ahora si pude aplicar el comando lspci y me salio el texto al pie.
Un abrazo,
Santiago


santiago@santiago-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
07:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
07:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
07:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
07:06.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
santiago@santiago-laptop:~$

---

### Post by Hei Ku on 2008-04-08
Encontre este post, quizas te sirva:

[http://ubuntuforums.org/showthread.php?t=539595](http://ubuntuforums.org/showthread.php?t=539595)

---

### Post by santisantermer on 2008-04-09
Hola Hei Ku!
Pude llegar hasta el paso "code". Despues me apareció un mensaje de error. No sè si escribì mal algo. 
Querìa aprovechar para agredecerte por la orientaciòn y la ayuda que me estás dando, tanto en esta como en otras consultas. Si seguimos asì pronto voy a poder manejarme 100% con ubuntu.
Un abrazo,
Santiago.

PD: esto es lo que escribì y lo que me saliò:

santiago@santiago-laptop:~$ sudo apt-get install build-essential ncurses-dev gettext
[sudo] password for santiago:
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Nota, seleccionando libncurses5-dev en lugar de ncurses-dev
gettext ya está en su versión más reciente.
fijado gettext como instalado manualmente.
Se instalarán los siguientes paquetes extras:
  g++ g++-4.1 libc6-dev libncurses5-dev libstdc++6-4.1-dev linux-libc-dev
Paquetes sugeridos:
  g++-multilib g++-4.1-multilib gcc-4.1-doc glibc-doc manpages-dev
  libstdc++6-4.1-doc
Se instalarán los siguientes paquetes NUEVOS:
  build-essential g++ g++-4.1 libc6-dev libncurses5-dev libstdc++6-4.1-dev
  linux-libc-dev
0 actualizados, 7 se instalarán, 0 para eliminar y 0 no actualizados.
Se necesita descargar 5397kB/9133kB de archivos.
Se utilizarán 37,3MB de espacio de disco adicional después de desempaquetar.
¿Desea continuar [S/n]? s
Cambio de medio: Por favor inserte el disco etiquetado
 'Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)'
en la unidad '/cdrom/' y presione Intro

Des:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main linux-libc-dev 2.6.22-14.52 [653kB]
Des:2 [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) gutsy-updates/main libc6-dev 2.6.1-1ubuntu10 [3287kB]
Des:3 [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) gutsy/main libncurses5-dev 5.6+20070716-1ubuntu3 [1456kB]
Descargados 5397kB en 59s (91,2kB/s)                                           
Seleccionando el paquete linux-libc-dev previamente no seleccionado.
(Leyendo la base de datos ...  
113308 ficheros y directorios instalados actualmente.)
Desempaquetando linux-libc-dev (de .../linux-libc-dev_2.6.22-14.52_i386.deb) ...
Seleccionando el paquete libc6-dev previamente no seleccionado.
Desempaquetando libc6-dev (de .../libc6-dev_2.6.1-1ubuntu10_i386.deb) ...
Seleccionando el paquete libstdc++6-4.1-dev previamente no seleccionado.
Desempaquetando libstdc++6-4.1-dev (de .../libstdc++6-4.1-dev_4.1.2-16ubuntu2_i386.deb) ...
Seleccionando el paquete g++-4.1 previamente no seleccionado.
Desempaquetando g++-4.1 (de .../g++-4.1_4.1.2-16ubuntu2_i386.deb) ...
Seleccionando el paquete g++ previamente no seleccionado.
Desempaquetando g++ (de .../g++_4.1.2-9ubuntu2_i386.deb) ...
Seleccionando el paquete build-essential previamente no seleccionado.
Desempaquetando build-essential (de .../build-essential_11.3ubuntu1_i386.deb) ...
Seleccionando el paquete libncurses5-dev previamente no seleccionado.
Desempaquetando libncurses5-dev (de .../libncurses5-dev_5.6+20070716-1ubuntu3_i386.deb) ...
Configurando linux-libc-dev (2.6.22-14.52) ...
Configurando libc6-dev (2.6.1-1ubuntu10) ...
Configurando libncurses5-dev (5.6+20070716-1ubuntu3) ...
Configurando libstdc++6-4.1-dev (4.1.2-16ubuntu2) ...
Configurando g++-4.1 (4.1.2-16ubuntu2) ...
Configurando g++ (4:4.1.2-9ubuntu2) ...

Configurando build-essential (11.3ubuntu1) ...
santiago@santiago-laptop:~$ udo apt-get install linux-headers-`uname -r`
El programa «udo» no está instalado actualmente.  Puede instalarlo escribiendo:
sudo apt-get install udo
bash: udo: orden no encontrada
santiago@santiago-laptop:~$ sudo apt-get install linux-headers-`uname -r`
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
linux-headers-2.6.22-14-generic ya está en su versión más reciente.
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.
santiago@santiago-laptop:~$ sudo mkdir -p /usr/src/alsa
santiago@santiago-laptop:~$ cd /usr/src/alsa
santiago@santiago-laptop:/usr/src/alsa$ sudo cp ~/downloads/alsa* .
cp: no se puede efectuar `stat' sobre `/home/santiago/downloads/alsa*': No existe el fichero ó directorio
santiago@santiago-laptop:/usr/src/alsa$ sudo cp ~/downloads/alsa*
cp: falta el operando archivo de destino después de `/home/santiago/downloads/alsa*'
Pruebe `cp --help' para más información.
santiago@santiago-laptop:/usr/src/alsa$ sudo cp ~/downloads/alsa* .
cp: no se puede efectuar `stat' sobre `/home/santiago/downloads/alsa*': No existe el fichero ó directorio
santiago@santiago-laptop:/usr/src/alsa$ 
santiago@santiago-laptop:/usr/src/alsa$

---

### Post by Hei Ku on 2008-04-09
santiago@santiago-laptop:/usr/src/alsa$ sudo cp ~/downloads/alsa* .

Este es el paso donde fallo. Basicamente porque no encuentra los archivos que deberias haber bajado. Supongo que los debes haber bajado con firefox, y entonces quedaron en tu escritorio, no?

Deberias hacer lo siguiente:
cd /usr/src/alsa
cp ~/Desktop/<nombre del archivo> .

donde reemplazas <nombre del archivo> por el nombre del primer archivo que bajaste. repeti el mismo paso por cada archivo.
despues seguis con los pasos de tar.

---

### Post by santisantermer on 2008-04-09
Hei Ku: pude pasar al siguiente paso. Con desktop no funcionò, pero en propiedades del archivo decìa que estaba en la carpeta temp.
Ahora me apareció este error. Calculo que no reemplace correctamente algo.
Muchas gracias,
Santiago.

PD: al principio, cometì algunos errores al armar el comando, quizàs sea eso, por eso te transcripo todo.

santiago@santiago-laptop:~$ sudo cp ~/temp/alsa* .
cp: no se puede efectuar `stat' sobre `/home/santiago/temp/alsa*': No existe el fichero ó directorio
santiago@santiago-laptop:~$ sudo cp ~/tmp/alsa-driver-1.0.14.tar.bz2> .
bash: .: Es un directorio
santiago@santiago-laptop:~$ cp ~/tmp/alsa-lib-1.0.14a.tar.bz22> .
bash: .: Es un directorio
santiago@santiago-laptop:~$ cp ~/tmp/alsa-utils-1.0.14.tar.bz2> .
bash: .: Es un directorio
santiago@santiago-laptop:~$ sudo tar xjf alsa-driver-1.0.14.tar.bz2
tar: alsa-driver-1.0.14.tar.bz2: No se puede open: No existe el fichero ó directorio
tar: El error no es recuperable: salida ahora
tar: Child returned status 2
tar: Salida con error demorada desde errores anteriores
santiago@santiago-laptop:~$ cd /usr/src/alsa
santiago@santiago-laptop:/usr/src/alsa$  sudo cp ~/tmp/alsa-driver-1.0.14.tar.bz2> .
bash: .: Es un directorio
santiago@santiago-laptop:/usr/src/alsa$  cp ~/tmp/alsa-driver-1.0.14.tar.bz2> .
bash: .: Es un directorio
santiago@santiago-laptop:/usr/src/alsa$ cp ~/tmp/alsa-lib-1.0.14a.tar.bz22> .
bash: .: Es un directorio
santiago@santiago-laptop:/usr/src/alsa$  cp ~/tmp/alsa-utils-1.0.14.tar.bz2> .
bash: .: Es un directorio
santiago@santiago-laptop:/usr/src/alsa$ sudo tar xjf alsa-driver-1.0.14.tar.bz2
tar: alsa-driver-1.0.14.tar.bz2: No se puede open: No existe el fichero ó directorio
tar: El error no es recuperable: salida ahora
tar: Child returned status 2
tar: Salida con error demorada desde errores anteriores
santiago@santiago-laptop:/usr/src/alsa$ cp ~/tmp/alsa-driver-1.0.14.tar.bz2> .
bash: .: Es un directorio
santiago@santiago-laptop:/usr/src/alsa$ sudo tar xjf alsa-driver-1.0.14.tar.bz2
tar: alsa-driver-1.0.14.tar.bz2: No se puede open: No existe el fichero ó directorio
tar: El error no es recuperable: salida ahora
tar: Child returned status 2
tar: Salida con error demorada desde errores anteriores
santiago@santiago-laptop:/usr/src/alsa$

---

### Post by Hei Ku on 2008-04-09
al final del nombre del archivo dejaste >
como no encuentra el nombre del archivo, el resto falla. volve a copiar los archivos con el nombre bien.

---

### Post by santisantermer on 2008-04-09
Le saqué el simbolo que estaba de más, pero esta vez no encuentra el archivo.
Me aparece esto:

santiago@santiago-laptop:~$ cd /usr/src/alsa
santiago@santiago-laptop:/usr/src/alsa$ cp ~/tmp/alsa-driver-1.0.14.tar.bz2 .
cp: no se puede efectuar `stat' sobre `/home/santiago/tmp/alsa-driver-1.0.14.tar.bz2': No existe el fichero ó directorio
santiago@santiago-laptop:/usr/src/alsa$ cp ~/tmp/alsa-lib-1.0.14a.tar.bz22 .
cp: no se puede efectuar `stat' sobre `/home/santiago/tmp/alsa-lib-1.0.14a.tar.bz22': No existe el fichero ó directorio
santiago@santiago-laptop:/usr/src/alsa$ cp ~/tmp/alsa-utils-1.0.14.tar.bz2 .
cp: no se puede efectuar `stat' sobre `/home/santiago/tmp/alsa-utils-1.0.14.tar.bz2': No existe el fichero ó directorio
santiago@santiago-laptop:/usr/src/alsa$ sudo tar xjf alsa-driver-1.0.14.tar.bz2
[sudo] password for santiago:
tar: alsa-driver-1.0.14.tar.bz2: No se puede open: No existe el fichero ó directorio
tar: El error no es recuperable: salida ahora
tar: Child returned status 2
tar: Salida con error demorada desde errores 

Gracias por todo,
Santiago.

---

### Post by Hei Ku on 2008-04-09
seguro que los archivos están ahi? Abri con Nautilius o Konqueror y fijate que realmente esten en esa carpeta.

---

### Post by santisantermer on 2008-04-09
Hei Ku, disculpa mi ignorancia, pero no puedo encontrar Nautilius ni Konqueror. De dónde los abro?

---

### Post by Hei Ku on 2008-04-09
Creo que en Gnome tenes una carpeta o menu llamado Lugares, eso te abre el Nautilius, que es un explorador de carpetas. Alguien de gnome le da una mano con eso, porfi?

Si no puedes, lo vemos de otra manera, no hay problema.

---

### Post by santisantermer on 2008-04-09
Ok, ahi logre instalar konqueror y no vi el archivo en esa carpeta
Voy a probar de repetir el proceso desde el principio a ver que pasa.
Saludos,
Santiago.

---

### Post by santisantermer on 2008-04-09
Volví a hacer todo desde el paso 0 creando la carpeta indicada y corrió toda la instalaciòn. Pero no sale sonido. Incluso el controlador de volumen (la perilla que tienen las toshiba) hacìa aparecer en pantalla como se modificaba el volumen pero ahora no lo hace. Me aparecen carteles diciendo que no hay un disposito asociado al controlador. Ademàs en la barra de tareas, el icono con forma de parlante esta con una cruz roja. Le pongo silenciar/desilenciar pero nada pasa.
Que puedo hacer?
Saludos,
Santiago.

PD: en el texto que habia que agregar al final de la instalacion en la ventana que se abrìa decia "lenovo" y yo tengo una toshiba, tendra algo que ver?

---

### Post by Hei Ku on 2008-04-09
en la configuracion de sistema en la parte de sonido que te aparece en hardware?

en el dispositivo de sonido, ponele autodetectar

---

### Post by santisantermer on 2008-04-09
En sistema/preferencias/sonido/dispositivos me aparece ALSA, OSS, EDS y autodetectar. Estaba en esta ùltima opciòn. Lo cambie a ALSA y lo volvi a poner en autodetectar pero no paso nada.

---

### Post by sajnox on 2008-04-10
Se que llego tarde, pero como acabo de instalar ubuntu en una toshiba el problema que tuve con el sonido es que era muy bajo y lo pude solucionar MUY facilmente.

Por las dudas pone todo el volumen al maximo y comentanos si escuchas algo

---

### Post by santisantermer on 2008-04-10
Antes de escribir al foro puse al maximo el volumen tanto desde el hard como del soft.
Igualmente gracias.
Santiago.

---

### Post by Hei Ku on 2008-04-10
ahi un lugar desde el cual no probaste seguramente.

en una terminal, pone:

alsamixer

ahi tenes la posta en controles de sonido.

---

### Post by santisantermer on 2008-04-10
me tiro esto:

santiago@santiago-laptop:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device
santiago@santiago-laptop:~$ 

En cuanto al lector de huellas digitales, creo que faltaba solo un paso con las indicaciones que me diste. No se si seguir las otras vias que sugieron otras personas o terminar todo lo que habiamos hecho.

Saludos.

---

### Post by Hei Ku on 2008-04-10
estas seguro que instalo bien el driver?
podes repetir el proceso y postear aca el texto?

---

### Post by santisantermer on 2008-04-11
Lo volví a repetir pero no pasó nada nuevo. Acá te paso el texto de la terminal.
Muchas gracias,
Santiago.

/usr/bin/install -c .libs/aserver /usr/bin/aserver
make[2]: No se hace nada para `install-data-am'.
make[2]: se sale del directorio `/usr/src/alsa/alsa-lib-1.0.14a/aserver'
make[1]: se sale del directorio `/usr/src/alsa/alsa-lib-1.0.14a/aserver'
Making install in alsalisp
make[1]: se ingresa al directorio `/usr/src/alsa/alsa-lib-1.0.14a/alsalisp'
make[2]: se ingresa al directorio `/usr/src/alsa/alsa-lib-1.0.14a/alsalisp'
make[2]: No se hace nada para `install-exec-am'.
make[2]: No se hace nada para `install-data-am'.
make[2]: se sale del directorio `/usr/src/alsa/alsa-lib-1.0.14a/alsalisp'
make[1]: se sale del directorio `/usr/src/alsa/alsa-lib-1.0.14a/alsalisp'
Making install in test
make[1]: se ingresa al directorio `/usr/src/alsa/alsa-lib-1.0.14a/test'
make[2]: se ingresa al directorio `/usr/src/alsa/alsa-lib-1.0.14a/test'
make[2]: No se hace nada para `install-exec-am'.
make[2]: No se hace nada para `install-data-am'.
make[2]: se sale del directorio `/usr/src/alsa/alsa-lib-1.0.14a/test'
make[1]: se sale del directorio `/usr/src/alsa/alsa-lib-1.0.14a/test'
Making install in utils
make[1]: se ingresa al directorio `/usr/src/alsa/alsa-lib-1.0.14a/utils'
make[2]: se ingresa al directorio `/usr/src/alsa/alsa-lib-1.0.14a/utils'
make[2]: No se hace nada para `install-exec-am'.
test -z "/usr/share/aclocal" || mkdir -p -- "/usr/share/aclocal"
 /usr/bin/install -c -m 644 'alsa.m4' '/usr/share/aclocal/alsa.m4'
test -z "/usr/lib/pkgconfig" || mkdir -p -- "/usr/lib/pkgconfig"
 /usr/bin/install -c -m 644 'alsa.pc' '/usr/lib/pkgconfig/alsa.pc'
make[2]: se sale del directorio `/usr/src/alsa/alsa-lib-1.0.14a/utils'
make[1]: se sale del directorio `/usr/src/alsa/alsa-lib-1.0.14a/utils'
make[1]: se ingresa al directorio `/usr/src/alsa/alsa-lib-1.0.14a'
make[2]: se ingresa al directorio `/usr/src/alsa/alsa-lib-1.0.14a'
make[2]: No se hace nada para `install-exec-am'.
make[2]: No se hace nada para `install-data-am'.
make[2]: se sale del directorio `/usr/src/alsa/alsa-lib-1.0.14a'
make[1]: se sale del directorio `/usr/src/alsa/alsa-lib-1.0.14a'
santiago@santiago-laptop:/usr/src/alsa/alsa-lib-1.0.14a$ cd ../alsa-utils-1.0.14
santiago@santiago-laptop:/usr/src/alsa/alsa-utils-1.0.14$ sudo ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for cross-compiler... gcc
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for ALSA CFLAGS... 
checking for ALSA LDFLAGS...  -lasound -lm -ldl -lpthread
checking for libasound headers version >= 1.0.12... found.
checking for snd_ctl_open in -lasound... yes
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for initscr in -lncurses... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for _LARGE_FILES value needed for large files... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating alsactl/Makefile
config.status: creating alsamixer/Makefile
config.status: creating amidi/Makefile
config.status: creating amixer/Makefile
config.status: creating m4/Makefile
config.status: creating po/Makefile.in
config.status: creating alsaconf/alsaconf
config.status: creating alsaconf/Makefile
config.status: creating alsaconf/po/Makefile
config.status: WARNING:  alsaconf/po/Makefile.in seems to ignore the --datarootdir setting
config.status: creating aplay/Makefile
config.status: creating include/Makefile
config.status: creating iecset/Makefile
config.status: creating utils/Makefile
config.status: creating utils/alsa-utils.spec
config.status: creating seq/Makefile
config.status: creating seq/aconnect/Makefile
config.status: creating seq/aplaymidi/Makefile
config.status: creating seq/aseqdump/Makefile
config.status: creating seq/aseqnet/Makefile
config.status: creating speaker-test/Makefile
config.status: creating speaker-test/samples/Makefile
config.status: creating include/aconfig.h
config.status: include/aconfig.h is unchanged
config.status: executing po-directories commands
config.status: creating po/POTFILES
config.status: creating po/Makefile
config.status: executing depfiles commands
santiago@santiago-laptop:/usr/src/alsa/alsa-utils-1.0.14$ sudo make
Making all in include
make[1]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/include'
make  all-am
make[2]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/include'
make[2]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/include'
make[1]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/include'
Making all in alsactl
make[1]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/alsactl'
if gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -MT alsactl.o -MD -MP -MF ".deps/alsactl.Tpo" -c -o alsactl.o alsactl.c; \
        then mv -f ".deps/alsactl.Tpo" ".deps/alsactl.Po"; else rm -f ".deps/alsactl.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -MT state.o -MD -MP -MF ".deps/state.Tpo" -c -o state.o state.c; \
        then mv -f ".deps/state.Tpo" ".deps/state.Po"; else rm -f ".deps/state.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -MT names.o -MD -MP -MF ".deps/names.Tpo" -c -o names.o names.c; \
        then mv -f ".deps/names.Tpo" ".deps/names.Po"; else rm -f ".deps/names.Tpo"; exit 1; fi
gcc  -g -O2   -o alsactl  alsactl.o state.o names.o  -lasound -lm -ldl -lpthread
make[1]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/alsactl'
Making all in alsaconf
make[1]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/alsaconf'
Making all in po
make[2]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/alsaconf/po'
make[2]: No se hace nada para `all'.
make[2]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/alsaconf/po'
make[2]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/alsaconf'
make[2]: No se hace nada para `all-am'.
make[2]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/alsaconf'
make[1]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/alsaconf'
Making all in alsamixer
make[1]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/alsamixer'
if gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -MT alsamixer.o -MD -MP -MF ".deps/alsamixer.Tpo" -c -o alsamixer.o alsamixer.c; \
        then mv -f ".deps/alsamixer.Tpo" ".deps/alsamixer.Po"; else rm -f ".deps/alsamixer.Tpo"; exit 1; fi
gcc  -g -O2   -o alsamixer  alsamixer.o -lncurses -lasound -lm -ldl -lpthread
make[1]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/alsamixer'
Making all in amidi
make[1]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/amidi'
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT amidi.o -MD -MP -MF ".deps/amidi.Tpo" -c -o amidi.o amidi.c; \
        then mv -f ".deps/amidi.Tpo" ".deps/amidi.Po"; else rm -f ".deps/amidi.Tpo"; exit 1; fi
gcc  -g -O2   -o amidi  amidi.o  -lasound -lm -ldl -lpthread
make[1]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/amidi'
Making all in amixer
make[1]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/amixer'
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT amixer.o -MD -MP -MF ".deps/amixer.Tpo" -c -o amixer.o amixer.c; \
        then mv -f ".deps/amixer.Tpo" ".deps/amixer.Po"; else rm -f ".deps/amixer.Tpo"; exit 1; fi
gcc  -g -O2   -o amixer  amixer.o -lm -lasound -lm -ldl -lpthread
make[1]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/amixer'
Making all in aplay
make[1]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/aplay'
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT aplay.o -MD -MP -MF ".deps/aplay.Tpo" -c -o aplay.o aplay.c; \
        then mv -f ".deps/aplay.Tpo" ".deps/aplay.Po"; else rm -f ".deps/aplay.Tpo"; exit 1; fi
gcc  -g -O2   -o aplay  aplay.o -lasound  -lasound -lm -ldl -lpthread
make[1]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/aplay'
Making all in iecset
make[1]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/iecset'
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT iecset.o -MD -MP -MF ".deps/iecset.Tpo" -c -o iecset.o iecset.c; \
        then mv -f ".deps/iecset.Tpo" ".deps/iecset.Po"; else rm -f ".deps/iecset.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT iecbits.o -MD -MP -MF ".deps/iecbits.Tpo" -c -o iecbits.o iecbits.c; \
        then mv -f ".deps/iecbits.Tpo" ".deps/iecbits.Po"; else rm -f ".deps/iecbits.Tpo"; exit 1; fi
gcc  -g -O2   -o iecset  iecset.o iecbits.o -lm -lasound -lm -ldl -lpthread
make[1]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/iecset'
Making all in seq
make[1]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/seq'
Making all in aconnect
make[2]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/seq/aconnect'
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aconnect.o -MD -MP -MF ".deps/aconnect.Tpo" -c -o aconnect.o aconnect.c; \
        then mv -f ".deps/aconnect.Tpo" ".deps/aconnect.Po"; else rm -f ".deps/aconnect.Tpo"; exit 1; fi
gcc  -g -O2   -o aconnect  aconnect.o  -lasound -lm -ldl -lpthread
make[2]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/seq/aconnect'
Making all in aplaymidi
make[2]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/seq/aplaymidi'
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aplaymidi.o -MD -MP -MF ".deps/aplaymidi.Tpo" -c -o aplaymidi.o aplaymidi.c; \
        then mv -f ".deps/aplaymidi.Tpo" ".deps/aplaymidi.Po"; else rm -f ".deps/aplaymidi.Tpo"; exit 1; fi
gcc  -g -O2   -o aplaymidi  aplaymidi.o  -lasound -lm -ldl -lpthread
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT arecordmidi.o -MD -MP -MF ".deps/arecordmidi.Tpo" -c -o arecordmidi.o arecordmidi.c; \
        then mv -f ".deps/arecordmidi.Tpo" ".deps/arecordmidi.Po"; else rm -f ".deps/arecordmidi.Tpo"; exit 1; fi
gcc  -g -O2   -o arecordmidi  arecordmidi.o  -lasound -lm -ldl -lpthread
make[2]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/seq/aplaymidi'
Making all in aseqdump
make[2]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/seq/aseqdump'
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aseqdump.o -MD -MP -MF ".deps/aseqdump.Tpo" -c -o aseqdump.o aseqdump.c; \
        then mv -f ".deps/aseqdump.Tpo" ".deps/aseqdump.Po"; else rm -f ".deps/aseqdump.Tpo"; exit 1; fi
gcc  -g -O2   -o aseqdump  aseqdump.o  -lasound -lm -ldl -lpthread
make[2]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/seq/aseqdump'
Making all in aseqnet
make[2]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/seq/aseqnet'
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aseqnet.o -MD -MP -MF ".deps/aseqnet.Tpo" -c -o aseqnet.o aseqnet.c; \
        then mv -f ".deps/aseqnet.Tpo" ".deps/aseqnet.Po"; else rm -f ".deps/aseqnet.Tpo"; exit 1; fi
gcc  -g -O2   -o aseqnet  aseqnet.o  -lasound -lm -ldl -lpthread
make[2]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/seq/aseqnet'
make[2]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/seq'
make[2]: No se hace nada para `all-am'.
make[2]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/seq'
make[1]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/seq'
Making all in speaker-test
make[1]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/speaker-test'
Making all in samples
make[2]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/speaker-test/samples'
make[2]: No se hace nada para `all'.
make[2]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/speaker-test/samples'
make[2]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/speaker-test'
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT speaker-test.o -MD -MP -MF ".deps/speaker-test.Tpo" -c -o speaker-test.o speaker-test.c; \
        then mv -f ".deps/speaker-test.Tpo" ".deps/speaker-test.Po"; else rm -f ".deps/speaker-test.Tpo"; exit 1; fi
gcc  -g -O2   -o speaker-test  speaker-test.o pink.o  -lasound -lm -ldl -lpthread
make[2]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/speaker-test'
make[1]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/speaker-test'
Making all in utils
make[1]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/utils'
make[1]: No se hace nada para `all'.
make[1]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/utils'
Making all in m4
make[1]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/m4'
make[1]: No se hace nada para `all'.
make[1]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/m4'
Making all in po
make[1]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/po'
make[1]: No se hace nada para `all'.
make[1]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/po'
make[1]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14'
make[1]: No se hace nada para `all-am'.
make[1]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14'
santiago@santiago-laptop:/usr/src/alsa/alsa-utils-1.0.14$ sudo make install
Making install in include
make[1]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/include'
make[2]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/include'
make[2]: No se hace nada para `install-exec-am'.
make[2]: No se hace nada para `install-data-am'.
make[2]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/include'
make[1]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/include'
Making install in alsactl
make[1]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/alsactl'
make[2]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/alsactl'
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"
  /usr/bin/install -c 'alsactl' '/usr/sbin/alsactl'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './alsactl.1' '/usr/share/man/man1/alsactl.1'
make[2]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/alsactl'
make[1]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/alsactl'
Making install in alsaconf
make[1]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/alsaconf'
Making install in po
make[2]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/alsaconf/po'
mkdir -p -- /usr/share
make[2]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/alsaconf/po'
make[2]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/alsaconf'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/alsaconf'
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"
 /usr/bin/install -c 'alsaconf' '/usr/sbin/alsaconf'
 /usr/bin/install -c -m 644 alsaconf.8 /usr/share/man/man8/alsaconf.8
 /usr/bin/install -c -m 644 alsaconf.fr.8 /usr/share/man/fr/man8/alsaconf.8
make[3]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/alsaconf'
make[2]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/alsaconf'
make[1]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/alsaconf'
Making install in alsamixer
make[1]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/alsamixer'
make[2]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/alsamixer'
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'alsamixer' '/usr/bin/alsamixer'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './alsamixer.1' '/usr/share/man/man1/alsamixer.1'
make[2]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/alsamixer'
make[1]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/alsamixer'
Making install in amidi
make[1]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/amidi'
make[2]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/amidi'
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'amidi' '/usr/bin/amidi'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './amidi.1' '/usr/share/man/man1/amidi.1'
make[2]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/amidi'
make[1]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/amidi'
Making install in amixer
make[1]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/amixer'
make[2]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/amixer'
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'amixer' '/usr/bin/amixer'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './amixer.1' '/usr/share/man/man1/amixer.1'
make[2]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/amixer'
make[1]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/amixer'
Making install in aplay
make[1]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/aplay'
make[2]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/aplay'
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aplay' '/usr/bin/aplay'
make  install-exec-hook
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/aplay'
rm -f /usr/bin/arecord
(cd /usr/bin && ln -s aplay arecord)
make[3]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/aplay'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aplay.1' '/usr/share/man/man1/aplay.1'
 /usr/bin/install -c -m 644 './arecord.1' '/usr/share/man/man1/arecord.1'
make  install-data-hook
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/aplay'
rm -f /usr/share/man/man1/arecord.1
(cd /usr/share/man/man1 && ln -s aplay.1 arecord.1)
make[3]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/aplay'
make[2]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/aplay'
make[1]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/aplay'
Making install in iecset
make[1]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/iecset'
make[2]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/iecset'
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'iecset' '/usr/bin/iecset'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './iecset.1' '/usr/share/man/man1/iecset.1'
make[2]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/iecset'
make[1]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/iecset'
Making install in seq
make[1]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/seq'
Making install in aconnect
make[2]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/seq/aconnect'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/seq/aconnect'
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aconnect' '/usr/bin/aconnect'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aconnect.1' '/usr/share/man/man1/aconnect.1'
make[3]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/seq/aconnect'
make[2]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/seq/aconnect'
Making install in aplaymidi
make[2]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/seq/aplaymidi'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/seq/aplaymidi'
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aplaymidi' '/usr/bin/aplaymidi'
  /usr/bin/install -c 'arecordmidi' '/usr/bin/arecordmidi'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aplaymidi.1' '/usr/share/man/man1/aplaymidi.1'
 /usr/bin/install -c -m 644 './arecordmidi.1' '/usr/share/man/man1/arecordmidi.1'
make[3]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/seq/aplaymidi'
make[2]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/seq/aplaymidi'
Making install in aseqdump
make[2]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/seq/aseqdump'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/seq/aseqdump'
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aseqdump' '/usr/bin/aseqdump'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aseqdump.1' '/usr/share/man/man1/aseqdump.1'
make[3]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/seq/aseqdump'
make[2]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/seq/aseqdump'
Making install in aseqnet
make[2]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/seq/aseqnet'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/seq/aseqnet'
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aseqnet' '/usr/bin/aseqnet'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aseqnet.1' '/usr/share/man/man1/aseqnet.1'
make[3]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/seq/aseqnet'
make[2]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/seq/aseqnet'
make[2]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/seq'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/seq'
make[3]: No se hace nada para `install-exec-am'.
make[3]: No se hace nada para `install-data-am'.
make[3]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/seq'
make[2]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/seq'
make[1]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/seq'
Making install in speaker-test
make[1]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/speaker-test'
Making install in samples
make[2]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/speaker-test/samples'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/speaker-test/samples'
make[3]: No se hace nada para `install-exec-am'.
test -z "/usr/share/alsa/speaker-test" || mkdir -p -- "/usr/share/alsa/speaker-test"
 /usr/bin/install -c -m 644 'sample_map.csv' '/usr/share/alsa/speaker-test/sample_map.csv'
test -z "/usr/share/sounds/alsa" || mkdir -p -- "/usr/share/sounds/alsa"
 /usr/bin/install -c -m 644 'Front_Left.wav' '/usr/share/sounds/alsa/Front_Left.wav'
 /usr/bin/install -c -m 644 'Rear_Center.wav' '/usr/share/sounds/alsa/Rear_Center.wav'
 /usr/bin/install -c -m 644 'Rear_Right.wav' '/usr/share/sounds/alsa/Rear_Right.wav'
 /usr/bin/install -c -m 644 'Side_Right.wav' '/usr/share/sounds/alsa/Side_Right.wav'
 /usr/bin/install -c -m 644 'Front_Center.wav' '/usr/share/sounds/alsa/Front_Center.wav'
 /usr/bin/install -c -m 644 'Front_Right.wav' '/usr/share/sounds/alsa/Front_Right.wav'
 /usr/bin/install -c -m 644 'Noise.wav' '/usr/share/sounds/alsa/Noise.wav'
 /usr/bin/install -c -m 644 'Rear_Left.wav' '/usr/share/sounds/alsa/Rear_Left.wav'
 /usr/bin/install -c -m 644 'Side_Left.wav' '/usr/share/sounds/alsa/Side_Left.wav'
make[3]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/speaker-test/samples'
make[2]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/speaker-test/samples'
make[2]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/speaker-test'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/speaker-test'
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'speaker-test' '/usr/bin/speaker-test'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './speaker-test.1' '/usr/share/man/man1/speaker-test.1'
make[3]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/speaker-test'
make[2]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/speaker-test'
make[1]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/speaker-test'
Making install in utils
make[1]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/utils'
make[2]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/utils'
make[2]: No se hace nada para `install-exec-am'.
make[2]: No se hace nada para `install-data-am'.
make[2]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/utils'
make[1]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/utils'
Making install in m4
make[1]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/m4'
make[2]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/m4'
make[2]: No se hace nada para `install-exec-am'.
make[2]: No se hace nada para `install-data-am'.
make[2]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/m4'
make[1]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/m4'
Making install in po
make[1]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14/po'
mkdir -p -- /usr/share
installing ja.gmo as /usr/share/locale/ja/LC_MESSAGES/alsa-utils.mo
if test "alsa-utils" = "gettext-tools"; then \
          mkdir -p -- /usr/share/gettext/po; \
          for file in Makefile.in.in remove-potcdate.sin quot.sed boldquot.sed [email]en@quot.head[/email]er [email]en@boldquot.head[/email]er insert-header.sin Rules-quot   Makevars.template; do \
            /usr/bin/install -c -m 644 ./$file \
                            /usr/share/gettext/po/$file; \
          done; \
          for file in Makevars; do \
            rm -f /usr/share/gettext/po/$file; \
          done; \
        else \
          : ; \
        fi
make[1]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14/po'
make[1]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14'
make[2]: se ingresa al directorio `/usr/src/alsa/alsa-utils-1.0.14'
make[2]: No se hace nada para `install-exec-am'.
make[2]: No se hace nada para `install-data-am'.
make[2]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14'
make[1]: se sale del directorio `/usr/src/alsa/alsa-utils-1.0.14'
santiago@santiago-laptop:/usr/src/alsa/alsa-utils-1.0.14$ sudo gedit /etc/modprobe.d/alsa-base
santiago@santiago-laptop:/usr/src/alsa/alsa-utils-1.0.14$

---

### Post by Hei Ku on 2008-04-11
falta algo, me parece.

pone:

sudo modprobe -r alsa-base

sudo modprobe alsa-base

y postea si te tira algun mensaje.

otra cosa interesante para ver seria tu log de drivers.

es el archivo /var/log/dmesg

---

### Post by santisantermer on 2008-04-11
Intente ejecutar los comandos pero me aparece esto: 

santiago@santiago-laptop:~$ sudo modprobe -r alsa-base
[sudo] password for santiago:
FATAL: Module alsa_base not found.
santiago@santiago-laptop:~$ sudo modprobe alsa-base
FATAL: Module alsa_base not found.
santiago@santiago-laptop:~$ 



En /var/log/dmesg me aparece esto:

[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007f670000 (usable)
[    0.000000]  BIOS-e820: 000000007f670000 - 000000007f700000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007f700000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] 1142MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f71d0
[    0.000000] Entering add_active_range(0, 0, 521840) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   521840
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   521840
[    0.000000] On node 0 totalpages: 521840
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2284 pages used for memmap
[    0.000000]   HighMem zone: 290180 pages, LIFO batch:31
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7120 checksum 0
[    0.000000] ACPI: RSDP 000F7120, 0024 (r2 TOSINV)
[    0.000000] ACPI: XSDT 7F67B634, 008C (r1 TOSINV TOSINV00  6040000  INV        0)
[    0.000000] ACPI: FACP 7F682BF8, 00F4 (r3 TOSINV TOSINV00  6040000 ALAN        1)
[    0.000000] ACPI: DSDT 7F67D387, 57FD (r2 TOSINV CALISTGA  6040000 INTL 20050624)
[    0.000000] ACPI: FACS 7F683FC0, 0040
[    0.000000] ACPI: APIC 7F682CEC, 0068 (r1 INTEL  CALISTGA  6040000 LOHR       5A)
[    0.000000] ACPI: HPET 7F682D54, 0038 (r1 INTEL  CALISTGA  6040000 LOHR       5A)
[    0.000000] ACPI: MCFG 7F682D8C, 003C (r1 INTEL  CALISTGA  6040000 LOHR       5A)
[    0.000000] ACPI: TCPA 7F682DC8, 0032 (r1 PTLTD  CALISTGA  6040000  PTL        1)
[    0.000000] ACPI: APIC 7F682DFA, 0068 (r1 TOSINV   APIC    6040000  INV        0)
[    0.000000] ACPI: SLIC 7F682E62, 0176 (r1 TOSINV TOSINV00  6040000  INV        0)
[    0.000000] ACPI: BOOT 7F682FD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SSDT 7F67CD38, 064F (r1 SataRe  SataPri     1000 INTL 20050624)
[    0.000000] ACPI: SSDT 7F67C6A6, 0692 (r1 SataRe  SataSec     1000 INTL 20050624)
[    0.000000] ACPI: SSDT 7F67BC4C, 025F (r1  PmRef  Cpu0Tst     3000 INTL 20050624)
[    0.000000] ACPI: SSDT 7F67BBA6, 00A6 (r1  PmRef  Cpu1Tst     3000 INTL 20050624)
[    0.000000] ACPI: SSDT 7F67B6C0, 04E6 (r1  PmRef    CpuPm     3000 INTL 20050624)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify [email]linux-acpi@vger.kernel.org[/email]
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7ec00000)
[    0.000000] Built 1 zonelists.  Total pages: 517764
[    0.000000] Kernel command line: root=UUID=849be486-bb63-401c-887a-19881f374c12 ro quiet splash locale=es_ES
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1662.666 MHz processor.
[   10.536026] Console: colour VGA+ 80x25
[   10.536295] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   10.536593] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   10.629449] Memory: 2058040k/2087360k available (2015k kernel code, 28124k reserved, 915k data, 364k init, 1169856k highmem)
[   10.629458] virtual kernel memory layout:
[   10.629459]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   10.629460]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   10.629461]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   10.629462]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   10.629463]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   10.629465]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
[   10.629466]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
[   10.629469] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   10.629509] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   10.629661] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   10.629666] hpet0: 3 64-bit timers, 14318180 Hz
[   10.710564] Calibrating delay using timer specific routine.. 3328.74 BogoMIPS (lpj=6657497)
[   10.710588] Security Framework v1.0.0 initialized
[   10.710595] SELinux:  Disabled at boot.
[   10.710607] Mount-cache hash table entries: 512
[   10.710740] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e3bd 00000000 00000001
[   10.710748] monitor/mwait feature present.
[   10.710750] using mwait in idle threads.
[   10.710754] CPU: L1 I cache: 32K, L1 D cache: 32K
[   10.710757] CPU: L2 cache: 2048K
[   10.710759] CPU: Physical Processor ID: 0
[   10.710761] CPU: Processor Core ID: 0
[   10.710763] CPU: After all inits, caps: bfebfbff 20000000 00000000 00003940 0000e3bd 00000000 00000001
[   10.710772] Compat vDSO mapped to ffffe000.
[   10.710786] Checking 'hlt' instruction... OK.
[   10.726654] SMP alternatives: switching to UP code
[   10.727096] Early unpacking initramfs... done
[   11.057397] ACPI: Core revision 20070126
[   11.057442] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   11.092902] CPU0: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz stepping 02
[   11.092918] SMP alternatives: switching to SMP code
[   11.092996] Booting processor 1/1 eip 3000
[   11.103205] Initializing CPU#1
[   11.181836] Calibrating delay using timer specific routine.. 3325.01 BogoMIPS (lpj=6650033)
[   11.181842] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e3bd 00000000 00000001
[   11.181848] monitor/mwait feature present.
[   11.181851] CPU: L1 I cache: 32K, L1 D cache: 32K
[   11.181853] CPU: L2 cache: 2048K
[   11.181855] CPU: Physical Processor ID: 0
[   11.181857] CPU: Processor Core ID: 1
[   11.181858] CPU: After all inits, caps: bfebfbff 20000000 00000000 00003940 0000e3bd 00000000 00000001
[   11.182418] CPU1: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz stepping 02
[   11.182441] Total of 2 processors activated (6653.76 BogoMIPS).
[   11.182638] ENABLING IO-APIC IRQs
[   11.182840] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   11.329700] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   11.349686] Brought up 2 CPUs
[   11.540690] migration_cost=52
[   11.540822] Booting paravirtualized kernel on bare hardware
[   11.540911] Time: 21:54:39  Date: 03/11/108
[   11.540931] NET: Registered protocol family 16
[   11.541014] EISA bus registered
[   11.541018] ACPI: bus type pci registered
[   11.541144] PCI: PCI BIOS revision 2.10 entry at 0xfd604, last bus=7
[   11.541146] PCI: Using configuration type 1
[   11.541148] Setting up standard PCI resources
[   11.543931] ACPI: EC: Look up EC in DSDT
[   11.544802] ACPI: EC: GPE=0x16, ports=0x66, 0x62
[   11.546261] ACPI: System BIOS is requesting _OSI(Linux)
[   11.546264] ACPI: Please test with "acpi_osi=!Linux"
[   11.546265] Please send dmidecode to [email]linux-acpi@vger.kernel.org[/email]
[   11.546786] ACPI: Interpreter enabled
[   11.546790] ACPI: (supports S0 S3 S4 S5)
[   11.546806] ACPI: Using IOAPIC for interrupt routing
[   11.559001] ACPI: EC: GPE=0x16, ports=0x66, 0x62
[   11.559060] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   11.559069] PCI: Probing PCI hardware (bus 00)
[   11.559842] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   11.559846] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   11.560918] PCI: Transparent bridge - 0000:00:1e.0
[   11.561060] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   11.561382] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   11.561510] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[   11.561635] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[   11.561771] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   11.565457] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   11.565558] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   11.565656] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[   11.565753] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   11.565850] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[   11.565947] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[   11.566044] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[   11.566141] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   11.566315] ACPI: Power Resource [FN00] (on)
[   11.566324] Linux Plug and Play Support v0.97 (c) Adam Belay
[   11.566337] pnp: PnP ACPI init
[   11.566345] ACPI: bus type pnp registered
[   11.570425] pnp: PnP ACPI: found 10 devices
[   11.570428] ACPI: ACPI bus type pnp unregistered
[   11.570432] PnPBIOS: Disabled by ACPI PNP
[   11.570479] PCI: Using ACPI for IRQ routing
[   11.570482] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   11.596329] NET: Registered protocol family 8
[   11.596331] NET: Registered protocol family 20
[   11.596394] pnp: 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[   11.596398] pnp: 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
[   11.596401] pnp: 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[   11.596404] pnp: 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[   11.596412] pnp: 00:04: iomem range 0xfed00000-0xfed003ff could not be reserved
[   11.597206] Time: tsc clocksource has been installed.
[   11.597220] Switched to high resolution mode on CPU 0
[   11.597304] Switched to high resolution mode on CPU 1
[   11.626709] PCI: Bridge: 0000:00:1c.0
[   11.626713]   IO window: 2000-2fff
[   11.626719]   MEM window: f0600000-f06fffff
[   11.626724]   PREFETCH window: f0000000-f01fffff
[   11.626730] PCI: Bridge: 0000:00:1c.1
[   11.626734]   IO window: 3000-3fff
[   11.626740]   MEM window: f0700000-f07fffff
[   11.626745]   PREFETCH window: f0200000-f03fffff
[   11.626751] PCI: Bridge: 0000:00:1c.2
[   11.626754]   IO window: 4000-4fff
[   11.626761]   MEM window: f0800000-f08fffff
[   11.626766]   PREFETCH window: f0400000-f05fffff
[   11.626778] PCI: Bus 8, cardbus bridge: 0000:07:06.0
[   11.626780]   IO window: 00005000-000050ff
[   11.626785]   IO window: 00005400-000054ff
[   11.626791]   PREFETCH window: 88000000-8bffffff
[   11.626797]   MEM window: 8c000000-8fffffff
[   11.626801] PCI: Bridge: 0000:00:1e.0
[   11.626805]   IO window: 5000-5fff
[   11.626811]   MEM window: f0900000-f09fffff
[   11.626816]   PREFETCH window: 88000000-8bffffff
[   11.626846] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16
[   11.626853] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   11.626878] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 17
[   11.626885] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   11.626909] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   11.626916] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   11.626930] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   11.626948] PCI: Enabling device 0000:07:06.0 (0000 -> 0003)
[   11.626951] ACPI: PCI Interrupt 0000:07:06.0[A] -> GSI 18 (level, low) -> IRQ 18
[   11.626968] NET: Registered protocol family 2
[   11.673076] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   11.673135] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   11.673860] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   11.674120] TCP: Hash tables configured (established 131072 bind 65536)
[   11.674123] TCP reno registered
[   11.689188] checking if image is initramfs... it is
[   12.340380] Freeing initrd memory: 7067k freed
[   12.340502] Simple Boot Flag at 0x36 set to 0x1
[   12.340995] audit: initializing netlink socket (disabled)
[   12.341011] audit(1207950879.316:1): initialized
[   12.341120] highmem bounce pool size: 64 pages
[   12.343011] VFS: Disk quotas dquot_6.5.1
[   12.343060] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   12.343155] io scheduler noop registered
[   12.343157] io scheduler anticipatory registered
[   12.343160] io scheduler deadline registered
[   12.343173] io scheduler cfq registered (default)
[   12.343189] Boot video device is 0000:00:02.0
[   12.343364] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   12.343423] assign_interrupt_mode Found MSI capability
[   12.343426] Allocate Port Service[0000:00:1c.0:pcie00]
[   12.343462] Allocate Port Service[0000:00:1c.0:pcie02]
[   12.343563] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   12.343622] assign_interrupt_mode Found MSI capability
[   12.343624] Allocate Port Service[0000:00:1c.1:pcie00]
[   12.343655] Allocate Port Service[0000:00:1c.1:pcie02]
[   12.343761] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   12.343820] assign_interrupt_mode Found MSI capability
[   12.343822] Allocate Port Service[0000:00:1c.2:pcie00]
[   12.343853] Allocate Port Service[0000:00:1c.2:pcie02]
[   12.344014] isapnp: Scanning for PnP cards...
[   12.697396] isapnp: No Plug & Play device found
[   12.717927] Real Time Clock Driver v1.12ac
[   12.718171] hpet_resources: 0xfed00000 is busy
[   12.718203] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   12.719276] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   12.719501] input: Macintosh mouse button emulation as /class/input/input0
[   12.719620] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   12.723191] serio: i8042 KBD port at 0x60,0x64 irq 1
[   12.723195] serio: i8042 AUX port at 0x60,0x64 irq 12
[   12.723347] mice: PS/2 mouse device common for all mice
[   12.723454] EISA: Probing bus 0 at eisa.0
[   12.723462] Cannot allocate resource for EISA slot 1
[   12.723466] Cannot allocate resource for EISA slot 2
[   12.723468] Cannot allocate resource for EISA slot 3
[   12.723470] Cannot allocate resource for EISA slot 4
[   12.723473] Cannot allocate resource for EISA slot 5
[   12.723487] EISA: Detected 0 cards.
[   12.723701] TCP cubic registered
[   12.723715] NET: Registered protocol family 1
[   12.723734] Using IPI No-Shortcut mode
[   12.723888]   Magic number: 4:931:954
[   12.723900]   hash matches device ttya9
[   12.723936]   hash matches device ptyzb
[   12.724175] Freeing unused kernel memory: 364k freed
[   12.743879] input: AT Translated Set 2 keyboard as /class/input/input1
[   13.926055] AppArmor: AppArmor initialized<5>audit(1207950880.816:2):  type=1505 info="AppArmor initialized" pid=1257
[   13.931962] fuse init (API version 7.8)
[   13.936347] Failure registering capabilities with primary security module.
[   13.961535] ACPI: Fan [FAN0] (on)
[   13.966211] ACPI: SSDT 7F67C3F2, 01F9 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[   13.966423] ACPI: SSDT 7F67BEAB, 04C2 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[   13.966920] Monitor-Mwait will be used to enter C-1 state
[   13.966923] Monitor-Mwait will be used to enter C-2 state
[   13.966925] Monitor-Mwait will be used to enter C-3 state
[   13.966930] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   13.966935] ACPI: Processor [CPU0] (supports 8 throttling states)
[   13.967166] ACPI: SSDT 7F67C5EB, 00BB (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[   13.967362] ACPI: SSDT 7F67C36D, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[   13.967892] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   13.967897] ACPI: Processor [CPU1] (supports 8 throttling states)
[    3.188000] Marking TSC unstable due to: possible TSC halt in C2.
[    3.192000] Time: hpet clocksource has been installed.
[    3.192000] ACPI: Thermal Zone [TZ00] (50 C)
[    3.192000] ACPI: Invalid passive threshold
[    3.196000] ACPI: Thermal Zone [TZ01] (48 C)
[    3.656000] usbcore: registered new interface driver usbfs
[    3.656000] usbcore: registered new interface driver hub
[    3.656000] usbcore: registered new device driver usb
[    3.656000] USB Universal Host Controller Interface driver v3.0
[    3.656000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[    3.656000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    3.656000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.656000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.656000] uhci_hcd 0000:00:1d.0: irq 19, io base 0x00001820
[    3.656000] usb usb1: configuration #1 chosen from 1 choice
[    3.656000] hub 1-0:1.0: USB hub found
[    3.656000] hub 1-0:1.0: 2 ports detected
[    3.716000] SCSI subsystem initialized
[    3.720000] libata version 2.21 loaded.
[    3.760000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 20
[    3.760000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    3.760000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.760000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.760000] uhci_hcd 0000:00:1d.1: irq 20, io base 0x00001840
[    3.760000] usb usb2: configuration #1 chosen from 1 choice
[    3.760000] hub 2-0:1.0: USB hub found
[    3.760000] hub 2-0:1.0: 2 ports detected
[    3.864000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[    3.864000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    3.864000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.864000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.864000] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    3.864000] usb usb3: configuration #1 chosen from 1 choice
[    3.864000] hub 3-0:1.0: USB hub found
[    3.864000] hub 3-0:1.0: 2 ports detected
[    3.972000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 17
[    3.972000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    3.972000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.972000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    3.972000] uhci_hcd 0000:00:1d.3: irq 17, io base 0x00001880
[    3.972000] usb usb4: configuration #1 chosen from 1 choice
[    3.972000] hub 4-0:1.0: USB hub found
[    3.972000] hub 4-0:1.0: 2 ports detected
[    4.000000] Clocksource tsc unstable (delta = -190906945 ns)
[    4.076000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[    4.076000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    4.076000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.076000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    4.076000] ehci_hcd 0000:00:1d.7: debug port 1
[    4.076000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    4.076000] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xf0d44000
[    4.080000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.080000] usb usb5: configuration #1 chosen from 1 choice
[    4.080000] hub 5-0:1.0: USB hub found
[    4.080000] hub 5-0:1.0: 8 ports detected
[    4.184000] ACPI: PCI Interrupt 0000:07:06.1[B] -> GSI 17 (level, low) -> IRQ 16
[    4.232000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[f0905000-f09057ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    4.236000] ata_piix 0000:00:1f.2: version 2.11
[    4.236000] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    4.392000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
[    4.392000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    4.392000] scsi0 : ata_piix
[    4.392000] scsi1 : ata_piix
[    4.392000] ata1: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x000118b0 irq 14
[    4.392000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x000118b8 irq 15
[    4.556000] ata1.00: ATA-8: FUJITSU MHX2250BT, 0000000B, max UDMA/100
[    4.556000] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    4.572000] ata1.00: configured for UDMA/100
[    4.848000] usb 5-8: new high speed USB device using ehci_hcd and address 3
[    4.912000] ata2.00: ATAPI: PIONEER DVD-RW DVR-K17LF, 2.52, max UDMA/33
[    4.996000] usb 5-8: configuration #1 chosen from 1 choice
[    5.104000] ata2.00: configured for UDMA/33
[    5.104000] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHX2250B 0000 PQ: 0 ANSI: 5
[    5.112000] scsi 1:0:0:0: CD-ROM            PIONEER  DVD-RW DVR-K17LF 2.52 PQ: 0 ANSI: 5
[    5.124000] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[    5.124000] sd 0:0:0:0: [sda] Write Protect is off
[    5.124000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.124000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.124000] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[    5.124000] sd 0:0:0:0: [sda] Write Protect is off
[    5.124000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.124000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.124000]  sda: sda1 sda2 sda3 sda4
[    5.168000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.168000] Uniform CD-ROM driver Revision: 3.20
[    5.168000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.172000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.172000] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    5.208000] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.248000] usb 3-2: new full speed USB device using uhci_hcd and address 2
[    5.428000] usb 3-2: configuration #1 chosen from 1 choice
[    5.508000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00080da0d1781e4a]
[    5.508000] Attempting manual resume
[    5.508000] swsusp: Resume From Partition 8:1
[    5.508000] PM: Checking swsusp image.
[    5.508000] PM: Resume from disk failed.
[    5.520000] kjournald starting.  Commit interval 5 seconds
[    5.520000] EXT3-fs: mounted filesystem with ordered data mode.
[   14.752000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   14.760000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.772000] intel_rng: FWH not detected
[   14.780000] Linux agpgart interface v0.102 (c) Dave Jones
[   14.784000] agpgart: Detected an Intel 945GM Chipset.
[   14.788000] agpgart: Detected 7932K stolen memory.
[   14.804000] agpgart: AGP aperture is 256M @ 0xd0000000
[   14.832000] Yenta: CardBus bridge found at 0000:07:06.0 [1179:ff10]
[   14.832000] Yenta: Enabling burst memory read transactions
[   14.832000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   14.832000] Yenta: Routing CardBus interrupts to PCI
[   14.832000] Yenta TI: socket 0000:07:06.0, mfunc 0x01a01b22, devctl 0x66
[   14.916000] sdhci: Secure Digital Host Controller Interface driver
[   14.916000] sdhci: Copyright(c) Pierre Ossman
[   14.964000] Linux video capture interface: v2.00
[   14.984000] iTCO_vendor_support: vendor-support=0
[   14.988000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   15.064000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 18
[   15.064000] Socket status: 30000006
[   15.064000] Yenta: Raising subordinate bus# of parent bus (#07) from #07 to #0b
[   15.064000] pcmcia: parent PCI bridge I/O window: 0x5000 - 0x5fff
[   15.064000] cs: IO port probe 0x5000-0x5fff: clean.
[   15.064000] pcmcia: parent PCI bridge Memory window: 0xf0900000 - 0xf09fffff
[   15.064000] pcmcia: parent PCI bridge Memory window: 0x88000000 - 0x8bffffff
[   15.064000] ACPI: PCI Interrupt 0000:07:06.2[A] -> GSI 18 (level, low) -> IRQ 18
[   15.064000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 17
[   15.064000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   15.064000] sky2 0000:02:00.0: v1.18 addr 0xf0600000 irq 17 Yukon-FE (0xb7) rev 3
[   15.064000] sky2 eth0: addr 00:a0:d1:78:1e:4a
[   15.064000] sdhci: SDHCI controller found at 0000:07:06.3 [104c:803c] (rev 0)
[   15.064000] ACPI: PCI Interrupt 0000:07:06.3[A] -> GSI 18 (level, low) -> IRQ 18
[   15.064000] mmc0: SDHCI at 0xf0905800 irq 18 DMA
[   15.176000] uvcvideo: Found UVC 1.00 device Chicony USB 2.0 Camera (04f2:b008)
[   15.180000] usbcore: registered new interface driver uvcvideo
[   15.180000] USB Video Class driver (v0.1.0)
[   15.356000] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.1.0
[   15.356000] iwl4965: Copyright(c) 2003-2007 Intel Corporation
[   15.356000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 16
[   15.356000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   15.356000] iwl4965: Detected Intel Wireless WiFi Link 4965AGN
[   15.420000] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x9280b1, caps: 0xa04713/0x204000
[   15.420000] synaptics: Toshiba Satellite A205 detected, limiting rate to 40pps.
[   15.452000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[   15.456000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   15.456000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   15.692000] cs: IO port probe 0x100-0x3af: clean.
[   15.696000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   15.696000] cs: IO port probe 0x820-0x8ff: clean.
[   15.696000] cs: IO port probe 0xc00-0xcf7: clean.
[   15.696000] cs: IO port probe 0xa00-0xaff: clean.
[   15.720000] iwl4965: Tunable channels: 11 802.11bg, 13 802.11a channels
[   15.720000] wmaster0: Selected rate control algorithm 'iwl-4965-rs'
[   15.960000] snd_hda_intel: disagrees about version of symbol snd_dma_free_pages
[   15.960000] snd_hda_intel: Unknown symbol snd_dma_free_pages
[   15.964000] snd_hda_intel: disagrees about version of symbol snd_dma_alloc_pages
[   15.964000] snd_hda_intel: Unknown symbol snd_dma_alloc_pages
[   16.136000] lp: driver loaded but no devices found
[   16.204000] Adding 1534168k swap on /dev/sda1.  Priority:-1 extents:1 across:1534168k
[   16.852000] EXT3 FS on sda3, internal journal

---

### Post by Hei Ku on 2008-04-11
Proba esto:

```

sudo rm /lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko
sudo ln -s /lib/modules/2.6.22-14-generic/kernel/sound/pci/hda/snd-hda-intel.ko /lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko
sudo modprobe -r snd_hda_intel
sudo modprobe snd_hda_intel

```

---

### Post by santisantermer on 2008-04-12
Hola Hei Ku. Me tiró esto.
Gracias.
S.

santiago@santiago-laptop:~$ sudo rm /lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-
rm: no se puede borrar `/lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-': No existe el fichero ó directorio
santiago@santiago-laptop:~$ hda-intel.ko
bash: hda-intel.ko: orden no encontrada

---

### Post by Hei Ku on 2008-04-12
Proba de vuelta. Ahi lo edité para que no tenga el corte de linea, que fue lo que hizo que fallara. :s

---

### Post by santisantermer on 2008-04-12
Mejoro la situacion. Al girar la perilla del volumen aparece la regulaciòn en pantalla y desde el icono de la barra de tareas aparece un control de volumen. Con el utimo proceso estas opciones habian desaparecidoy al hacer esto ultimo me aparecia un cartel de error. Pero no sale ningun sonido por mas que ponga ambas regulaciones al mango.
Gracias,
Santiago

---

### Post by Hei Ku on 2008-04-12
que te dice ahora si ejecutas el alsamixer?

---

### Post by santisantermer on 2008-04-12
Me tira esto:



&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[AlsaMixer v1.0.14 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA Intel                                                              &#9474;
&#9474; Chip: Realtek ID 268                                                         &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master [dB gain=-40.00, -40.00]                                        &#9474;
&#9474;                                                                              &#9474;
&#9474;           &#9484;&#9472;&#9472;&#9488;             &#9484;&#9472;&#9472;&#9488;                                              &#9474;
&#9474;           &#9474;  &#9474;             &#9474;&#9618;&#9618;&#9474;                                              &#9474;
&#9474;           &#9474;  &#9474;             &#9474;&#9618;&#9618;&#9474;                                              &#9474;
&#9474;           &#9474;  &#9474;             &#9474;&#9618;&#9618;&#9474;                                              &#9474;
&#9474;           &#9474;  &#9474;             &#9474;&#9618;&#9618;&#9474;                                              &#9474;
&#9474;           &#9474;  &#9474;             &#9474;&#9618;&#9618;&#9474;                                              &#9474;
&#9474;           &#9474;  &#9474;             &#9474;&#9618;&#9618;&#9474;                                              &#9474;
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                                              &#9474;
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                                              &#9474;
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                                              &#9474;
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                                              &#9474;
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                                              &#9474;
&#9474;           &#9492;&#9472;&#9472;&#9496;             &#9492;&#9472;&#9472;&#9496;             &#9484;&#9472;&#9472;&#9488;             &#9484;&#9472;&#9472;&#9488;            &#9474;
&#9474;                                             &#9474;MM&#9474;             &#9474;MM&#9474;            &#9474;
&#9474;                                             &#9492;&#9472;&#9472;&#9496;             &#9492;&#9472;&#9472;&#9496;            &#9474;
&#9474;          38<>38          100<>100                                            &#9474;
&#9474;        < Master >          PCM            Caller I         Off-hook          &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

---

### Post by Hei Ku on 2008-04-13
subile el volumen en todos los canales. A veces el principal de tu placa no es el que reconoce como Master.

---

### Post by santisantermer on 2008-04-13
Entre al alsamixer y puse al maximo Master y PCM. Apretando F4 aparecio Digital y lo subi hasta el tope tb. Pero Caller ID y Off-hook estàn en off y no sè còmo activarlos para poder subirlos. Tenes idea como puedo hacer?.
Muchas gracias,
Santiago.

---

### Post by sajnox on 2008-04-13
Perdon que me meta nuevamente pero tal vez esto te sirve

[http://www.bloog.cl/2007/05/solucion-a-problemas-de-sonido-en-ubuntu-feisty-con-chips-intel/](http://www.bloog.cl/2007/05/solucion-a-problemas-de-sonido-en-ubuntu-feisty-con-chips-intel/)

Saludos

---

### Post by santisantermer on 2008-04-13
Hola Sajnox, segui tu sugerencia pero no paso nada. En donde agregue el texto quedo justo debajo de lo que agregamos con Hei Ku, no se si se invalidan mutuamente o algo asi. Igualmente sigo teniendo dos canales en off en el aslamixer, el coller ID y el hook-off o algo asi. No encuentro la manera de activarlos y ponerlos al maximo. Alguien sabe como hacerlo.
Muchas gracias por todas las sugerencias,
Santiago.

---

### Post by Hei Ku on 2008-04-13
esos dos canales parecen ser otra cosa. raro que todavia sigas sin oir nada.

fijate si cambiando el dispositivo de sonido en las preferencias del sistema, por alsa o oss te empieza a salir sonido.

---

### Post by santisantermer on 2008-04-14
Hola Hei Ku. Hice los cambios, pero al ponerle "probar" se me aparece un cartel que dice "Prueba..." y abajo una barra oscilante durante mucho tiempo. Pasa con las opciones de ALSA y OSS, con otras tambien. Algunas tiran un mensaje de error.
Muchas gracias por todo,
Santiago.

---

### Post by sajnox on 2008-04-14
Hola,

En la lista de mail de Ubuntu-ar uno de los miembros, Marco Antonio de Hoyos  (un pibe que realmente sabe del tema) tuvo un problema parecido y lo saco andando.

Copio el mail en el que comenta que lo hizo andar

1er. Mail

```
buenas...

estoy "migrando" una note toshiba a 7.10 , pero la nena no quiere sonar.. :P

los datos son: toshiba a105-s4384 con ubuntu 7.10

ya re-instale alsa, segui estos pasos (aunque sea de una ibm, el hard
el es mismo):

https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/94373/comments/33

modifique el alsa-base con varias opciones y nada.

a alguien le paso lo mismo ? alguien lo pudo hacer funcionar ??

es lo que me falta terminar para dejarla andando

antes con un madriva andaba de lujo.. :(

salu2

```

En este mail comenta que lo soluciono

```
gracias a todos x la respuesta..

parece que despues de tanto "toquetear" salio andando.. que hice ?? lo
siguiente:

- realice lo que puse en el link del 1er post.
- agregue el repo backposts y realice un update / upgrade.
- como no andaba, me puse a buscar los nuevos snd-hda-intel.ko dentro
de /lib/modules
- empece a "copiar" (previamente renombrar el existente" desde el dir
/ubuntu/sound, /updates y demas..
- despues de varios reinicios y movidas, empezo a funcionar...

lo extraño: al "bajar" el servicio alsadound y el modulo a mano,
(modprobe -r snd-hda-intel) y luego volver a cargarlo (modprobe -v
snd-hda-intel) levanta del dir /lib/modules/'uname -r'/updates/sound
el modulo, y no de otros dirs que estan dentro de contenedor
principal, estando un .ko mas actualizado y generado desde el link que
pase al principio.

esto, parece que hay que "mover" un poco los archivos, y despues de
varias reiniciadas, "toma" el que tiene que andar.. :P

a ciencia cierta, no podria indicarles el procedimiento esacto, pero
esta funcionando y es lo que necesitaba... jejeje..
- Ocultar texto citado -

salutes
```

Si necesitas mas ayuda de el, te sugiero que te suscribas a la lista o lo contactes a traves de su pagina web [www.tecnicoslinux.com.ar](www.tecnicoslinux.com.ar)

Nuevamente espero que te sirva

---

### Post by santisantermer on 2008-04-14
Muchas gracias Sajonox. Debo confesarte que no tengo ni idea de còmo hacer lo que describe el chavon en el mensaje. Suena como que para alguien que sabe es una pavada, pero para mi es como traducir shimauta (la canciòn en japones que canta el gordo Casero) al celta antiguo. Bueno, creo que exagere un poco jejeje.
Si alguien puede orientarme un poco se lo voy a agradecer, sino me voy a poner en contacto con el que escribió el mensaje original.
Un abrazo,
Santiago.

---

### Post by Hei Ku on 2008-04-14
que te aparece en el /var/log/dmesg? eso puede dar una pista si todavia hay problemas con el driver.

---

### Post by santisantermer on 2008-04-27
Hola, al hacer el upgrade a ubuntu 8.04 levantó el sonido!!! Al instalarlo me dijo que habìa una nueva versiòn de alsa y la instalé. No sé si tendrá algo que ver o si solamente todo lo que habiamos hecho empezó a funcionar.Anda tanto con los parlantes como con el headset. 
Ahora que puedo escuchar sonido apareció un problema con el mic, pero lo voy a poner en otro post, asi este queda como solucionado.
Quería aprovechar esta oportunidad para agradecerles a todos por la ayuda, la paciencia y todo lo que pusieron para que pueda solucionar el problema de sonido que era crítico para seguir con ubuntu.
Saludos.
Santiago.

---

### Post by santisantermer on 2008-04-27
Fui a Thread tools para ponerlo como solucionado pero no me apareció la opción. Hay otra forma de hacerlo?
Muchas gracias,
Santiago.

---

### Post by sajnox on 2008-04-27
Por el momento sacaron la opcion de poner el thread como solved, haremos lo posible para que vuelva ya que siempre nos parecio util


Saludos

---

