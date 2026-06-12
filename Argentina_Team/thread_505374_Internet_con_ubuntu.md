---
title: "Internet con ubuntu"
date: 2007-07-20
forum: Argentina Team
---

### Post by Pabliich on 2007-07-20
**Hola amigos.. la verdad es qe ya estoy loco.. no se que aser pense qe ubuntuu no era tan complicado.. no se como hacer para conectarme a internet con ARNET mi moden Huawei SmartAX MT810.. leii unos tutos pero no me sirvieron cuando voi a accesorios y pongo terminal.. tipeoo lo qe me dicee y dice orden no encontrada.. ya no see qe hacer... si alguien me puede ayudar porfa..**

---

### Post by spg76 on 2007-07-20
El problema es no hay drivers de Huawei para Linux y el soporte para Linux de los proveedores de Internet es muy pobre en el mejor de los casos. En ambos casos no es un problema particular de Ubuntu.
De hecho, si en lugar de tener un modem USB, tuvieras un modem Ethernet, la instalación sería mucho más sencilla que en Windows.
En cuanto al error que te aparece en la terminal, tendrías que ser más específco para poder ayudarte.
Si queres podes ver un thread en el foro sobre este modem en [http://ubuntuforums.org/showthread.php?t=426944](http://ubuntuforums.org/showthread.php?t=426944)
Saludos.

---

### Post by Pabliich on 2007-07-20
**muchas gracias por responder amigo.. ya lo pude instalar con mi modem.. tube qe usar mucho la cabeza nada mas pero fue mas que sencillo.. jeje..**

---

### Post by User21 on 2007-07-21
Si pudiste instalar ese modem, haceme el favor de guiarme, kizas lo necesite para un amigo ke se va a pegar el crossover a Ubuntu! ;)

---

### Post by spg76 on 2007-07-21
Recién publicaron un COMO en nuestro sitio. Podés verlo en [http://ubuntu-ar.org/soporte/comos/modem-huawei-smartax-mt810](http://ubuntu-ar.org/soporte/comos/modem-huawei-smartax-mt810)

---

### Post by Tongax on 2007-09-05
Gente, como va? Che, mi problema es que estoy tratando de instalar el Huawei USB de Telecom con Fiesty Fawn 7.04 (Kernel 2.6.20-15-generic), y siguendo este Howto ([http://www.ubuntu-es.org/index.php?q=node/45097](http://www.ubuntu-es.org/index.php?q=node/45097)), el moden linkea, pero al tirar el pppoe-start, me aparecen los puntos, pero despues de unos segundos (10-15 +o-), me tira TIME OUT!

Los datos con los cuales yo configuro la conexion son estos:

DNS: 200.42.0.110/200.42.97.110
VPI: 0
VCI: 33

Yo estoy en Zona Telecom, con la conexion de Flash.

Alguien me puede ayudar o me puede corregir en que estoy haciendo mal POR FAVOR!!!!

Saludos, TongaX

---

### Post by marianom on 2007-09-05
Hola Tongax, gracias por visitarnos. 
Un tema: Por favor, con poner tu problema en un solo thread alcanza y sobra, no es necesario -y tampoco aceptable- que repitas tu post.

Gracias y a disposición por cual duda (aunque no se nada de tu modem).

---

### Post by Tongax on 2007-09-05
Mil disculpas Marianom... es que te soy sincero, estoy media desesperado por solucionar este quilombo que tengo porque ya estoy re podrido del Winchor, y aparte, porque la PC la uso para laburar.

Otra vez, mil disculpas.

Un Saludo.

---

### Post by marianom on 2007-09-05
Está todo bien, no hay problema.
Espera un rato ya que hay varios que están en horario laboral y no han podido ver tu consulta. No te preocupes que siempre se han resuelto esos problemas y esta vez no tiene porque ser la excepción.

Para ir ganando tiempo... ¿revisaste ya los posts existentes en este subforo con temas similares al tuyo? Capaz que ya hay algo posteado que te sirve.

---

### Post by Tongax on 2007-09-05
Gracias chabon....
si mire los foros de aca, y los de España... el tema particular mio, es que hago todo bien... pero en ningun foro hay detalles del mensaje de Time Out al levantar la conexion... para mi que estan mal los datos que pongo pero cuando llamo a Flash, me dicen que son esos... asi que no se che... igual gracias por la mano.

Saludos

---

### Post by leandr0f on 2007-09-07
Acá hay un COMO para este Modem, es para ubuntu 6.06, y sirve para 7.04
La diferencia está en que al comienzo dice de descargar de memoria unos módulos del driver que eran propios de 6.06 y que ya no se unsan en 7.04 por lo que esa parte ya no hace falta, solo hay que pasar por alto eso.

No solo está el COMO sino que están los archivos que hacen falta. Espero les sirva a todos los que lo necesiten desde hoy!

[http://rapidshare.com/files/53935382/Drivers_MT810_para_Feisty.rar](http://rapidshare.com/files/53935382/Drivers_MT810_para_Feisty.rar)

Cualquier problema me avisan?

---

### Post by edd12river on 2007-09-07
hola, me canse de postiar, nesesito ayuda para instalar el modem se speedy tomson 330 speedtouch, es por usb...y todas las soluciones q me dan son para placa de red...xfa, nesesito ayuda..


desde ya muchas gracias

---

### Post by Federick on 2007-09-09
Hola edd12river.

Esta es la guía posta que uso yo para mi modem Speedtouch 330:
[http://www.linux-usb.org/SpeedTouch/ubuntu/index-es.htm](http://www.linux-usb.org/SpeedTouch/ubuntu/index-es.htm)

Pero acá van los detalles que tenés que tener en cuenta:

Tenés que usar las instrucciones para PPPOE con vpi 8 y vci 35 (ya que sos de Speedy).

Tenés que instalar con el synaptic y el Cd de ubuntu esta librería:
**libatm** (no exacto pero va a salir) .

Y las intrucciones las tenés que seguir para versión Dapper en adelante.

Cuando no se conecta al reiniciar, en la terminal escribí:
sudo pppd call speedtch

Cualquier duda chiflá.

Saludos.

---

### Post by Gideon26 on 2007-09-10
Hola bueno lo de tu modem es sencillito no es tan complicado necesito que bajes:

1- [http://eagle-usb.org/ueagle-atm/non-free/ueagle-data-1.1.tar.gz](http://eagle-usb.org/ueagle-atm/non-free/ueagle-data-1.1.tar.gz) (este es el firmware)
2 - [http://rapidshare.com/files/14182268/br2684ctl_20040226_1_i386.deb](http://rapidshare.com/files/14182268/br2684ctl_20040226_1_i386.deb) que es el atm


3 hace sudo mkdir /lib/firmware/ueagle     

4 descomprimi el archivo que bajaste ueagle-data-1.1.tar.gz seria
sudo tar xzf ueagle-data-1.1.tar.gz 

5. cd uagle-data-1.1      luego sudo cp -a *.*  /lib/firmware/ueagle

6 instala el paquete br2684ct_ ********** con un simple doble click basta jaja 

luego reinicia la maquina cuando se inicia y entras de nuevo a ubuntu espera un rato y vas a ver las lucecitas del modem titilar eso quiere decir que se esta inicializando y que el firmware funciono.

luego configurar es mas sencillo vamos de nuevo a terminal y (suponiendo que tenes speedy) escribimos 
sudo br2684ctl -b -c 0 -a 8.35
te va a hacer 
br2684ctl[6767]: Interface &#8220;nas0&#8243; created sucessfully
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

y despues anda a las propiedades de ese documento y  en permisos donde dice ejecucion marcalo para que se tome como ejecutable ya que lo que acabamos de hace es un script. es para simplificarnos la vida cada vez que querramos conectarnos a internet, ya que solo deberemos hacer doble click y nos preguenta ejecutar mostrar o ejecutar en terminal, elige siempre en terminal nos habre la consola y nos pregunta nuestra contraseña de root se la damos y hace todo el resto por nosotros y se cierra solo.

espera unos segundos y vas a ver que tenes internet.

saludos espero que te haya ayudado este how to


Pd: por lo que estuve viendo sos de arnet en ese caso el vci y vpi es 0.33 (osea sudo br2684ctl -b -c 0 -a 0.33)

---

### Post by Federick on 2007-09-10
Hola Gideon26.
Pero él necesita para el Speedtouch, y no veo que esté soportado por ese script en la página que mencionás.
Creo que te referís al modem que inició la discusión.

Saludos.

---

### Post by Gideon26 on 2007-09-10
> **Federick said:**
> Hola Gideon26.
Pero él necesita para el Speedtouch, y no veo que esté soportado por ese script en la página que mencionás.
Creo que te referís al modem que inició la discusión.

Saludos.

bueno en ese caso tiene que bajar este firmware [http://www.speedtouch.com/download/drivers/USB/SpeedTouch330_firmware_3012.zip](http://www.speedtouch.com/download/drivers/USB/SpeedTouch330_firmware_3012.zip)
descomprimirlo como explique arriba y copiar el archivo a /lib/firmware reiniciar la maquina y se va a inicializar el modem cuando dejan de titilar las luces y quedan prendidas ya esta sincronizado ahi bueno el resto del how to y los valores vpi y vci de telecom es 0.33 

saludos espero que te sirva

---

### Post by leandr0f on 2007-09-12
> **Pabliich said:**
> **Hola amigos.. la verdad es qe ya estoy loco.. no se que aser pense qe ubuntuu no era tan complicado.. no se como hacer para conectarme a internet con ARNET mi moden Huawei SmartAX MT810.. leii unos tutos pero no me sirvieron cuando voi a accesorios y pongo terminal.. tipeoo lo qe me dicee y dice orden no encontrada.. ya no see qe hacer... si alguien me puede ayudar porfa..**

poné atención a si al comando que vas a ejecutar no le estés anteponiendo el $ o #
Otra posibilidad es que tengas qeu instalar antes un par de paquetes, que a lo mejor sean build-essential y libatm (los comandos son: sudo aptitude install build-essential y sudo aptitude install libatm)

Decinos qué comandos no podés ejecutar (orden no encontrada) para poder ayudarte mejor.
Éxito!

---

### Post by Montsegur87 on 2007-09-12
tengo el mismo modem , uso esta guia

[http://www.ubuntu-es.org/index.php?q=node/19203](http://www.ubuntu-es.org/index.php?q=node/19203)

solo que para configurar la conexion al final uso

```
$ sudo pppoeconf
```


Configuro todo

Conecto

```
$ sudo pon dsl-provider
```

Desconecto

```
sudo poff dsl-provider
```

---

