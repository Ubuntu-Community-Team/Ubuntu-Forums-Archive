---
title: "problema wifi broadcom y ubuntu"
date: 2007-09-01
forum: Argentina Team
---

### Post by niko_3100 on 2007-09-01
Hola bueno tratando de hacer funcionar mi wifi de mi compaq v3415 que por cierto no se bien que modelo de placa wifi tengo solo se que es una broadcom 802.11 b/g wifi nada mas. Intente instalarla porque mi ubuntu feisty fawn reconoces una placa wifi y le asigna eth1 pero no encuentra red ni nada como que al reconoce por la mitad al hard instale wifiradar y tampoco entonces siguiendo un tutorial hice todo tal cual y ahora ni siquiera me reconoces eso como que no tengo placa wifi mi pregunta es como hacer para por lo menos volver atras y que me siga reconociendo la eth1 y no volver a hacer ese tutorial que cada ves estoy mas lejos de poder conectar mi wifi a una red wifi. :(

---

### Post by DuckMan on 2007-09-01
ejecuta el comando lspcia y busca ahi el modelo de tu placa, igual te digo q si es broadcom te de unos pequeños dolores de cabeza. Yo tengo una 1390 y con una guia del foro la pude hacer andar perfectamente sin problemas, pero sin razon de un dia para otro dejo de andar bien la aplicacion de red de ubuntu, y tuve q usar el wifi radar para conectarme.

Ahora la reinstale y por ahora anda bien asi q :P fijese

---

### Post by niko_3100 on 2007-09-01
Hare eso yo tambien siguiendo un tutorial para ver si me conectaba intente pero algo hice mal o algo no era del todo cierto y ahora para ubuntu no tengo nada de nada solo me dice red cableada cuando antes me marcaba que buscaba redes wifi, como que reconocia la placa de red inalambrica pero no conectaba con ninguna red ni las veia ni nada.

---

### Post by niko_3100 on 2007-09-03
Bueno al final pude hacerlo como? Me baje el wine y instale el driver de windows xp del wifi broadcom y me lo tomo de una. Ahora tengo otro problema el nm-applet la primera ves que se conecto me dijo de poner una contraseña a la aplicacion aparte de la contraseña del router para acceder al wifi alguien sabe como sacar esta contraseña para que no pida contraseña? algun comando para resetear el nm-applet? porque me gusta que cuando arranque ubuntu ya este conectada y con esa aplicacion me pide la contraseña apenas arranca ubuntu...   :S

---

### Post by zspikes on 2007-09-03
creo q tengo la solucion a tu problema... te dejo una pequeña guia... notese los # adelante de cada instruccion... esto significa q debemos ejecutar cada comando como super usuario.
saludos!

VERIFICAMOS NUESTRA TARJETA

#lspci

02:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)

INSTALAMOS LO NECESARIO EN EL KERNEL

# apt-get install build-essential linux-headers-`uname -r` cabextract

INSTALAMOS ndiswrapper

# apt-get install module-assistant
# module-assistant auto-install ndiswrapper

INSTALAMOS EL DRIVER

# wget [http://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe](http://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe)
# mkdir bcm1390
# mv sp33008.exe bcm1390
# cd bcm1390
# cabextract sp33008.exe
# ndiswrapper -i bcmwl5.inf
# ndiswrapper -m
# depmod -a
# modprobe ndiswrapper
# ifconfig wlan0 up

---

### Post by niko_3100 on 2007-09-03
Buenisimo gracias por la guia mas o menos hice esos pasos y me lo tomo joya. Pero ahora quiero ver como sacar que el nm-applet me pide contraseña para buscar redes wifi a parte de la contraseña provistar por la red en si, no se com hacer. Si sabes el comando o algun archivito para tocar.. no quiero tocar mucho para no mandarme otro moco y volver a No tener wifi :(

---

### Post by zspikes on 2007-09-04
la verdad q no entiendo bien tu duda... yo para buscar redes uso el comando "$iwlist scan". Hice un pequeño script para conectarse.

```
#!/bin/bash

sudo iwconfig wlan0 essid $1 key $2
sudo dhclient

if [ $? -ne 0 ]; then
  echo "Ha habido un problema al conectarse a la red $1"
else
  echo "Conectado a la red $1"
fi
```

Pones "$conectar <ESSID> <pass>" y te conecta.
Espero q te sirva, saludos!

---

### Post by niko_3100 on 2007-09-07
NOOOOO!!!! intentando acceder a un wifi con ip statica me desconfiguro el wifi intento instalar todo de cero y me lo reconoce pero cuando reinicio me vuelve a no reconocer el wifi y tengo que hacer modprobe ndiswrapper para que me levante el wifi porque tengo todo isntalado bien. Esto antes no me lo hacia desde que quise meter ip statica borre todo y instale todo de cero pero nada el mismo problema.

---

