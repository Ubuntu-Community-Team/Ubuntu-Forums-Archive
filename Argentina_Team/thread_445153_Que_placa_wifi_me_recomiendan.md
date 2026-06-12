---
title: "Que placa wifi me recomiendan?"
date: 2007-05-15
forum: Argentina Team
---

### Post by undiaperfecto on 2007-05-15
Bueno el tema es que me gane una fonera  ([http://www.fon.com/es/](http://www.fon.com/es/)) y me quiero comprar una placa wifi para mi pc de escritorio, y antes de comprarme alguna y que despues no tenga drivers para ubuntu, prefieron consultarles cual me recomiendan comprar, alguna marca en especial o cosas asi.
Supongo que en windows no tendre drama porque siempre vienen con los drivers, pero ademas el 99% del tiempo estoy en ubuntu, asi que esa es la parte que mas me interesa.
Gracias desde ya.

---

### Post by fetova on 2007-05-15
Pues aca esta la pagina de tarjetas soportadas de ubuntu:

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

Saludos!

---

### Post by lavaramano on 2007-05-15
para.. aca hay data que me interesa

 te ganaste una fonera? **como?**

---

### Post by Gohalien on 2007-05-15
Yo tengo una TL-WN551G Chipset Atheros, si bien tuve problemas en la version Dapper drake (porque tenia los drivers madwifi desactualizado) en la version feisty simplemente no tuve que configurar practicamente nada y me funciona exelente, aunque por mi genio, no pude dejarle los drivers default y puse los ultimos drivers MadWifi (drivers para placas de red wireless con chipset Atheros) y tambien me anda exelente =)

Creeria que cualquier placa de red con chipset Atheros te tendria que andar bien. Para mas infomación podes leer:
[http://madwifi.org/wiki/Compatibility](http://madwifi.org/wiki/Compatibility)
Suerte !

---

### Post by undiaperfecto on 2007-05-15
Buenisimo, muchas gracias.
Voy a ver una D-Link DWL-G510 y despues cuento como me fue.

---

### Post by undiaperfecto on 2007-05-16
> **lavaramano said:**
> para.. aca hay data que me interesa

 te ganaste una fonera? **como?**

La gane en un sorteo en este blog 
[http://paiscambiante.wordpress.com/2007/05/07/3-foneras-para-sortear/](http://paiscambiante.wordpress.com/2007/05/07/3-foneras-para-sortear/)
Supongo que es alguien que trabaja para fon porque prometio sortear mas dentro de poco y por ahi dice que estaba trabajando con varsavsky.

---

### Post by undiaperfecto on 2007-05-18
Bueno finalmente les cuento lo que hice. Como no llegaba con el dinero para comprarme la placa D-Link, me compre una Encore ENLWI-G, el problema es que cuando llegue a casa antes de instalarla, consulto la lista de tarjetas soportadas y me encuentro que la que acabo de comprar no estaba. Bueno, la coloque, y tal cual, no funciona, no la detecta o no se que es lo que pasa, pero en el network manager no me sale ninguna opcion para buscar redes inalambricas. 
Estuve buscando un poco, pero la verdad no entendi nada, no se si alguno de ustedes tuvo este mismo problema y me puede dar una mano, igualmente tengo internet por cable, pero todavia no pude instalar la fonera :(

---

### Post by beuno on 2007-05-18
¿Que chip tiene la placa WiFI?
Es posible que necesites instalar algun driver propietario.

---

### Post by undiaperfecto on 2007-05-18
Hice un "lspci -v | less" y me salio esto:



00:0b.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
        Subsystem: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless

---

### Post by beuno on 2007-05-18
Tu placa efectivamente no tiene drivers open source.

Proba esto: [http://ubuntuforums.org/showthread.php?t=288341](http://ubuntuforums.org/showthread.php?t=288341)

o esto: [https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)
o esto: [http://ubuntuforums.org/showthread.php?t=380396&page=2](http://ubuntuforums.org/showthread.php?t=380396&page=2)

---

### Post by undiaperfecto on 2007-05-19
No hay manera, cuando trato de instalar ndiswrapper me tira un error.
Llego hasta el make distclean y bien.
Pero cuando hago make me tira este error:

> make -C driver
make[1]: se ingresa al directorio `/home/minotauro/ndiswrapper-1.29/driver'
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/minotauro/ndiswrapper-1.29/driver
make[2]: se ingresa al directorio `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/minotauro/ndiswrapper-1.29/driver/ndis.o
/home/minotauro/ndiswrapper-1.29/driver/ndis.c:39:47: error: la macro "INIT_WORK" recibió 3 argumentos, pero solamente tomó 2
/home/minotauro/ndiswrapper-1.29/driver/ndis.c: En la función &#8216;ndis_init&#8217;:
/home/minotauro/ndiswrapper-1.29/driver/ndis.c:39: error: &#8216;INIT_WORK&#8217; no se declaró aquí (primer uso en esta función)
/home/minotauro/ndiswrapper-1.29/driver/ndis.c:39: error: (Cada identificador no declarado solamente se reporta una vez
/home/minotauro/ndiswrapper-1.29/driver/ndis.c:39: error: ara cada funcion en la que aparece.)
make[3]: *** [/home/minotauro/ndiswrapper-1.29/driver/ndis.o] Error 1
make[2]: *** [_module_/home/minotauro/ndiswrapper-1.29/driver] Error 2
make[2]: se sale del directorio `/usr/src/linux-headers-2.6.20-15-generic'
make[1]: *** [default] Error 2
make[1]: se sale del directorio `/home/minotauro/ndiswrapper-1.29/driver'
make: *** [all] Error 2

Todo esto siguien el paso 2.
La opcion 3 no la probe, pero igualmente necesito tener instalado ndiswrapper, asi que es lo mismo.

EDIT: Hay un ndiswrapper en synaptic, es lo mismo?

---

### Post by undiaperfecto on 2007-05-20
Bueno finalmente me mande y trate de hacerlo.
Instale ndiswrapper desde synaptic, lo cual me ahorro un gran paso.
Consegui instalar el driver, consegui que la placa funcione, pero al reiniciar, me encuentro con un error en el administrador de preferencias de gnome, busco que puede ser y era el archivo /etc/network/interfaces
Asi que trato de encontrar el error y supongo yo que el problema esta en la siguiente linea:

> iface wlan0 inet dhcp
wireless-essid My_Essid
wireless-key XXXXXXXXXXXXXXXXXXXXXXXXXX
auto wlan0

Yo supongo que es porque estoy poniendo mal, la wireless-key, no se de donde obtenerla o si la tengo que crear yo y ponerla ahi. Hasta aca llegue, intente poniedo una clave nueva, pero nada, funciona todo barbaro, pero cuando reinicio se rompe de nuevo y ya no funciona mas la placa wifi. O tal vez estoy poniendo ese codigo en donde no debo, pero ya probe agregandolo al final del /etc/network/interface, y agregandolo donde dice auto wlan0 y nada.
Por si acaso adjunto como lo tengo configurado actualmente.


> auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid My_Essid
wireless-key ps2crew1977
auto wlan0

iface eth0 inet dhcp



auto eth0

Todo siguiendo esta guia:
[https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)

---

### Post by Steppenwolfalex on 2007-05-22
Atheros o Senao van de 10 sino tenes broadcom q son mas baratas.

Me sorprende te pasaron una lista y te tiraste al muere [-X

---

### Post by undiaperfecto on 2007-05-22
Si, la verdad que fue una locura, pero ya esta, lo logre hace 15 minutos despues de probar y probar.
Finalmente mi /etc/network/interfaces quedo de esta manera.

> auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

iface eth0 inet dhcp



auto eth0

---

