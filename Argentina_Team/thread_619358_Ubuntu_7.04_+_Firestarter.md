---
title: "Ubuntu 7.04 + Firestarter"
date: 2007-11-21
forum: Argentina Team
---

### Post by HomeroJS2006 on 2007-11-21
Firestarter tiene problemas con una placa que yo no tengo.
Ya hace dos semana que vengo luchando con este problema y quemandome las pestañas buscando la solucion.

Paso a explicarles la situación:
En la casa de mis viejos hay dos PC's.
Una con Ubuntu 7.04, con dos placas de red, una placa conectada a cablemodem, la otra conectada a un laptop con XP
La idea siempre es que la PC c/Ubuntu comparta / permita / de acceso a la conexión a internet al laptop con XP, nada del otro mundo.
Actualmente en Ubuntu las placas son eth0 (conectada a cablemodem) y eth1 (conectada a la red local)

Ahora el problema:
En algún momento eth1 pasó a llamarse eth2, desconozco el porqué.
Luego los nombres volvieron a ser los mismos: eth0 (conectada a cablemodem) y eth1 (conectada a la red local)
Esto provocó que Firestarter ande cuando quiere y cada tanto me diga "Hay un problema desconocido con eth2" (Eth2 no existe!)
Me cansé de Firestarter busqué otra solución, un script. Nunca anduvo.

Busqué dónde puede quedar información guardada sobre eth2 para borrarla, interfaces y otros archivos.
Pero la prueba de que todavía queda algo es evidente, Firestarter me sigue dando ese error, incluso reinstalandolo.

Agradeceré de antemano a quien sepa darme una mano o recomendación.

P.D.: Mas frustante todavía es ver lo facil y los "casos de exito" de la gente con el mismo objetivo que el mio que no tuvieron problemas.

---

### Post by faktorqm on 2007-11-21
> **HomeroJS2006 said:**
> Firestarter tiene problemas con una placa que yo no tengo.
Ya hace dos semana que vengo luchando con este problema y quemandome las pestañas buscando la solucion.

Firestarter es un frontend del paquete iptables, no administra dispositivos.

> **HomeroJS2006 said:**
> Ahora el problema:
En algún momento eth1 pasó a llamarse eth2, desconozco el porqué.
Luego los nombres volvieron a ser los mismos: eth0 (conectada a cablemodem) y eth1 (conectada a la red local)
Esto provocó que Firestarter ande cuando quiere y cada tanto me diga "Hay un problema desconocido con eth2" (Eth2 no existe!)
Me cansé de Firestarter busqué otra solución, un script. Nunca anduvo.

Busqué dónde puede quedar información guardada sobre eth2 para borrarla, interfaces y otros archivos.
Pero la prueba de que todavía queda algo es evidente, Firestarter me sigue dando ese error, incluso reinstalandolo.

Lo estas desinatalando bien? usaste la opcion --purge en el apt-get remove? te fijaste que no haya ningun script autogenerado? alguna carpeta estilo .firestarter en tu /home/usuario?

> **HomeroJS2006 said:**
> P.D.: Mas frustante todavía es ver lo facil y los "casos de exito" de la gente con el mismo objetivo que el mio que no tuvieron problemas.

No te desanimes, no es para tanto.

Asumo que estas usando ubuntu, si estas usando (K)(X)ubuntu cambian los nombres de los editores (para kubuntu es "kate" y para xubuntu es "mousepad")

Abri un terminal y poné:

```
sudo gedit iptablesconf.sh
```

Ahora copia y pegá esto (ojo! esto es solo para tu caso, donde eth0 es la del modem y la eth1 la otra pc):

```

#!/bin/bash

iptables --table nat --append POSTROUTING --out-interface eth1 -j MASQUERADE
iptables --append FORWARD --in-interface eth0 -j ACCEPT
echo 1 > /proc/sys/net/ipv4/ip_forward

```

ahora guardalo en esta ubicacion: ```
 /etc/init.d/
```

cerra el gedit, y en la terminal escribi:

```
sudo chmod 755 /etc/init.d/iptablesconf.sh
```

despues lo ejecutas: ```
sudo sh /etc/init.d/iptablesconf.sh
```

Ahora bien, para estar super seguros de que esto anda, la computadora que tiene XP la configuras como:

DIRECCION IP: 192.168.1.2
MASCARA DE SUBRED: 255.255.255.0
PUERTA DE ENLACE: 192.168.1.1
DNS primario: 192.168.1.1

y la interfaz de salida, ETH1 la configuras como:

DIRECCION IP: 192.168.1.1
MASCARA DE SUBRED: 255.255.255.0

La eth0 seguro la tenes en DHCP para que el ISP te dé la direccion IP. asi que no te preocupes. 

tips basicos para cualquier red. UNA VEZ ASIGNADAS LAS DIRECCIONES, probas:

desde el xp(abris un cmd): ```
ping 192.168.1.1
```
desde el gnu/linux(abris una terminal): ```
ping -c 4 192.168.1.2
```

los dos te tienen que contestar, si esto te contesta y seguis sin internet, desde el xp hace un: ```
tracert www.google.com
``` y ahi tiene que decir, sino pudo verificar el nombre de dominio o no. si te muestra una direccion IP pero paquetes perdidos, postea y lo vemos.

Espero que te haya servido. salu2!

---

### Post by HomeroJS2006 on 2007-11-21
1ro que nada Gracias faktorqm

Y si, esta PC tiene Ubuntu, no Kubunto ni otro.
- Lo que es Firestarter +o- lo entendí buscando la soluc.,x eso probé con un script.
- La desinstalacón la hice desde el 1er ítem del menú de aplicaciones, destildando Firestarter. Y luego borrando el directorio y lo que tenía dentro.
- Voy a probar además con el comando apt-get remove xxx --purge y a buscar si queda algo.
- El script que había probado a simple vista es parecido al que me sugeris, el tuyo parece mas sencillo.
- La config. que me sugeris p/ la PC con XP es tal cual, excepto "DNS primario: 192.168.1.1", donde de algún tutorial saqué que debían ir los que yo tenía en la maq con ubuntu (q son los del ISP): Probaré esto también.

El resto lo pruebo hoy al salir del laburo y posteo el resultado.

Lo que es innegable es la cant de cosas q voy aprendiendo a medida que no soluciono nada, config, uso de scripts, asign de permisos, etc (JA!)

---

### Post by Mafber on 2007-11-21
Hola HomeroJS2006!!
Te hago una pregunta: vos estas cambiando el tipo de conección de tu modem? 
Te pregunto esto porque cuando cambio la conección del modem a la pc de red a la de usb te cambia de eth0 a eth1 (2 o 3). Cuando me pasaba esto, lo que tenia que hacer era cambiar en el Firestarter la configuración (basicamente decirle cual era el nuevo despositivo  eth1)
Suerte!!!

---

### Post by HomeroJS2006 on 2007-11-21
> **Mafber said:**
> Hola HomeroJS2006!!
Te hago una pregunta: vos estas cambiando el tipo de conección de tu modem? 
Te pregunto esto porque cuando cambio la conección del modem a la pc de red a la de usb te cambia de eth0 a eth1 (2 o 3). Cuando me pasaba esto, lo que tenia que hacer era cambiar en el Firestarter la configuración (basicamente decirle cual era el nuevo despositivo  eth1)
Suerte!!!

No Mafber, siempre conexiones LAN. 
El que eth1 se haya autobautizado como eth2 en algún momento, y que luego sin aviso vuelva a su nombre anterior (eth1) para mi es un misterio. Como el triang de las bermudas, la ult elección de Cordoba o la calavera de cristal.

No, en serio, doy por hecho que no va a volver a suceder ese cambio. Basandome en lo anterior intento darle una solución antes de seguir escuchando quejas de mi flia.

Gracias Mafber.

---

### Post by faktorqm on 2007-11-22
> **HomeroJS2006 said:**
> 
- Lo que es Firestarter +o- lo entendí buscando la soluc.,x eso probé con un script.
- La desinstalacón la hice desde el 1er ítem del menú de aplicaciones, destildando Firestarter. Y luego borrando el directorio y lo que tenía dentro.
- Voy a probar además con el comando apt-get remove xxx --purge y a buscar si queda algo.


Cuando arrancas firestarter por primera vez te aparece un wizard para configurar compratir la conexion a internet. cuando borres todo y borres las configuraciones y todo eso capaz eso te lo hace de una.

> **HomeroJS2006 said:**
> 
- El script que había probado a simple vista es parecido al que me sugeris, el tuyo parece mas sencillo.
- La config. que me sugeris p/ la PC con XP es tal cual, excepto "DNS primario: 192.168.1.1", donde de algún tutorial saqué que debían ir los que yo tenía en la maq con ubuntu (q son los del ISP): Probaré esto también.


Teoria de redes: la puerta de enlace, se utiliza cuando un paquete es enviado a otra red, es decir, se envia, como no corresponde a ninguna de las ip's asignadas a esta red, se desconoce, pero por defecto lo envia a la puerta de enlace, entonces lo envia y de ahi se despreocupa. 
Ahora bien, si pones [www.google.com](www.google.com), esa ip no esta en tu red, por lo tanto la va a enviar a la puerta de enlace. la puerta de enlace va a enviar la peticion afuera y los dns de la otra placa son los que van a hacer el trabajo de encontrar, que son los del isp. (en realidad ellos son los que te van a dar la ip pero bueno).
ahora bien, si vos pones los dns del isp directamente, que ocurre? veamos: los dns no estan en nuestra red, y google tampoco, entonces para resolver los nombres de dominio......... utiliza la puerta de enlace! que es la direccion de la placa que contiene los dns del isp. 

we, suerte con eso y cualquier cosa, como ultima opcion, borramos iptables, firestarter, y todos los archivos de configuracion, y arrancamos de cero. salu2!

---

### Post by HomeroJS2006 on 2007-11-22
> **faktorqm said:**
> 
```

#!/bin/bash

iptables --table nat --append POSTROUTING --out-interface eth1 -j MASQUERADE
iptables --append FORWARD --in-interface eth0 -j ACCEPT
echo 1 > /proc/sys/net/ipv4/ip_forward


Bueno, +o- te cuento como sigue.

Reemplacé el script que tenia antes por este que me sugeriste.
Al menos pude hacer ping de vuelta con resultados OK desde los dos lados.
Pero al hacer desde XP "tracer www.google.com" no anduvo.

Ademas eth1 volvió a autobautizarse como eth2! (Esto es cada vez mas divertido)
Al hacer un ifconfig eth1 ya no existe, solo tengo eth0 y eth2 (!)

Al final cambie interfaces y la dejé asi:
[CODE]
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth2
iface eth2 inet static
address 192.168.0.1
netmask 255.255.255.0

```

Envalentonado porque al menos los ping llegaban reinstalé Firestarter.
Me sigue dando un error pero ya no es el mismo, ya no menciona eth2 (será poque ahora es la interface que vale? Desconozco)

Resultado: La PC con XP volvió a tener internet, medio raro y todavia no reinicié la PC c/Ubuntu.

Seguiré averiguando para sacarme la duda y posteo una solución definitiva si la encuentro por si a alguien le llega a pasar lo mismo.

Saludos y gracias.

---

### Post by BiTFx on 2007-11-28
> **faktorqm said:**
> 
 
Ahora bien, para estar super seguros de que esto anda, la computadora que tiene XP la configuras como:

DIRECCION IP: 192.168.1.2
MASCARA DE SUBRED: 255.255.255.0
PUERTA DE ENLACE: 192.168.1.1
DNS primario: 192.168.1.1

y la interfaz de salida, ETH1 la configuras como:

DIRECCION IP: 192.168.1.1
MASCARA DE SUBRED: 255.255.255.0

La eth0 seguro la tenes en DHCP para que el ISP te dé la direccion IP. asi que no te preocupes. 



 
Hola, gracias por la información, pero ¿como quedaría en mi caso todo esto, ya que Speedy le asigna a la placa de red (eth0) conectada al Modem ethernet la direccion 192.168.1.10 y la puerta de enlace 192.168.1.1?
 
Supongo que entrarian en conflicto si uso la configuracion que vos pones acá. 
 
¿de que manera quedaría todo para que la placa eth1 que es la que se conecta con otra pc que tiene XP se configure como 192.168.0.1?
 
Corregime cualquier cosa, soy nuevo en esto.
 
Gracias

---

### Post by faktorqm on 2007-11-29
perdona ke tarde en responderte, es que no encontraba el post xD

la cosa es asi, si vos te fijas en el script rutea por interfaces, no por redes. ahora bien,  el modem te da la ip automaticamente, pero, si vos pones una ip fija, el modem se da cuenta de que esta ocupada y no la asigna. lo que veo es que tenes el modem configurado en modo router, por lo tanto para estar seguro de que esto te anda (capaz si pones todo en la misma red alcanza, pero vamos a hacerlo de otra manera) basta con configurar eth1 y la compu con windows en otra red.

La computadora que tiene XP la configuras como:

DIRECCION IP: 192.168.2.2
MASCARA DE SUBRED: 255.255.255.0
PUERTA DE ENLACE: 192.168.2.1
DNS primario: 192.168.2.1

y la interfaz de salida, ETH1 la configuras como:

DIRECCION IP: 192.168.2.1
MASCARA DE SUBRED: 255.255.255.0

we, espero que te haya servido, contame como te fue y que problemas tuviste. hace los pings obvio que puse antes para probar si """se ven""" bien las pc's. salu2!!

---

