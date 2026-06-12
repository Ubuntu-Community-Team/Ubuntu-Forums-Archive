---
title: "Problemas con RED pcmcia"
date: 2008-05-20
forum: Argentina Team
---

### Post by anarko on 2008-05-20
Hola, acabo de instalar hardy en una notebook que tiene una placa de red pcmcia "tamarack" el problema es que me dice que no pude insertar tamarack.cis cuando pongo la placa pcmcia y de hecho no existe tal tamarack.cis y no lo encuentro por ningun lado, alguien tiene una idea.

Nota: en debian etch me habia pasado lo mismo pero el tal tamarack.cis estaba en /etc/pcmcia/algo y se llamaba tamarack.dat lo copie a /lib/firmware/tamarack.cis y ando 10 puntos, pero ahora en ubuntu no doy pie con bola.

PD: ya que estamos tambien tengo probelmas con un dongle wifi que conecta obtiene la IP por DHCP pero cuando voy a pinguear el router tira mas 10000 ms y despues pierde la coneccion, el mismo dongle pero en una pc de escritorio anda 10 puntos ( los 2 son ubuntu 8.04 la notebook es i386 y la de escritorio es x86_64 )

Conslucion estoy 100% desconectado :confused:  :(

Saludos.

---

### Post by faktorqm on 2008-05-20
Postea modelo y marca de la notebook, modelo y marca de la placa de red, version de ubuntu, si es de 32 o de 64 bits, y la salida del comando lspci.

---

### Post by anarko on 2008-05-20
gracias, ya lo soluciones, como dije falta el archivo tamarack.cis en /lib/firmware
baje el paquete de debian que contenia dicho archivo, lo copie y ando 10 puntos.

meintresa mas lo del donge usb wifi.
Paso los datos que me pedis igualmente.
Marca y modelo: Fujitsu siemens Lifebook C series

anarko@Laptop:~$ lsusb 
Bus 001 Device 002: ID 0bda:8187 Realtek Semiconductor Corp. 

Ubuntu 8.04 i386

Recomento el problema de la wifi : toma la IP del dhcp y cuando pingueo tira 2 o 3 respuestas de 2000000 ms y despues dice que la red es inaccesible.

dmesg : 
[  186.682027] wlan0: associated
[  186.682043] wlan0: CTS protection enabled (BSSID=00:40:f4:f8:c8:d7)
[  186.682056] wlan0: switched to short barker preamble (BSSID=00:40:f4:f8:c8:d7)
[  186.682580] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  196.702565] wlan0: no IPv6 routers present
[  365.611641] wlan0: CTS protection disabled (BSSID=00:40:f4:f8:c8:d7)
[  383.017041] wlan0: CTS protection enabled (BSSID=00:40:f4:f8:c8:d7)
[  428.984183] wlan0: CTS protection disabled (BSSID=00:40:f4:f8:c8:d7)
[  429.701773] wlan0: CTS protection enabled (BSSID=00:40:f4:f8:c8:d7)
[  441.577613] wlan0: CTS protection disabled (BSSID=00:40:f4:f8:c8:d7)
[  460.723039] wlan0: CTS protection enabled (BSSID=00:40:f4:f8:c8:d7)
[  518.566968] wlan0: CTS protection disabled (BSSID=00:40:f4:f8:c8:d7)
[  534.743180] wlan0: CTS protection enabled (BSSID=00:40:f4:f8:c8:d7)
[ 1143.342378] wlan0: RX deauthentication from 00:40:f4:f8:c8:d7 (reason=2)
[ 1143.342397] wlan0: deauthenticated
[ 1144.341024] wlan0: authenticate with AP 00:40:f4:f8:c8:d7
[ 1144.540944] wlan0: authenticate with AP 00:40:f4:f8:c8:d7
[ 1144.740869] wlan0: authenticate with AP 00:40:f4:f8:c8:d7
[ 1144.940793] wlan0: authentication with AP 00:40:f4:f8:c8:d7 timed out

---

