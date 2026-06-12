---
title: "How to para speedy tomson 330 speedtouch"
date: 2007-09-10
forum: Argentina Team
---

### Post by Gideon26 on 2007-09-10
1-http://www.speedtouch.com/download/drivers/USB/SpeedTouch330_firmware_3012.zip (este es el firmware)
2 - [http://rapidshare.com/files/14182268...226_1_i386.deb](http://rapidshare.com/files/14182268...226_1_i386.deb) que es el atm
3 hace sudo mkdir /lib/firmware/speedtouch 
4 descomprimi el archivo que bajaste SpeedTouch330_firmware_3012.zip  seria
sudo tar xzf SpeedTouch330_firmware_3012.zip 

5. cd SpeedTouch330_firmware_3012 luego  sudo cp -a *.* /lib/firmware/speedtouch
6 instala el paquete br2684ct_ ********** con un simple doble click basta jaja

luego reinicia la maquina cuando se inicia y entras de nuevo a ubuntu espera un rato y vas a ver las lucecitas del modem titilar eso quiere decir que se esta inicializando y que el firmware funciono.

luego configurar es mas sencillo vamos de nuevo a terminal y (suponiendo que tenes speedy) escribimos
sudo br2684ctl -b -c 0 -a 8.35
te va a hacer
br2684ctl[6767]: Interface “nas0&#8243; created sucessfully
br2684ctl[6767]: Communicating over ATM 0.8.35, encapsulation: LLC
br2684ctl[6767]: Interface configured

7 ahi haces sudo ifconfig nas0 up
8 sudo pppoeconf y te va a preguntar todos los datos nombre de usuario esa es la de speedy despues contraseña configuras todo lo que te pregunta que es sencillo.

luego en el escritorio hacete un documento vacio entra y dentro del documento escribi

#!/bin/bash
sudo br2684ctl -b -c 0 -a 8.35
sudo ifconfig nas0 up
pon dsl-provider

guardar

---

### Post by edd12river on 2007-09-10
es para el modem speedtouch de usb?, a mi el modem me prende, pero nose como conectarme, no instale nada yo...q puede ser?

---

### Post by Gideon26 on 2007-09-10
si es para el usb, solo segui el how to al pie de la letra y vas a ver que si te vas a poder conectar.
Saludos.

---

### Post by edd12river on 2007-09-11
no me baja el de rapidshare, me dice  file not found :(, y el otro me dice q no encontro nada en la busqeuda...

---

### Post by Gideon26 on 2007-09-12
Bueno como no pudiste bajarlo desde ese link los subi al foro podes bajarlos desde aca, los acabo de alojar aca los archivos.

Saludos

---

### Post by edd12river on 2007-09-12
tengo una duda, cuando arranco ubuntu el modem prende y las luces estan ocmo para q me conecte, segui los pasos sin instalar nada, pero cuando hago sudo br2684ctl -b -c 0 -a 8.35 me dice q no encuentra algo y cuando hago sudo pppoeconf me busca algo por placa de red, q hago?, cree el archivo en el escritorio, pero pienso q no puedo utilizarlo xq no instake algo, ahora pruebo de nuvo y te digo..


ya probe, me dice esto:

sudo tar xzf SpeedTouch330_firmware_3012.zip
tar: SpeedTouch330_firmware_3012.zip: No se puede open: No existe el fichero ó directorio
tar: El error no es recuperable: salida ahora
tar: Child returned status 2
tar: Salida con error demorada desde errores anteriores

cree la carpeta, y cuando quise descomprimir el archivo me lo dijo...nose q estare haciendo mal

---

### Post by Gideon26 on 2007-09-12
> **edd12river said:**
> tengo una duda, cuando arranco ubuntu el modem prende y las luces estan ocmo para q me conecte, segui los pasos sin instalar nada, pero cuando hago sudo br2684ctl -b -c 0 -a 8.35 me dice q no encuentra algo y cuando hago sudo pppoeconf me busca algo por placa de red, q hago?, cree el archivo en el escritorio, pero pienso q no puedo utilizarlo xq no instake algo, ahora pruebo de nuvo y te digo..


ya probe, me dice esto:

sudo tar xzf SpeedTouch330_firmware_3012.zip
tar: SpeedTouch330_firmware_3012.zip: No se puede open: No existe el fichero ó directorio
tar: El error no es recuperable: salida ahora
tar: Child returned status 2
tar: Salida con error demorada desde errores anteriores

cree la carpeta, y cuando quise descomprimir el archivo me lo dijo...nose q estare haciendo mal

jejej mil perdones mi error en el caso del archivo zip es

sudo unzip SpeedTouch330_firmware_3012.zip


saludos y en cuanto al br2684ctl me podrias decir que error tira o es cuando haces pppoeconf? te comento br2684ctl tienen que crear la conexion nas0 y luego la tenemos que montar con ifconfig nas0 up para que el pppoeconf tenga dispositivo que configurar conexion. me explico ?


con lo de unzip con eso deberia andar.

y con br2684ctl pasame los errores. asi sabemos si te falta alguna libreria o modulos cuales bajar. saludos.

---

### Post by edd12river on 2007-09-12
cambie por unzip pero me dice esto:

Utility for configuring RFC 2684 ATM/Ethernet bridging
ATM bridging is a way to extend Ethernet over an ATM network and is mainly used for DSL connections. This package contains the user space utility needed to configure the kernel driver.
This package is needed if you own an USB DSL modem and your connection uses one of these protocols: RFC 1483 bridged (RFC 2684 bridged), PPP over Ethernet (PPPoE). 

va, en realidad cuando pongo sudo unzip SpeedTouch330_firmware_3012.zip, me dice q no encunatra el archivo, y cuando pongo extraer buscandolo en vez de por un terminal me dice eso.... hay una cosa q no entiendo en el paso:
"5. cd SpeedTouch330_firmware_3012 luego sudo cp -a *.* /lib/firmware/speedtouch", cuando pones "*", q tengo q poner ahi?

desde ya muchas gracias

---

### Post by FlyerDie on 2007-09-17
... vos mismo te estas contestando a tu problema... :mad:
Si no te encuentra el archivo, porque seguis con los demas pasos!?!?!?!?!!?!

Estas parado sobre la ruta donde te fue bajado el archivo .zip? me parece que no...:)
Entonces, empeza por pararte dentro de donde fue bajado el archivo .zip, que mas que seguro es /home/TUUSUARIO/Desktop y desde ahi corre el sudo tar blabla... y segui con los pasos, no SALTEES!

Saludos

---

### Post by edd12river on 2007-09-17
el archivo no esta en el deskpot, pero lo pondre alli para q me sirva tu consejo, ya se q no sigo las reglas del foro, pero hace un mes q estoy con esto y cuando alguien se digna a ayudarme despues de dos o 3 respuestas desaparece...y nesesito usar esa pc, pero = el modem prende las luces y todo como para conectarme a internet, osea, q me reconoce todo y no tendria q instalar nada no?...me faltaria coonfigurarlo q es por eso q me saltie pasos, xq al ver q el modem prendia y funcionaba lo q hice fue tratar de configurarlo, pero me dice eso cuando pongo pppoeconf...por eso pregunte de nuevo...


gracias!

---

### Post by leo_rockway on 2007-09-17
La verdad que no se como sera ese modem, pero el mio solo con enchufarlo al tomacorriente prende las luces y se conecta a internet (aunque no este linkeado a ninguna computadora). asi que el hecho de que prenda las luces (en mi caso al menos) no es prueba de que ubuntu lo haya reconocido.

EDIT:
eh... hagamos de cuenta que no dije nada... yo tengo cablemodem, no adsl.

---

### Post by por100pre1 on 2007-09-17
Ya he visto bastantes dificultades en los foros con ese modem, y permitanme decirles que todos estos lios son culpa del proveedor de internet por suministrar tecnologia del siglo pasado. Los modems USB siempre requieren controladores. Para los que no han visto el Thompson 330 [aquí]("http://www.thomson-broadband.co.uk/codepages/content3.asp?c=7&ProductID=471") esta la descripción. Es un modem subestándar para estos tiempos. Evidentemente le tienen que salir casi regalados al proveedor de internet. Yo tengo un Thompson ST780 que funciona con casi cualquier sistema operativo sencillamente por que se conecta por Ethernet.
:guitar:

---

### Post by FlyerDie on 2007-09-18
si...si hablamos de costos el HUAWEI que da TELECOM Argentina tiene un precio de venta a consumidor final de U$15, y un precio de venta a TELECOM de U$4,5 ....Osea, es de cuarta tener un modem USB ya que imaginense la calidad de los componentes, descartando la problematica de hacerlos funcionar.

---

### Post by Gideon26 on 2007-09-18
Hola disculpen por la tardanza de responder, ajaj pasa que no unicamente uno reponde a los foros uno tambien tiene otras obligaciones, mas alla de formar parte del Ubuntu Linux User Group Argentina o como es mi caso del Lug regional (Lugna). Asi que edd12river no te enojes si? en cuanto al modem no es nada de otro mundo 1 y principal si estas usando feisty o una mas viejita como edgy, solo necesitamos el br2684ctl y los firmware del modem ya que el reconocer el modem nos lo hace el Hotplug cuando se inicia el sistema, lo que hay que tener en cuenta es que debemos tenerel br2684ctl de acuerdo a la arquitectura del SO que usamos por ejemplo si me baje el ubuntu Feisty fawn 7.04 32bits necesito el br2684ctl de i386 y si es el 7.04 de 64 necesito el de arquitectura de 64. 

Hasta vamos bien... supongo supongamos que el br2684ctl que bajaste es el de 32bits que es el que postee en el foro

lo vamos a hacer por consola.

en la consola cuando la abro uno siempre aparece en esta ruta


/home/Usuario* (este usuario es el que creamos al instalar el SO)


supongamos que el archivo *.deb  br2684ctl_20040226_1_i386.deb lo pusimos en una carpeta  no se Drivers

/home/Usuario*/Drivers

debemos hacer (recordemos que en linux se deben respetar las mayusculas y minusculas ya que el sistema los toma a las mayusculas como un caracter y las minusculas como otra osea que para el sistema no le es igual ( a) que (A) estamos? lo aclaro por si esto lo lee alguien que recien se inicia y esta acostumbrado a la consola de windows si es que la usa.


seria 
cd /home/Usuario*/Drivers
sudo dpkg -i br2684ctl_20040226_1_i386.deb

esto haria que el archivo se instale en su pc. que es lo que necesitamos


---------------------------------------------------------------------------------------


el Firmware lo necesitamos colocar si o si en /lib/firmware como los del modem que estan en el archivo zip son varios para que quede ordenado hacemos una carpeta dentro de /lib/firmware seria ej.

/lib/firmware/speedtouch

para crearlo debemos si o si acerlo bajo usuario superUsuario ya que es una carpeta de sistema entonces lo hacemos asi


sudo mkdir /lib/firmware/speedtouch

como necesitamos ponerles los archivos en esa carpeta hacemos asi

como en el ejemplo dijimos que lo pondriamos en la carpeta /home/Usuario*/Drivers

seria cd /home/Usuario*/Drivers
sudo sudo unzip SpeedTouch330_firmware_3012.zip 
luego hacemos 
cd  SpeedTouch330_firmware_3012 ya que esa es la carpeta que se creara al descomprimiry alli 
sudo cp -a *.* /lib/firmware/speedtouch

luego reinicia la maquina

y hace lo de sudo br2684ctl -b -c 0 -a 8.35 (8.35 o el valor vpi y vci de tu servidor de internet)

y segui el resto de la guia que coloque antes
acordate que primero debes hacer el br2684  y despues ifconfig ya que sino pppoeconf no va a tener que dispositivo buscar para configurar la conexion y despues si el script de consejo para no configurar todo a mano por consola para poder conectarte ok? si te sale algun error con br2684 al intentar instalar como yo te dije avisa para saber que modulo te falta si es que falta si usas feisty fawn 7.04 con gnome (ubuntu ) no creo que te falte nada ya que lo tiene casi todo de defaulth (libatm etc.) solo necesitas ese br2684 de todas maneras si sale un error haciendo las cosas como te dije avisanos asi chequeamos que esta mal en la pc o que le falta si o si el error postealo completo asi sabemos que es.
Saludos

de Ultima mandame un mail a la lista de uluga que a mi me llegan por mail

---

### Post by edd12river on 2007-09-18
Gideon26:
no me enojo, lo q me pasa es q me desespera q el servidor no me brinde ayuda, y los pocos q consigo q me ayuden son ustedes, y si se borran pienso q poray se cansaron ya q al no tener experiencia pregunto muchas cosas q poray son obvias...pero bueno, trate de instalar y me sale este error:


edd@edd-desktop:~/drivers$ sudo dpkg -i br2684ctl_20040226_1_i386.deb
Seleccionando el paquete br2684ctl previamente no seleccionado.
(Leyendo la base de datos ...  
88399 ficheros y directorios instalados actualmente.)
Desempaquetando br2684ctl (de br2684ctl_20040226_1_i386.deb) ...
dpkg: problemas de dependencias impiden la configuración de br2684ctl:
 br2684ctl depende de libatm1; sin embargo:
  El paquete `libatm1' no está instalado.
dpkg: error al procesar br2684ctl (--install):
 problemas de dependencias - se deja sin configurar
Se encontraron errores al procesar:
 br2684ctl


nose q puede ser...seguro ustedes sepan...pero bue...bueno, espero sus respuestas, y no importa si tardan, ya se q no estan todo el dia pendientes del foro...es obvio q hacen otras cosas...


nos vemos!


gracias! :)

---

### Post by por100pre1 on 2007-09-18
[libatm1]("http://fr.archive.ubuntu.com/ubuntu/pool/main/l/linux-atm/libatm1_2.4.1-17_i386.deb"). Instala esto primero.

y luego haz esto:

```
sudo apt-get install -f
```

---

### Post by edd12river on 2007-09-18
bueno, hice eso, pero me sale esto...

br2684ctl[5435]: Interface "nas0" created sucessfully
br2684ctl[5435]: Communicating over ATM 0.8.35, encapsulation: LLC
br2684ctl[5435]: Fatal: failed to connect on socket
edd@edd-desktop:~$ sudo br2684ctl -b -c 0 -a 8.35
br2684ctl[5456]: Interface "nas0" could not be created, reason: File exists
br2684ctl[5456]: Communicating over ATM 0.8.35, encapsulation: LLC
br2684ctl[5456]: Fatal: failed to connect on socket
edd@edd-desktop:~$ sudo ifconfig nas0 up

ahora cuando hago pppoeconf me reconoce, carga una barra en donde reconoce el modem, pero despues me tira un error me dice q el modem esta siendo utilizado o q otro comando pppoe lo esta usando...q puede ser?

---

### Post by matogrosso on 2007-09-25
Puede ser que te ayude:


[http://ubuntuforums.org/showthread.php?t=559395](http://ubuntuforums.org/showthread.php?t=559395)

---

### Post by edd12river on 2007-09-26
ahora lo veo, pero veniamos bien!, debe ser una cosa media tonta lo q me dice, nose q error es, pero como q crea el archivo pero depsues no lo puede modificar o leer o ativar,matogrosso ahi veo lo q me pasaste...


grax!

bye

---

### Post by edd12river on 2007-10-04
hice lo de la guia, pero me sigue saliendo lo mismo, como q no se puede activar o algo asi...q puede ser?

---

### Post by steve_ignorant on 2007-10-16
hola soy nuevo tambien en esto de linux, me di bastante maña ademas un ayudante de la facu es uno de los desarrolladores del linux de la facu y me tiro un par de ayudas, pero sigue *********** *** ***** el modem, 

explico que me ocurre ami.

1) pedi a speedtouch un driver mandando mails y todo, especificando la pc que tenia y la distri de linux que tengo(ubuntu7.04)
 
2) me un link en el cual decia todo paso a paso, con las tablas de los VCI/VPI y toda la bola y obviamente el firmware y todo... 

3) configuro todo, incluyendo los secrets, los enlaces y los puentes(pppo <----> nas0)

4) reinicio ubuntu, y las luces titilan joya, sin ningun problema... hasta que... taran taran... pongo en la consola... "pppd call speedtch" 

y ahi me tira, que A) o es invalida la atenticacion del PAP o...
                             B) time out waiting for PADO/PAD0(no distingui si era una O o un cero) packets unable tu complete pppoe discovery. 


para los que les interese, les dejo el link del howto que me pasaron los fabricantes del modem(esta en español e ingles) 
[http://www.linux-usb.org/SpeedTouch/ubuntu/index.html]("http://www.linux-usb.org/SpeedTouch/ubuntu/index.html") 


espero que me puedan dar una idea de que hacer o como hacer para que se conecte....

---

### Post by steve_ignorant on 2007-10-16
bueno gente, aca estoy posteando desde el ubuntu. hice andar el modem. una aclaracion que es lo que me dificulto hacer andar la conexion a internet.

en la parte que dice que tenes que hacer el archivo de texto "pap-secrets"/"chap-secrets" lo que hice yo sin darme cuenta fue ponerle esos nombres, cuando en realidad el archivo de texto va con el nombre SECRETS, y ahi lo instalas con los codigos que puse en el post de arriba. 

bueno, al que todavia no pudo hacerlo andar, le sugiero que siga ese instructico que es casi imposible que no lo tome. 

agur!

---

### Post by Valgaav on 2007-11-17
Holas! hago necrología del thread porqué es el mejor lugar para preguntar.

Tengo speedy y el thomson 330 usb y toda la bola, pero tengo una duda, (soy newbie de linux). El firmware que le bajo, me modifica el firmware físico del modem o simplemente me lo pone en una libreria del ubuntu para que lo reconozca?. Pregunto porque no quisiera que toque el firmware físico del modem. Instale el ubuntu con wubi, tengo windows xp y digamos instale el ubuntu para ver que onda, pero no quiero tener quilombos con el modem en windows xp despues.

bueno muchas gracias

---

