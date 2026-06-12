---
title: "SmartAX MT810 en un Feisty x64"
date: 2007-09-09
forum: Argentina Team
---

### Post by leandr0f on 2007-09-09
Hola Gente Linda! Quiero pedirles que me den una mano. Cómo hago para instalar el Modem de Arnet Argentina en un Feisty x64?
Tengo los paquetes necesarios para instalarlo en x86 pero no van para x64 (ya hice la prueba)
Gracias!

---

### Post by Gideon26 on 2007-09-09
(Hola bueno aca esta un how to echo en ubuntu España esta basado en el ubuntu 5.04 pero deberia ser similar a la que se usa en la distro que tenes

Regocijaos sufridos usuarios ADSL con este modem USB, pues Kubuntu/Ubuntu 5.04 ya trae el modulo del kernel listo para configurar y usar, es detectado en el inicio del sistema y es cargado, para verificar que el modulo esta cargado, abrir una terminal y ejecutar:

$ lsmod | grep eagle_usb
eagle_usb 120512 0
usbcore 107384 5 usblp,eagle_usb,ehci_hcd,ohci_hcd

Esto quiere decir, que el modulo de nuestro modem (eagle_usb) está cargado y listo para usarse. Para configurar los modems soportados por este modulo, se deben tener instalados los paquetes eagle-usb-data y eagle-usb-utils, que estan incluidos en el CD de instalacion de Kubuntu/Ubuntu 5.04, en una terminal ejecutar:

$ sudo apt-get install eagle-usb-data eagle-usb-utils

Luego de responder afirmativamente, eagle-usb-utils comenzara el proceso de configuracion (que no finalizara de buena forma, dara un error, no os preocupeis), donde se nos pediran datos importantes para realizar la conexion a nuestro proveedor de internet, estos datos son:

* Los parametros VPI y VCI, para Arnet de Argentina, VPI = 00000000 y VCI = 00000021 , cabe aclarar que estos valores deben expresarse en hexadecimal, asi, si yo pregunto al servicio técnico de Arnet me dicen que VPI es 0 y VCI es 33, 33 en hexadecimal es 21.
* El tipo de encapsulamiento, la mayoria utilizar PPP Over Ethernet (PPPOE)
* El nombre de usuario y clave de acceso.

Luego eagleconfig saldra con el error:

Error: pppoe cannot be launch. Exiting...

Sucede que pppoe no existe!, y Kubuntu no trae el paquete pppoe en el CD, pero aún asi trae el paquete pppoeconf que nos ayudara en la conexión.
Una vez que eagle-usb-utils salga con error, hay que editar el archivo de configuracion /etc/eagle-usb/eagle-usb.conf, para esto ejecutar en la termninal:

Si estan en Kubuntu:
$ sudo kwrite /etc/eagle-usb/eagle-usb.conf

Si estan en Ubuntu:
$ sudo gedit /etc/eagle-usb/eagle-usb.conf

(Vale, no aclaro mas, en Kubuntu el editor usado es kwrite, en Ubuntu es gedit algooooo

En este archivo limitense a cambiar el VPI y VCI segun concuerde con el de su proveedor, recordando que deben expresarse en hexadecimal, y que el numero es de 8 digitos (p.e.:00000021), asi tambien como el tipo de encapsulamiento, si no saben prueben con 00000001 (PPPOE) que es el mas usado, por ejemplo mi archivo se ve asi:

--------------------------/etc/eagle-usb/eagle-usb.conf--------------------------
# Options are set whith the following syntax:
#
# Name = Value
#
# where "Name" is the option name, and
# "Value" is the option value, specified
# in hexadecimal (without any prefix).
# Option names are case sensitive.
# Options that are commented out are specified
# with their default values.
#
# Other than VPI, VCI and Encapsulation,
# I really don't known what these options mean.

#POTS FOR EAGLE
OPTN0=80020066
# OPTN2=23700000
# OPTN3=00000000
OPTN4=00000000
# OPTN5=00000000
# OPTN6=00000000
# OPTN7=02CD8044
# OPTN15=09090909
VPI=00000000
VCI=00000021

#The following values are valid for encapsulation :
#MPOA_MODE_BRIDGED_ETH_LLC ----> 1
#MPOA_MODE_BRIDGED_ETH_VC ----> 2
#MPOA_MODE_ROUTED_IP_LLC ----> 3
#MPOA_MODE_ROUTED_IP_VC ----> 4
#MPOA_MODE_PPPOA_LLC ----> 5
#MPOA_MODE_PPPOA_VC ----> 6
Encapsulation=00000001

Linetype=00000001
RatePollFreq=00000009

STATIC_IP=none
ISP=manual configuration
LANG=es
ASYNCHRONOUS_START=1
--------------------------/etc/eagle-usb/eagle-usb.conf--------------------------

Una vez realizados estos cambios, debemos decirle al modem que tome estos nuevos parametros, para esto eagle-usb-utils, nos provee el comando eagleconfig, en una terminal ejecutar:
$ sudo eaglectrl -w
Si todo va bien veran como el modem se resetea, (parpadea el led de LINK hasta quedar encendida) y queda listo para conectarse a nuestro ISP. Si falla con el mensaje "timeout", intenten de nuevo con el mismo comando. En cambio si el error que les da es "Resource busy", intenten lo siguiente:

$ sudo rmmod eagle_usb
$ sudo modprobe eagle_usb
$ sudo eaglectrl -w

Para saber si el modem esta listo, el siguiente comando nos deberia informar la interfaz ethernet (virtual) usada por el mismo:

$ sudo eaglectrl -i
eth1

El resultado de este ultimo comando varia, segun tengas en tu PC una (sera eth1), dos (eth2) o ninguna tarjeta de red ethernet (el resultado es eth0).

Bueno, no queda mas que ejecutar pppoeconf, que se encargara de crear la conexion a nuestro ISP:

$ sudo pppoeconf

Este comando primero nos informara de las interfaces ethernet encontradas y nos pedira confirmación para escanearlas en busca de un modem PPPOE, les damos ok. Si todo va bien nos dira que la interfaz ethx (eth0,eth1,eth2...debe ser la misma interfaz ethernet que nos devolvio el comando "eaglectrl -i") esta lista para configurar una conexion de acceso, les damos ok a todas las preguntas, informamos de nuestro nombre de usuario y pasword provistos por nuestro ISP.
Una vez terminado, si ejecutamos el comando eaglediag, nos deberia informar que todo esta OK:

$ sudo eaglediag
Diagnostic (1.13 2004/08/29) driver eagle-usb 20050814113503
# System Information
Linux Kubuntu 2.6.10-5-386 #1 Tue Apr 5 12:12:40 UTC 2005 i686 GNU/Linux 3.1
Linux version 2.6.10-5-386 (buildd@terranova) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Tue Apr 5 12:12:40 UTC 2005
used : 3.3.4 (Debian 1:3.3.4-9ubuntu5)
# module loaded ? [ OK ]
# modem operational ? [ OK ]
# Config vpi/vci/encapsulation/isp : 21 1 (pppoe) manual configuration
# pppd launched ? [ OK ]
# Service for connection [ OK ]
# ping IP ? [ OK ]
# test DNS resolution ? [ OK ]
Complete diagnostic has been saved on /var/log/eagle-usb/eagle_diag_20050814113503.txt
Please keep only relevant data and remove personal informations.

Si os da error este ultimo comando, espero les sirva de guia esta lista:
# module loaded ? [ KO ]
Significa que el modulo del modem no esta cargado o el propio modem no esta conectado al PC, conectalo y comienza desde el principio, antes ejecuta "$ sudo modprobe eagle_usb", si os da error, el modulo no existe! (se quemaron mis premisas y deberias conseguir el paquete con el modulo para tu kernel)
# modem operational ? [ KO ]
El modem esta cargado pero esta inoperable, prueba desconectarlo (fisicamente, levanta el trasero, desconecta el cable usb que llega a el modem, deberia apagarse, si tu modem es alimentado por otra fuente apagalo, espera 5 segunos y conecta todo de nuevo como estaba, y enciendelo), luego intenta con los comandos:
$ sudo rmmod eagle_usb
$ sudo modprobe eagle_usb
$ sudo eaglectrl -w
Verifica otra vez con eaglediag

Luego, si deseas controlar la conexion/desconexion a tu antojo:
Para desconectarte:
$ sudo poff
Para conectarte:
$ sudo pon dsl-provider

Algo que queda en el tintero luego de esta configuracion es la seguridad (cortafuegos shorewall, que explicare en otro howto) y el odioso eagle-usb-utils que quedo mal configurado, para remediar esto ultimo, debes instalar el paquete pppoe... pero para esto debes estar conectado a internet y tener las fuentes de APT frecas y listas para instalar soft actualizado.
Para actualizar el software de tu Kubuntu/Ubuntu, debes editar el archivo /etc/apt/sources.list, antes realiza una copia de seguridad, ejecuta estos comandos:
$ sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
$ sudo kwrite /etc/apt/sources.list
----------------------------------------/etc/apt/sources.list----------------------------------------------

deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

## Uncomment the following two lines to fetch updated software from the network
# deb [http://ar.archive.ubuntu.com/ubuntu](http://ar.archive.ubuntu.com/ubuntu) hoary main restricted
# deb-src [http://ar.archive.ubuntu.com/ubuntu](http://ar.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://ar.archive.ubuntu.com/ubuntu](http://ar.archive.ubuntu.com/ubuntu) hoary-updates main restricted
# deb-src [http://ar.archive.ubuntu.com/ubuntu](http://ar.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://ar.archive.ubuntu.com/ubuntu](http://ar.archive.ubuntu.com/ubuntu) hoary universe
# deb-src [http://ar.archive.ubuntu.com/ubuntu](http://ar.archive.ubuntu.com/ubuntu) hoary universe

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

-----------------------------------------/etc/apt/sources.list------------------------------------------

Si miras bien, veras que todas las lineas estan comentadas (comeinzan con #), excepto una, la linea que define las fuentes del CD de instalacion de Kubuntu/Ubuntu:
deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted
Ahora, para tener las fuentes actualizadas debes descomentar (Remover los caracteres #) de todas las fuentes adicionales, que son las lineas que comienzan con deb o deb-src.
No te preocupes si las lineas adicionales no concuerdan perfectamente con las mias, depende de la seleccion de tu pais realizada en el proceso de instalacion, por ejemplo, la linea:
# deb [http://ar.archive.ubuntu.com/ubuntu](http://ar.archive.ubuntu.com/ubuntu) hoary main restricted
A alguien en España deberia aparecerle:
# deb [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) hoary main restricted
Y si estas en la tierra del tequila tu linea seria:
# deb [http://mx.archive.ubuntu.com/ubuntu](http://mx.archive.ubuntu.com/ubuntu) hoary main restricted
Luego de descomentar estas lineas, agregaras las siguientes que permiten obtener mayor cantidad de softwrae, a riesgo de no ser libre como librerias reporductores MP3, Video, etc.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

El archivo deberia quedarte asi:

-----------------------------------------/etc/apt/sources.list------------------------------------------
deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

## Uncomment the following two lines to fetch updated software from the network
deb [http://ar.archive.ubuntu.com/ubuntu](http://ar.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://ar.archive.ubuntu.com/ubuntu](http://ar.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://ar.archive.ubuntu.com/ubuntu](http://ar.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://ar.archive.ubuntu.com/ubuntu](http://ar.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ar.archive.ubuntu.com/ubuntu](http://ar.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://ar.archive.ubuntu.com/ubuntu](http://ar.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

-----------------------------------------/etc/apt/sources.list------------------------------------------
No tienes mas que guardarlo y en una terminal ejecutar (recuerda estar conectado!):
$ sudo apt-get update
Si todo salio OK, tu sistema esta listo para aptgear.
Por ejemplo, para instalar el visor de PDF de la firma Adobe (Acrobat Reader 7):
$ sudo apt-get install acroread
Apt-get no solo obtendra el paquete que deseas de internet, sino tambien todas sus dependencias (paquetes relacionados sin los cuales no podria funcionar), pero tener cuidado, pues algunas dependencias pueden forzarte a ELIMINAR paquetes de tu sistema actual dejandolo inutilizado, ten mucho ojo, y no respondas sin leerte bien toda indicacion y ante la duda no fuerzes tu suerte, te lo digo por experiencia.

Ok, en que andabamos?... instalar el paquete pppoe (por el cual eagle-usb-utils quedo colgado)
$ sudo apt-get install pppoe
Una vez terminado te recomendaria verificar que eagle-usb-utils no haya trasteado con la configuiracion de tu modem en /etc/eagel-usb/eagle-usb.conf.

-- ketamikih


Espero que te sirva proba con eso a medida que saten dudas consultanos de nuevo.

saludos

---

### Post by leandr0f on 2007-09-12
> **Gideon26 said:**
> 


Espero que te sirva proba con eso a medida que saten dudas consultanos de nuevo.

saludos

Lo voy a probar...
Pero a decir verdad, esperaba otra cosa. Y te explico por qué. Cuando me puse a buscar cómo instalar esta porquería de alfajor en un Ubuntu x86 encontré un HOW TO bastante bueno, para lo que tenía que descargar un par de archivos, instalarlos, configurar unos datos y luego correr un Script que configuraba e instalaba otras tantas cosas y me pedía unos datitos más (usuario de Arnet, pwd, DNS, etc) y listo; luego, con un par de comandos me conectaba. Pero por lo que vi acá (lo leí unua sola vez, quizá revisandolo de nuevo esté bien) es más complicado establecer la conección.
Ah! con el otro me permitía elegir si habilitar un Firewall o no.
De todos modos, promero lo pruebo, a ver qué onda.
Millón de gracias!

---

### Post by Gideon26 on 2007-09-12
tenes razon hay otro metodo mas para instalar y esta en este post [http://ubuntuforums.org/showthread.php?t=505374](http://ubuntuforums.org/showthread.php?t=505374)


mil disculpas jaja yo mismo lo coloque en ese post ajaj pasa que busque lo de lo tuyo y como no encontre ningun firmware te di este el largo!!! pero despues dias despues vi que ahi un firmware me puse a investigar mas y hice el otro how to que es mas sencillo, dicho de paso lo pude probar , en cuanto a lo que necesitas de diferente vos es el br2684ctl para arquitectura 64 nada mas.

Saludos!!!

---

