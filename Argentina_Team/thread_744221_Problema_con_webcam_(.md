---
title: "Problema con webcam :("
date: 2008-04-03
forum: Argentina Team
---

### Post by chispachips on 2008-04-03
Hola, muy buenas una vez más Argentina.

Resulta que yo tenía por ahí una webcam Trust 120 Spacecam que no utilizaba desde hace tiempo, realmente desde Windows no le daba un gran uso, puesto que la única vez que la probé en Linux fue en la primera versión con la que empecé, la 6.10, y sí la detectaba bien y todo con camorama y capturaba imagen pero entonces los clientes de mensajería no estaban tan empeñados en el uso de cams como ahora. Pues el caso es que ahora sí es cuando me apetecía usarla, ahora teniendo la 7.04, y la enchufo, se enciende el led que tiene y con el comando "lsusb" me la detecta como Microdia, sin embargo probé a bajar camorama y soltó una frase que más de una vez oí:

"Could not connect to video device (/dev/video0).
Please check connection."

Por eso mismo chequeé la conexión con lsusb y sí estaba ahí como dije antes; así que probé a ver qué me decía amsn en su configuración, me voy a Preferencias>Otras>Configurar cámara web , y lo primero que me dice en la ventana que aparece es: 

"Te encuentras detrás de un cortafuegos o enrutador."

(Cosa que es mentira, yo nunca instalé ningún cortafuegos y el router que yo sepa no tiene ninguno activado)

Así que le doy al botón de Configuración de vídeo, y veo que efectivamente detecta mi cámara web, en la columna de Dispositivos aparece así: v4l2: SN9C10x PC Camera , y en la columna de la derecha que pone Canales aparece ya como: Camera . Así que lo señalo en Dispositivos, y dentro señalo el Canal de Camera y pone: Your webcam uses a combinattion of palette/resolution that this extension does not support yet.

Así que no tengo ni idea de por qué me la detecta pero no funciona :confused: ... espero que me podáis ayudar, confio en vosotros :guitar:

---

### Post by Hei Ku on 2008-04-03
pone lspci y postea a ver que aparece para la webcam. Es importante saber el chipset, porque de eso depende cuan bien soportada esta.

---

### Post by chispachips on 2008-04-03
Gracias por la rápida contestación, aquí está el informe ;)

chispachips@mario-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
00:0a.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
00:0a.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
00:0a.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 62)
00:0a.3 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
00:0b.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 08)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8233 PCI to ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
00:11.4 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 30)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 440] (rev a3)


Eso es, pero de todas formas la antena es USB, no se si tendrá que ver por el comando, no es una pcmcia, tampoco tengo mucha idea de para qué sirve el comando jaja vosotros sabréis más, gracias ;)

---

### Post by Mauro22 on 2008-04-03
no seria lsusb ??



No se si sirve, pero probaste con TvTime para ver si captura algo de la webcam

sudo apt-get install tvtime

y despues, puedes probar con video0 o video1 asi:

tvtime --device=/dev/video0
o
tvtime --device=/dev/video1


Se que es para ver la tv pero en teoria tendria que leer cualquier entrada de video.

---

### Post by Hei Ku on 2008-04-03
> **Mauro22 said:**
> no seria lsusb ??



Mi error. :(

El comando seria lsusb

---

### Post by chispachips on 2008-04-04
Jaja por eso lo decía jeje, me extrañaba lo de pci ;) . Bueno, he hecho lo de TvTime, me lo he bajado y según lo arranco sale una pantalla azul entera como que no captura imagen ninguna y abajo a la izquierda pone: 

Frames too short from sn9c102
No puedo abrir dispositivo de captura /dev/video0.

Entonces he probado con tvtime --device=/dev/video1 y en vez de decirme lo anterior me cambia lo de arriba diciendo:

No existe el fichero ó directorio
No puedo abrir dispositivo de captura /dev/video1.

Entonces miré a ver qué me decía desde la consola ejecutando el primero tvtime --device=/dev/video0 , y me dice lo siguiente:

chispachips@mario-desktop:~$ sudo tvtime --device=/dev/video0
Ejecutando tvtime 1.0.2.
Leyendo la configuración de /etc/tvtime/tvtime.xml
I/O warning : failed to load external entity "/home/chispachips/.tvtime/tvtime.xml"
videoinput: Driver won't tell us its norm: Argumento inválido
videoinput: Can't get tuner info: Argumento inválido

    Your capture card driver: sn9c102 [SN9C10x PC Camera/usb-0000:00:0a.0-1/65563]
    does not support full size studio-quality images required by tvtime.
    This is true for many low-quality webcams.  Please select a
    different video device for tvtime to use with the command line
    option --device.

Supuestamente me dice que no soporta esas resoluciones.. pero es que ni en un programa ni en otro xD . Por cierto, puse "sudo" porque sin ello me decía que no tenía permisos para acceder al archivo tvtime.xml, así que le dije: todo tuyo xDDD, y eso es lo que me salió.

Eso es todo :S , me extraña tanto.. porque en mi 6.10 Edgy Eft me iba estupenda la misma webcam sin tener que hacer nada.. ni idea

Aquí os dejo el informe de lsusb, es Microdia el dispositivo de cámara web:

chispachips@mario-desktop:~$ lsusb
Bus 006 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0c45:600d Microdia 
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 0ace:1215 ZyDAS 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000
[B][U]
Edito[/U][/B]

Todo arregladoo ^^, al final investigando un poco por ahí logré encontrar el driver de mi webcam, que al parecer en la 6.10 funcionaba pero con la actualización del kernel ya no volvió a funcionar y había que bajarse el driver manualmente, además es comodísimo porque era un paquete .deb :p , aquí está la URL:

[http://www.linux-projects.org/modules/mydownloads/viewcat.php?cid=7](http://www.linux-projects.org/modules/mydownloads/viewcat.php?cid=7)

Y el enlace de descarga para i386 del módulo SN9CXX está donde pone "Download Now!Generic SN9CXXX Video4Linux1 & Video4Linux2 driver for Ubuntu" y al lado pone "Popular", pinchando en el título vamos. Esto sirve para Ubuntu Feisty Fawn, pero en esa página está para cualquier versión ;) .
Una vez descargado el .deb cuando se está instalando yo es que me creía que no terminaba en la vida pero es porque hace falta interactuar por parte del usuario, tienes que desplegar lo de Ver la terminal mientras se instala, y te pide que pongas Yes o No para aceptar la política esa, y luego te dice que si quieres eliminar unos archivos (al menos a mi si), todo es yes o no; que creo que debí meter la pata en algo porque yo puse Yes en todo y al reiniciar el PC se me colgó algo del driver de Nvidia porque me decía que no podía iniciar las X, así que ahora tengo que ver qué ha pasado con Nvidia pero bueno; esto por lo menos ya está solucionado.

 Mil gracias igualmente a esta gran comunidad que no ha parado de ayudarme desde que he venido :p

**_Edito 2 xD_**

Bua, creo que lo doy por imposible, parece ser que los drivers de Nvidia tienen conflictos con el driver recien instalado de la webcam, lo vi aquí: [http://www.elotrolado.net/hilo_Problema-webcam-en-linux_952945](http://www.elotrolado.net/hilo_Problema-webcam-en-linux_952945) , y amsn me seguía diciendo el mismo error con la cam de todas formas de la resolución; el único programa que me la cogía ahora era camorama pero con un tono de colores que no era el apropiado, yo tenía la piel gris xDDD; parece ser que esta webcam es un poco viejita y ya no soporta ese tipo de resolución; ya me compraré una nueva porque no merece la pena hacer todo esto y que se me vaya la gráfica xD, mejor retiro el driver que instalé y reinstalo Nvidia. Una vez más, gracias ;) .

---

