---
title: "no puedo instalar el modem speedtouch thomson 330 de speedy en ubuntu 64bits"
date: 2008-04-16
forum: Argentina Team
---

### Post by pedunight on 2008-04-16
ya sé que hay miles de post sobre esto, pero probé de todo y no me funciona nada.

ahora me sale este error cuando intento conectar:

In file /etc/ppp/peers/speedtch: unrecognized option 'nas0'


alguien sabe que significa?

no entiendo nada!

tengo el ubuntu de 64 bits!! como hago para usar el modem!! ayudaaaa

---

### Post by guisheca on 2008-04-17
Yo creería que tenés que ser un poco mas explicito, por ejemplo, que tutorial utilizaste, que pasos seguiste hasta que llegaste hasta ahí etc. Así como lo pones no hay mucho que hacer.
Saludos.

---

### Post by srmantis on 2008-04-24
Usa el script de esta direccion:
[http://lopeztobal.googlepages.com/st_ubuntu_pppoe.tar.gz](http://lopeztobal.googlepages.com/st_ubuntu_pppoe.tar.gz)

Descomprimir e ingresar hasta llegar a la carpeta speedtouch 330.
Ahora a modificar los archivos con cualquier editor de texto (sin cambiar el nombre original):

archivo: speedtch

modificar la línea que dice:
user 'adslppp@telefonicanetpa'
por el nombre de usuario de la cuenta internet, por ejemplo:
user 'ads2555555@lineafull.terra'

archivo: secrets

modificar la línea que dice:
"adslppp@telefonicanetpa" "*" "adslppp"
por el nombre de usuario y clave de internet , por ejemplo:
"ads2555555@lineafull.terra" "*" "ads2555555"

archivo: dial

modificar la línea que dice, solamente si fuera necesario:
br2684ctl -b -c 0 -a 8.32
cambiar los valores VP.VC, por defecto es 8.32, para terra en chile es el mismo.
revisa los valores en esta tabla:
[http://www.linux-usb.org/SpeedTouch/faq/index.html#q12](http://www.linux-usb.org/SpeedTouch/faq/index.html#q12)

Los firmaware vienen incluidos en la carpeta, para la version 1,2 y 4 del speedtouch 330.


Ahora a instalar, abrir una consola:
ingresar dentro de la carpeta con el comando cd speedtouch330 
ejemplo: cd Escritorio/speedtouch330 (si la carpeta speedtouch estuviera en el excritorio)

una vez dentro de la carpeta ejecuta:
sudo sh instalar.sh


Hasta ese paso funciona para ubuntu 32 bits, pero hay un archivo que instala por defecto br2684ctl que no sirve para 64 bits, por eso hay que actualizarlo:

descarga el archivo br2684ctl desde:
[http://packages.ubuntu.com/gutsy/net/br2684ctl](http://packages.ubuntu.com/gutsy/net/br2684ctl)

obviamente eliges la opcion amd64 y luego como tiene extension deb, lo instalas directamente haciendo doble click.

Ahora ya tienes configurada la conexion, solo te falta reiniciar el sistema para que te conecte automaticamente.

La mayoria de la veces no te conecta automaticamente, asi que hay que ir a la consola:

conectar: crea la interface nas0 y ppp0

sudo /etc/init.d/dial

desconectar: cierra nas0 y con ello tambien ppp0
sudo killall br2684ctl

Desconectar y volver a conectar inmediatamente, especialmente para cambiar dirección IP:
sudo pkill pppd
sudo pppd call speedtch

El primer comando cierra ppp0 y el segundo lo vuelve a conectar, asi evitamos tener que cerrar nas0.


La solucion la he probado en Ubuntu 7.04 y 7.10, ambas en arquitectura 64bits (amd64).
La unica diferencia que en el 7.04 faltan varias librerias (libatm1, build-essential y dpkg-dev, se buscan en la misma página, tienen extension deb)

Tambien funciona para opensuse 64bits, pero el archivo br2684ctl viene dentro de linux-atm, linux-atm-devel y linux-atm-lib en formato rpm

---

### Post by faktorqm on 2008-04-25
llama al 911

---

