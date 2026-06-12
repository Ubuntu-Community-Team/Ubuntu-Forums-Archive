---
title: "fingerprint reader toshiba"
date: 2008-04-02
forum: Argentina Team
---

### Post by santisantermer on 2008-04-02
Hi, I've just installed ubuntu 7.10 in my laptop Toshiba satellite A205 S4617, but I don't know how to install my built-in fingerprint reader.
Thank you for your help!

---

### Post by facundocorradini on 2008-04-02
acá hablamos español.

---

### Post by alejandro.mc on 2008-04-02
Jajjajajajaj que bueno. Perdon pero me resulto divertido.

---

### Post by vk-cdg on 2008-04-03
Que toman allá?
Dos veces lo posteó y dos veces la pifió.

---

### Post by santisantermer on 2008-04-04
Queridos miembros del foro de ubuntu. Escribí en ingles porque al antrar al foro de Argentina me redireccionó a otro en el cual todos los mensajes estaban escritos en ese idioma.
Además tuve que crear nuevamente mi usuario, por lo cual supuse que ya no estaba más en el foro de nuestro país. Creo que presta para la confusión. De no ser por eso, obviamente hubiera escrito en español que, sinceramente, me es mucho más fácil.
Mi duda era la siguiente: al instalar ubuntu, no me reconoce el lector de huellas digitales. La verdad es que no tengo la menor idea de cómo instalarlo. Si alguien conoce la forma y tiene ganas de ayudarme me haría un gran favor.
Muchas gracias,
Santiago.

---

### Post by vk-cdg on 2008-04-04
Ahora si, superado el mal entendido, paso a contestarte.
A menos que esté equivocado (que alguien me corrija) en las notebooks no andan ni los lectores de tarjetas ni los de huellas. 
Al parecer no hay drivers para nada de eso todavía.

---

### Post by Hei Ku on 2008-04-04
la manera de buscar si hay soporte es conseguir con lspci o lsusb (dependiendo si es un periferico pci o usb) el modelo de chipset, y con eso buscar en google.
los que mas clara la tienen con esas cosas, despues de los de openBSD, son los de Gentoo. cualquiera de los dos te van a aparecer si buscas, pero postea los modelos de chipset aca a ver si te podemos dar una mano.

---

### Post by leo_rockway on 2008-04-04
> **vk-cdg said:**
> Ahora si, superado el mal entendido, paso a contestarte.
A menos que esté equivocado (que alguien me corrija) en las notebooks no andan ni los lectores de tarjetas ni los de huellas. 
Al parecer no hay drivers para nada de eso todavía.

Depende de que tarjetas, yo tengo un lector multiple y con xD no va ni patras ni padelante, pero con SD funciona ferpecto.

---

### Post by santisantermer on 2008-04-08
Muchas gracias por la orientación.
Al poner  lspci me apareció el mensaje al pie. Espero que la info sirva para seguir. No tengo idea cuál de estos corresponde al lector de huellas digitales.
Un abrazo,
Santiago.


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

### Post by MeduZa on 2008-04-09
lsusb que pone?

---

### Post by santisantermer on 2008-04-09
Hola MeduZa, con Isusb me pone esto:

santiago@santiago-laptop:~$ lsusb
Bus 005 Device 003: ID 04f2:b008 Chicony Electronics Co., Ltd 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
santiago@santiago-laptop:~$ 

Muchas gracias por todo.
Santiago.

---

### Post by Hei Ku on 2008-04-09
Tenes un par de opciones.

1) Esperar a Hardy, que ya va a incluir el driver: [https://bugs.launchpad.net/bugs/117654](https://bugs.launchpad.net/bugs/117654)

2) Fijarte en esta pagina, que es la del driver, a ver si lo instalas a mano:
[http://thinkfinger.sourceforge.net/](http://thinkfinger.sourceforge.net/)

---

### Post by santisantermer on 2008-04-09
Hola Hei Ku,
lo bajè desde la pagina y extraje los archivos en temp pero no puedo instalarlos. Intente con el synaptic pero no lo encuentra. Con la terminal tampoco pude.
Ya no se como agradecerte todo lo que estas haciendo por mi. Soy nuevo en ubuntu y estoy perdidisimo!!!!!!.
Un abrazo,
Santiago.



santiago@santiago-laptop:~$ sudo apt-get install thinkfinger-0.3.tar.gz
[sudo] password for santiago:
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
E: No se pudo encontrar el paquete thinkfinger-0.3.tar.gz
santiago@santiago-laptop:~$ tar xfvz thinkfinger-0.3.tar.gz
tar: thinkfinger-0.3.tar.gz: No se puede open: No existe el fichero ó directorio
tar: El error no es recuperable: salida ahora
tar: Child returned status 2
tar: Salida con error demorada desde errores anteriores
santiago@santiago-laptop:~$ sudo apt-get install thinkfinger-0.3.tar.gz
[sudo] password for santiago:
E: No se pudo bloquear /var/lib/dpkg/lock - open (11 Recurso temporalmente no disponible)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
santiago@santiago-laptop:~$

---

### Post by Hei Ku on 2008-04-09
estas re perdido. el comando que probaste es para synaptic, que es para instalar desde los repositorios oficiales de ubuntu.

para instalar archivos bajados desde internet la manera es distinta

por empezar, me gustaria saber donde te esta dejando realmente el firefox los archivos que bajas, porque en temp no tan.

asi que vamos a hacer lo siguiente en una terminal:

```

wget http://downloads.sourceforge.net/thinkfinger/thinkfinger-0.3.tar.gz?modtime=1175248481&big_mirror=0
tar xvfz thinkfinger-0.3.tar.gz

```

ahi te tiene q crear una carpeta llamada thinkfinger o algo asi
entra a la carpeta y postea los contenidos
alguno de esos archivos tiene que ser un readme que explique como instalarlo

---

### Post by santisantermer on 2008-04-09
Me tiró esto:

santiago@santiago-laptop:~$ wget [http://downloads.sourceforge.net/thi...1&big_mirror=0](http://downloads.sourceforge.net/thi...1&big_mirror=0)
[1] 7340
santiago@santiago-laptop:~$ tar xvfz thinkfinger-0.3.tar.gz--23:53:56--  [http://downloads.sourceforge.net/thi...1](http://downloads.sourceforge.net/thi...1)
           => `thi...1'
Resolviendo downloads.sourceforge.net... 66.35.250.203
Conectando a downloads.sourceforge.net|66.35.250.203|:80... conectado.
Petición HTTP enviada, esperando respuesta... 301 Moved Permanently
Ubicación: [http://sourceforge.net/projects/thi---1/files](http://sourceforge.net/projects/thi---1/files) [siguiente]
--23:54:05--  [http://sourceforge.net/projects/thi---1/files](http://sourceforge.net/projects/thi---1/files)
           => `files.1'
Resolviendo sourceforge.net... 66.35.250.203
Conectando a sourceforge.net|66.35.250.203|:80... conectado.
Petición HTTP enviada, esperando respuesta... 200 OK
Longitud: no especificado [text/html]

    [  <=>                                ] 10.508        37.18K/s             

23:54:14(37.08 KB/s) - `files.1' guardado [10508]

---

### Post by Hei Ku on 2008-04-10
proba de vuelta, ahi corregi mi post anterior para que puedas copiar bien todo. antes te corto la direccion http.

---

### Post by santisantermer on 2008-04-10
Gracias Hei Ku.
Lo que no se es donde encontrar la carpeta.
Por las dudas aca te puse lo que me posteo.
Muchas gracias,
Santiago.


santiago@santiago-laptop:~$ wget [http://downloads.sourceforge.net/thinkfinger/thinkfinger-0.3.tar.gz?modtime=1175248481&big_mirror=0](http://downloads.sourceforge.net/thinkfinger/thinkfinger-0.3.tar.gz?modtime=1175248481&big_mirror=0)
[1] 6366
santiago@santiago-laptop:~$ --18:48:23--  [http://downloads.sourceforge.net/thinkfinger/thinkfinger-0.3.tar.gz?modtime=1175248481](http://downloads.sourceforge.net/thinkfinger/thinkfinger-0.3.tar.gz?modtime=1175248481)
           => `thinkfinger-0.3.tar.gz?modtime=1175248481'
Resolviendo downloads.sourceforge.net... 66.35.250.203
Conectando a downloads.sourceforge.net|66.35.250.203|:80... conectado.
Petición HTTP enviada, esperando respuesta... 302 Found
Ubicación: [http://ufpr.dl.sourceforge.net/sourceforge/thinkfinger/thinkfinger-0.3.tar.gz](http://ufpr.dl.sourceforge.net/sourceforge/thinkfinger/thinkfinger-0.3.tar.gz) [siguiente]
--18:48:24--  [http://ufpr.dl.sourceforge.net/sourceforge/thinkfinger/thinkfinger-0.3.tar.gz](http://ufpr.dl.sourceforge.net/sourceforge/thinkfinger/thinkfinger-0.3.tar.gz)
           => `thinkfinger-0.3.tar.gz.1'
Resolviendo ufpr.dl.sourceforge.net... 200.17.202.1
Conectando a ufpr.dl.sourceforge.net|200.17.202.1|:80... conectado.
Petición HTTP enviada, esperando respuesta... 200 OK
Longitud: 372.053 (363K) [application/x-gzip]

100%[====================================>] 372.053       54.31K/s    ETA 00:00

18:48:29 (65.37 KB/s) - `thinkfinger-0.3.tar.gz.1' guardado [372053/372053]

tar xvfz thinkfinger-0.3.tar.gz
thinkfinger-0.3/
thinkfinger-0.3/pam/
thinkfinger-0.3/pam/pam_thinkfinger.c
thinkfinger-0.3/pam/pam_thinkfinger-uinput.c
thinkfinger-0.3/pam/pam_thinkfinger-uinput.h
thinkfinger-0.3/pam/pam_thinkfinger-compat.c
thinkfinger-0.3/pam/pam_thinkfinger-compat.h
thinkfinger-0.3/pam/Makefile.am
thinkfinger-0.3/pam/Makefile.in
thinkfinger-0.3/NEWS
thinkfinger-0.3/docs/
thinkfinger-0.3/docs/pam_thinkfinger.8
thinkfinger-0.3/docs/autodocs/
thinkfinger-0.3/docs/autodocs/Makefile.am
thinkfinger-0.3/docs/autodocs/Makefile.in
thinkfinger-0.3/docs/autodocs/Doxyfile
thinkfinger-0.3/docs/tf-tool.1
thinkfinger-0.3/docs/Makefile.am
thinkfinger-0.3/docs/Makefile.in
thinkfinger-0.3/compile
thinkfinger-0.3/depcomp
thinkfinger-0.3/aclocal.m4
thinkfinger-0.3/README.in
thinkfinger-0.3/README
thinkfinger-0.3/ltmain.sh
thinkfinger-0.3/configure
thinkfinger-0.3/configure.in
thinkfinger-0.3/tf-tool/
thinkfinger-0.3/tf-tool/tf-tool.c
thinkfinger-0.3/tf-tool/Makefile.am
thinkfinger-0.3/tf-tool/Makefile.in
thinkfinger-0.3/config.guess
thinkfinger-0.3/install-sh
thinkfinger-0.3/config.sub
thinkfinger-0.3/missing
thinkfinger-0.3/INSTALL.in
thinkfinger-0.3/Makefile.am
thinkfinger-0.3/Makefile.in
thinkfinger-0.3/config.h.in
thinkfinger-0.3/AUTHORS
thinkfinger-0.3/libthinkfinger/
thinkfinger-0.3/libthinkfinger/libthinkfinger.c
thinkfinger-0.3/libthinkfinger/libthinkfinger.h
thinkfinger-0.3/libthinkfinger/Makefile.am
thinkfinger-0.3/libthinkfinger/Makefile.in
thinkfinger-0.3/libthinkfinger/libthinkfinger-crc.c
thinkfinger-0.3/libthinkfinger/libthinkfinger-crc.h
thinkfinger-0.3/libthinkfinger/libthinkfinger.pc.in
thinkfinger-0.3/INSTALL
thinkfinger-0.3/ChangeLog
thinkfinger-0.3/COPYING
[1]+  Done                    wget [http://downloads.sourceforge.net/thinkfinger/thinkfinger-0.3.tar.gz?modtime=1175248481](http://downloads.sourceforge.net/thinkfinger/thinkfinger-0.3.tar.gz?modtime=1175248481)
santiago@santiago-laptop:~$

---

### Post by MeduZa on 2008-04-10
> **Hei Ku said:**
> Tenes un par de opciones.

1) Esperar a Hardy, que ya va a incluir el driver: [https://bugs.launchpad.net/bugs/117654](https://bugs.launchpad.net/bugs/117654)

2) Fijarte en esta pagina, que es la del driver, a ver si lo instalas a mano:
[http://thinkfinger.sourceforge.net/](http://thinkfinger.sourceforge.net/)

no vale ganarme de mano :lolflag: al menos lo encontraste rapido!!

---

### Post by MeduZa on 2008-04-10
> **Hei Ku said:**
> proba de vuelta, ahi corregi mi post anterior para que puedas copiar bien todo. antes te corto la direccion http.

lo complicaste al pobre con la consola -.-, lo que bajaste esta en tu home.
todo eso lo podias hacer desde ventanas xD

ya que empezaste en consola terminemosla ahi.

borra todo lo que hiciste que aca te lo compile yo y te lo hice deb, no se si te va a andar mi arquitectura es i686 y mi kernel es otro pero por ahi te va!!

si no llega a andar diganme como compilo de otra manera para que ande Y_Y solo se hacerlo de esa!

EDIT: no lo instale y por ende no lo proble ya que no tengo un lector de huellas dactilares.

---

### Post by sajnox on 2008-04-10
Para compilar fuentes hasta ahora siempre me sirvio el comando alien que me ahorro dolores varios de cabeza

Primero instalar alien

```
sudo apt-get install alien
```
Segundo: Usar alien para generar un paquete .deb compilado en tu maquina

```
sudo alien -v thinkfinger-0.3.tar.gz
```

El -v (verbose) no es necesario pero a mi me gusta que me cuente que es lo que esta haciendo.

Con el .deb generado podes simplemente hacer doble click y el paquete se instala, despues fijate en que carpeta lo puso para poder ejecutarlo

Tambien si queres alien puede instalar el archivo tar.gz directamente, a mi me gutsar dejarlo compilado en mi maquina por cualquier cosa pero la logica indica siempre tener las fuentes y compilarlas segun la necesidad

```
sudo alien -vi thinkfinger-0.3.tar.gz
```

---

### Post by santisantermer on 2008-04-10
Muchachos, no entiendo una goma. Tengo que bajar el archivo que compilo Meduza y despues seguir las instrucciones de Sajonox o directamente esto ultimo. Al descargar el archivo lo guardo en algun lugar en particular o dejo que lo abra fireforx por default?
Gracias por sus sugerencias.

---

### Post by Hei Ku on 2008-04-10
baja el archivo, abri una terminal en la carpeta donde bajaste el archivo, y segui las instrucciones de sajnox

---

### Post by sajnox on 2008-04-10
> **Hei Ku said:**
> baja el archivo, abri una terminal en la carpeta donde bajaste el archivo, y segui las instrucciones de sajnox

Un honor que avales mi post!!!!

Nos vemos el 24

---

### Post by santisantermer on 2008-04-11
Ahi lo corri. Tuve que cambiarle el nombre del archivo porque no lo encontraba, me fije y no coincidia con el nombre del de MeduZa.
Supuestamente está instalado pero no tengo idea de a donde ir a buscarlo para usarlo. Lo busque por todos lados y no lo encuentro.
Gracias,
Santiago

PD: Por las dudas ahi va lo que apareciò en la terminal.

santiago@santiago-laptop:/home$ cd /home/santiago/downloads
santiago@santiago-laptop:~/downloads$ sudo apt-get install alien
[sudo] password for santiago:
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
alien ya está en su versión más reciente.
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.
santiago@santiago-laptop:~/downloads$ sudo alien -v thinkfinger-0.3.tar.gz
File "thinkfinger-0.3.tar.gz" not found.
santiago@santiago-laptop:~/downloads$ sudo alien -v thinkfinger_0.3-1_i386.deb
        dpkg-deb --info thinkfinger_0.3-1_i386.deb control 2>/dev/null
        dpkg-deb --info thinkfinger_0.3-1_i386.deb control 2>/dev/null
        dpkg-deb --info thinkfinger_0.3-1_i386.deb conffiles 2>/dev/null
        dpkg-deb --fsys-tarfile thinkfinger_0.3-1_i386.deb | tar tf -
        dpkg-deb --info thinkfinger_0.3-1_i386.deb postinst 2>/dev/null
        dpkg-deb --info thinkfinger_0.3-1_i386.deb postrm 2>/dev/null
        dpkg-deb --info thinkfinger_0.3-1_i386.deb preinst 2>/dev/null
        dpkg-deb --info thinkfinger_0.3-1_i386.deb prerm 2>/dev/null
santiago@santiago-laptop:~/downloads$ sudo alien -vi thinkfinger_0.3-1_i386.deb
        dpkg-deb --info thinkfinger_0.3-1_i386.deb control 2>/dev/null
        dpkg-deb --info thinkfinger_0.3-1_i386.deb control 2>/dev/null
        dpkg-deb --info thinkfinger_0.3-1_i386.deb conffiles 2>/dev/null
        dpkg-deb --fsys-tarfile thinkfinger_0.3-1_i386.deb | tar tf -
        dpkg-deb --info thinkfinger_0.3-1_i386.deb postinst 2>/dev/null
        dpkg-deb --info thinkfinger_0.3-1_i386.deb postrm 2>/dev/null
        dpkg-deb --info thinkfinger_0.3-1_i386.deb preinst 2>/dev/null
        dpkg-deb --info thinkfinger_0.3-1_i386.deb prerm 2>/dev/null
        dpkg --no-force-overwrite -i thinkfinger_0.3-1_i386.deb
(Leyendo la base de datos ...  
119363 ficheros y directorios instalados actualmente.)
Preparando para reemplazar thinkfinger 0.3-1 (usando thinkfinger_0.3-1_i386.deb) ...
Desempaquetando el reemplazo de thinkfinger ...
Configurando thinkfinger (0.3-1) ...
santiago@santiago-laptop:~/downloads$

---

### Post by MeduZa on 2008-04-11
creo que lo unico que tenias que hacer era bajar mi archivo hacerle doble click e instalarlo solo eso, despues de ahi en adelante no se deciste, ya que, como no tengo el lector no se como que hay que hacer pero seguramente cuando lo enchfes el modprove levanta el driver o capas tengas que hacer algo mas.

fijate.

---

### Post by Hei Ku on 2008-04-11
ahora necesitas un programa para usarlo. ni idea!! :D

EDIT:
me estuve fijando, y el thinkfinger viene con la integracion con PAM (el gestor de autenticacion de linux)

fijate si en la parte de administracion de usuarios, en tu usuario no tenes para registrar tu contraseña o algo asi. deberia aparecerte algo. si no, anda a la pagina de thinkfinger y fijate si hay alguna instruccion.

EDIT2:
[https://wiki.ubuntu.com/ThinkFinger](https://wiki.ubuntu.com/ThinkFinger)

ahi tenes info

---

### Post by MeduZa on 2008-04-12
> **Hei Ku said:**
> ahora necesitas un programa para usarlo. ni idea!! :D

EDIT:
me estuve fijando, y el thinkfinger viene con la integracion con PAM (el gestor de autenticacion de linux)


para compilarlo me pidio la libreria PAM asi que seguro se le instala como dependencia.

---

### Post by santisantermer on 2008-04-12
No puede encontrar nada con el nombre PAM ni en la configuraciòn del usuario y las contraseñas. En la pagina de finger print habia un comando para testearlo y este fue el resultado:

santiago@santiago-laptop:~$ sudo tf-tool --acquire
[sudo] password for santiago:

ThinkFinger 0.3 ([http://thinkfinger.sourceforge.net/](http://thinkfinger.sourceforge.net/))
Copyright (C) 2006, 2007 Timo Hoenig <thoenig@suse.de>

Initializing... done.
Please swipe your finger (successful swipes 3/3, failed swipes: 0)... done.
Storing data (/tmp/test.bir)...Warning: usb_bulk_read expected to read 0x40 (read 0x2c bytes).
sudo tf-tool --verify

Con el ultimo comando no paso nada.
Ejecute tambien los comandos bajo el titulo To be able to use ThinkFinger 0.3. en [https://wiki.ubuntu.com/ThinkFinger](https://wiki.ubuntu.com/ThinkFinger). Me aparecio esto:

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2











                               [ Leer 8 líneas ]
^G Ver ayuda ^O Guardar   ^R Leer Fich ^Y Pág Ant   ^K Cortar Tex^C Pos actual
^X Salir     ^J Justificar^W Dónde Está^V Pág Sig   ^U PegarTxt  ^T Ortografía

---

### Post by Hei Ku on 2008-04-13
estas ahi nomas. en realidad leyo la huella, pero no la pudo guardar.

pone esto:

```

sudo apt-get install build-essential libtool libusb-dev libpam0g-dev pkg-config

sudo mkdir /etc/pam_thinkfinger

```

postea cualquier error que te tire

despues tenes que hacer lo que dice en To be able to use ThinkFinger 0.3, que es verificar si esta cargado el modulo uinput, y si no agregarlo al archivo modules.

si con este comando no te aparece nada:
```

lsmod | grep uinput

```
entonces tenes que agregarlo a modules para que lo cargue.
```

sudo gedit /etc/modules

```
y al final del archivo agregas:
```

uinput

```

---

### Post by santisantermer on 2008-04-13
Agregue el comando y lo testee. Aparentemente funciona con el testeo pero no se como usarlo fuera de ahi.
Saludos,
S.

---

### Post by Hei Ku on 2008-04-13
La seccion Use it everyday ! explica como agregar la huella a tu usuario para utilizar el lector para loguearte.

EDIT: ya estas ahi, son solo unos pasos mas.
Y recapitulando un poco todo lo que tuviste que hacer para sacar las cosas andando, realmente quiero destacar la paciencia que tuviste para hacer funcionar el hw. No es común verlo, y me parece digno de admiracion. Si bien todavia te faltan resolver un par de cosas, ya estas a punto. el resto es en bajada. :)

---

### Post by santisantermer on 2008-04-14
Hola Hei Ku. Muchas gracias por las palabras de aliento.
Yo también me asombro de la paciencia que tenes para seguir dandome orientandome a esta altura. Muchas gracias por eso.
En cuanto a tu sugerencia, abri el archivo que señalan en la pagina y no me dejan guardar los cambios. El texto del mensaje dice: "No tiene los permisos necesarios para guardar el archivo. Compruebe que ha tecleado el lugar correctamente y pruebe de nuevo."

El archivo modificado quedó asì:

#
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
# traditional Unix authentication mechanisms.
#
auth    sufficient      pam_thinkfinger.so
auth    required        pam_unix.so try_first_pass nullok_secure

---

### Post by leo_rockway on 2008-04-14
El archivo que querés modificar evidentemente no está en tu home (~) y vas a necesitar permisos de administrador para poder modificarlo. Si estás usando alguna aplicación de Gnome para abrir el archivo (como gedit) necesitas anteponer gksudo al comando:

Por ejemplo, correr esto desde una terminal:
```
$ gksudo gedit nombrearchivo
```

Si estás en consola usá sudo en lugar de gksudo (o kdesudo si estás usando kde -kate- ). Esto te va a pedir tu contraseña de usuario.

Lo que hace sudo es permitirte correr aplicaciones con permisos de super usuario o root (lo que en window$ se conoce como administrador). sudo significa Super User DO.

Para más información usá el comando man desde consola para leer los manuales:

```
 $ man sudo 
```

Por cierto, el signo pesos ($) adelante de un comando significa que se ejecuta como usuario y el signo almohadilla o numeral (#) significa que se ejecuta como root.

EDIT: recién entré un toque a la página que estás usando de consulta. Si no me equivoco el archivo que estás modificando es /etc/pam.d/common-auth .
Si estás en Ubuntu escribí esto en una terminal:

```
 $ gksudo gedit /etc/pam.d/common-auth 
```

Eso lo podés copiar y pegar (sin el signo pesos, claro) o podes escribirlo. Si decidís escribirlo fijate de usar la tecla tab para autocompletar la ubicación del archivo.

Edit2: quizás te convendría buscarte algún pequeño manual de comandos para consola para más o menos entender que estás haciendo acá. Nunca falta alguno que se quiere hacer el gracioso y te pasa comandos que pueden borrarte todo el disco rígido... Usar la consola no es para nada complicado, es muy útil, te puede sacar de situaciones de apuro (cuando X -la parte gráfica- deja de funcionar, por ejemplo) y además hay muchas tareas que se efectúan de forma mucho más rápida por consola. No digo que dejes de usar la interfaz gráfica, pero conocer los comandos nunca viene mal.

---

### Post by santisantermer on 2008-04-14
Muchas gracias. Ahi pude guardar los cambios. Reinicie la maquina pero no me pidio huellas. Que mas puedo hacer?
Santiago.

---

### Post by Hei Ku on 2008-04-14
Apreta CTRL+Alt+F1 y te va a aparecer la consola. Fijate si te aparece algun error ahi al tratar de loguearte con el dedo. Fijate en al wiki que hay varios errores comunes y como solucionarlos.
Para volver a la parte grafica, apretas Ctrl+Alt+F7

---

