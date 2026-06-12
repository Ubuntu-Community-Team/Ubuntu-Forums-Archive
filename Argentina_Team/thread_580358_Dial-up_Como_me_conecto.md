---
title: "Dial-up Como me conecto?"
date: 2007-10-18
forum: Argentina Team
---

### Post by DavidRnR on 2007-10-18
Otra vez yo je :(

Bueno ya instale sactifactoriamente Ubuntu 7.10.

Me detecto mi modem...es un conexant rs56-pci.

Hice la cuenta pero no se que puerto ponerle ni como hacer para que marque.

Desde ya, Muchas Gracias

---

### Post by rretamar on 2007-10-18
Kubuntu tiene el utilitario kppp. Para instalarlo:

apt-get install kppp

Desconozco que usará Ubuntu, pero para salir del paso kppp te puede servir (a costa de consumir memoria cargando las librerías qt).

Saludetes !

---

### Post by DavidRnR on 2007-10-18
Bueno gracias, pero no entendi nada ja.

El asunto es que en ubuntu no tengo acceso a internet, por eso quiero configurar el modem y la cuenta.

Son 56k pero bue, a mi  me sirven para chatear y eso.

No se que comando es apt-get install kppp

---

### Post by atari130xe on 2007-10-18
Hola, yo todavía soy uno de los pocos que quedan que usan dial up para conectarse a la net:
1) llamá a tu proveedor de Internet y preguntale los DNS (primarios y secundarios) sinó buscalos en google, poné "DNS de: (ponés tu proveedor: Arnet, ciudad, etc.)
2) una vez obtenidos esos datos abrí una consola y escribí: sudo pppconfig (seguro te vá a pedir la clave que pusiste cuando creaste tu usuario (la clave de root)
se te abre un programa de configuracíon de Internet por modem y solo seguí los pasos, cuando te pide: dns primarios y secundarios poné los que hayas encontrado de tu proveedor.
3) pppconfig casi siempre detecta el puerto donde tenés el modem instalado en el caso que no sea así anda probando, el ttSy0, el 1, el 2 hasta que la pegues (de todas maneras hay otra herramienta que se llama wvdial que viene con Ubuntu, abri otra consola y tipeá: wvdialconfig y esa te tira la velocidad y puerto donde está tu modem.
espero te sirva la info.
abrazos
Jose

PD: 
Los dns de arnet son estos:
PRIMARIOS       200.45.191.35
SECUNDARIOS  200.45.191.40

los DNS de ciudad son:
PRIMARIOS         200.42.0.108
SECUNDARIOS    200.42.0.109

(esos van como ejemplo)

---

### Post by DavidRnR on 2007-10-18
> **atari130xe said:**
> Hola, yo todavía soy uno de los pocos que quedan que usan dial up para conectarse a la net:
1) llamá a tu proveedor de Internet y preguntale los DNS (primarios y secundarios) sinó buscalos en google, poné "DNS de: (ponés tu proveedor: Arnet, ciudad, etc.)
2) una vez obtenidos esos datos abrí una consola y escribí: sudo pppconfig (seguro te vá a pedir la clave que pusiste cuando creaste tu usuario (la clave de root)
se te abre un programa de configuracíon de Internet por modem y solo seguí los pasos, cuando te pide: dns primarios y secundarios poné los que hayas encontrado de tu proveedor.
3) pppconfig casi siempre detecta el puerto donde tenés el modem instalado en el caso que no sea así anda probando, el ttSy0, el 1, el 2 hasta que la pegues (de todas maneras hay otra herramienta que se llama wvdial que viene con Ubuntu, abri otra consola y tipeá: wvdialconfig y esa te tira la velocidad y puerto donde está tu modem.
espero te sirva la info.
abrazos
Jose

PD: 
Los dns de arnet son estos:
PRIMARIOS       200.45.191.35
SECUNDARIOS  200.45.191.40

los DNS de ciudad son:
PRIMARIOS         200.42.0.108
SECUNDARIOS    200.42.0.109

(esos van como ejemplo)

Muchas Gracias atari.

Te cuento, hice todo eso y termine en unas pantalla que no se que mas hacer.

Como hago para que marque?, no se, recorda que no se ni un comando de linux yo.

te dejo un screen en donde termine.

[http://img143.imageshack.us/img143/4629/pantallazomv2.png](http://img143.imageshack.us/img143/4629/pantallazomv2.png)

Aparentemente me dectecto todos los drivers, lo unico ,tampoco puedo usar la aceleracion de mi Nvidia 6200 porque cuando le doy para que se active quiere conectarse a un lugar, asique tb necesito internet para eso.

Quiero apretar marcar, y que marque 0610222....... jaja HELP!

EDIT: consegui el comando para detectar el modem, pero me dice que no lo encuentra.

      sudo wvdialconf /etc/wvdial.conf

escanea todo bien, pero me dice que el modem no esta.

---

### Post by atari130xe on 2007-10-19
listo si llegaste a esa pantalla es que lo configuraste.
Ahora para conectarte abris una consola y pones:
pon (y el nombre de la conexion que creaste con pppconfig)
para desconectarte en la misma consola escribis poff y listo
luego con synaptic podes instalarte gnome ppp que es un script (una rutina) que te permite hacerlo con un doble click es como un icono que podes poner en el escritorio para no conectarte por medio de la consola.

---

