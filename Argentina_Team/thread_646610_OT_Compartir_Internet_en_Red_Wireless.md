---
title: "OT: Compartir Internet en Red Wireless"
date: 2007-12-21
forum: Argentina Team
---

### Post by Hernán-Amaya on 2007-12-21
Disculpen el OT pero soy nuevo en el mundo de las redes. Les explico cual es la situación, tengo mi red wireless ya armada con un AP tew-430apb a la cual estan conectadas mis dos pcs con ubuntu y la pc de mi viejo con winbug, mi viejo cambió el isp (antes tenia ADLS que se conectaba con discador lo hacia con la pc de mi viejo y tenía la conexión compartida) ahora con Fibertel no tengo idea como hacer para compartir la conexión. 

Intenté haciendo que el AP( lo configure para que use el dhcp) se conectara con el cablemodem pero no hubo caso, seguramente me esta faltando algo pero no se que hacer.

Gracias por su tiempo y les pido perdón por el OT

---

### Post by vk-cdg on 2007-12-21
Mirá, medio que toco de oido porque no tengo Fibertel, pero a un compañero de trabajo hace un año (se cansó y puso Telecentro) Fibertel le "clavaba" en el modem de cablemodem la MAC de la PC donde el técnico instalaba todo. 
En su caso, cuando el técnico se iba, sacaba de abajo de la cama una 386 sin disco y booteaba con un diskette de linux que tenía un proxy (bien livianito). En el soft del proxy impostaba la MAC de la PC donde el técnico había hecho la instalación y todo salía andando.

Periodicamente le pasaba que Fibertel quería comunicar algo y lo hacía bloqueando todos los puertos y pusieras la URL que pusieras en el navegador solo te mostraba una web de ellos donde estaba el comunicado o publicidad y una vez que uno aceptaba esa pantalla desde un botón se habilitaba la navegación nuevamente.
El problema que el tenía es que desde ese proxy que el tenía montado y del cual colgaban 4 PC no se podía visualizar esa pantalla así que tenía que desconectar el cable, conectarlo a la PC donde se había hecho la instalación (la de la MAC clavada) y luego de acepta el botón ese volver a conectar la PC que tenía el proxy.
Esto (según cuenta) se tornó insoportable cuando eso le pasaba hasta 3 o 4 veces por semana.
Ahí pidió la baja del servicio.

No se si esto sigue siendo así y mucho menos si es tu caso, pero lo cuento como anécdota.

Saludos

---

### Post by faktorqm on 2007-12-22
Hola, yo tengo experiencia en estas cosas. Si bien no es mentira que Fibertel traba la MAC address de las placas de red que el tecnico instala, tampoco es una verdad tan rotunda. Veamos el simple caso de que pasa si se me quema la pc y me compro otra, ¿me quedo sin internet? la respuesta es NO. Aún sin saber con exactitud que hace esta empresa con las MAC, lo que existe con seguridad son metodos para saltear esta proteccion (si es que es una proteccion).

En routers d-link, podes routear sin problemas, y hay un modelo en particular que tuve en mis manos (di-605) que trae una casilla de opcion para CLONAR la MAC address de la placa de red que vos le digas. No me parece lo mas recomendable, pero aun asi deberias buscar si esta opcion se encuentra en tu router. PERO PARA! Antes, vamos a configurar el router (el tuyo) como si nada hubiera pasado.

Mas o menos te cuento como tendrias que hacer. En la parte WAN de tu router, le tenes que poner DHCP, entonces te va a dar una direccion local. 

ejemplo de parte de WAN: 

ip: 192.168.1.5
mascara: 255.255.255.0
default gateway: 192.168.1.1

SI NO TE PONE AUTOMATICAMENTE LOS DNS, tenes que poner VOS A MANO como DNS los de fibertel, o la puerta de enlace. si no sabes cuales son fijate en la pagina o llama x telefono.

EN LA PARTE DE LAN DEL ROUTER, tenes que poner una red DISTINTA:

ejemplo d eparte LAN:

ip: 192.168.[SIZE="3"][COLOR="Black"]2[/COLOR][/SIZE].1
mascara: 255.255.255.0

a una pc:

ip: 192.168.[SIZE="3"][COLOR="Black"]2[/COLOR][/SIZE].2
mascara: 255.255.255.0
default gateway: 192.168.2.1
dns: 192.168.2.1

en la otra:

ip: 192.168.[SIZE="3"][COLOR="Black"]2[/COLOR][/SIZE].3
mascara: 255.255.255.0
default gateway: 192.168.2.1
dns: 192.168.2.1

Espero a ver sido claro. no soy buen profesor. Si esto no te anda, postea a ver que onda. salu2 y feliz navidad!

---

### Post by hernan blau on 2007-12-23
Hola. Yo tengo Fibertel y no tengo problema. Cuando compré la portátil fui a un negocio y compré un router marca Encore. Lo único que hice fue conectar con un cable de red el módem de Fibertel marca webstar y lo conecté al router. Uso las dos pcs con Ubuntu sin problemas, tanto con wifi como con extensiones vía cable de red desde el router. Siempre tenés el viejo recurso de que un  colocador se haga una changa. Suerte.

---

### Post by Hernán-Amaya on 2007-12-23
gracias por las respuestas! Me parece es que el problema es el AP, no es router, es solo un simple access point. si alguno sabe de algún buen router wireless para recomendar.

gracias nuevamente!

---

### Post by Oktubre on 2007-12-26
Hola, 

tengo Fibertel hace bastante, instale dos routers WiFi y no tuve drama. Las marcas son MSI y Encore, ambos son similares en su instalacion. 
Hay que hacer CLONE MAC ADDRESS al inicio y listo (despues seguir las instrucciones que figuran en el manual).

En tu caso no funciona porque un Access Point no tiene la funcionalidad del Router que es justamente compartir la conexion.

Espero que te sirva.

Saludos,

---

### Post by faktorqm on 2007-12-26
claro digamos vos con tu AP lo que en realidad tenes es un switch de cables digamos, vos necesitas, o bien un router por cable, o vende el ap que tenes y comprate un router wireless. Linksys es la segunda marca de Cisco Systems, asi que esos son muy buenos (hay que ver el precio :S). Un amigo tiene un MSI negro y plateado que es una bestia de router wireless, y tiene fibertel tambien y le va de PM. Fijate los precios. salu2!!

---

### Post by User21 on 2007-12-27
NO se si viene al caso, pero teniendo cablemodem Fibertel y con la aplicacion macchanger vivo cambiandole la mac al eth0 , para poder descargar desde sitios de filehosting... 

Si no tiene nada que ver, pues, disculpen! No la tengo muy clara, jejeje xD

---

### Post by jpmorelli on 2007-12-27
Aporto mi granito de arena y te digo que si bien MSI o Encore ( el primero mejor que el segundo ) son routers que andan, no lo pensaría dos veces teniendo a 20 dolares de diferencia un buen router Linksys. Poseen mucha mejor señal, no se producen microcortes, la calidad de los componentes es muy superior a los anteriores y por último y no menos importante tiene la firma Cisco atrás ya que esta adquirió Linksys hace aprox. 2 o 3 años. POr algo será no ?
Desde que tengo mi router Linksys wireless, mi vida cambió :lolflag:

---

