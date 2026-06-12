---
title: "Wireless Router y conexión ADSL"
date: 2007-05-29
forum: Argentina Team
---

### Post by jajajavi on 2007-05-29
Cayó en mis manos un [**Asus 240 MIMO WL-566qM**]("http://www.zdnetindia.com/zdnetnew2007/index.php?action=pro_overview&prodid=1599") y tengo un Cisco 677 con el que actualmente me conecto a internet. Quiero armar una red wireless desde Ubuntu pero no tengo idea. Agradezco todo tipo de tutoriales, howtos o sugerencias.

---

### Post by jpmorelli on 2007-05-29
Bueno...es una pregunta un poco amplia... por donde empezar, a ver... tenés placa wireless en tu PC ? Qué marca ? Si la tenés, te la reconoció Ubuntu ?
No es dificil, solo tenés que seguir un par de pasos para poder manejarte con seguridad con tu red inalambrica y nada más...tirá mas datos a ver como te podemos ayudar.
Yo tengo un router Linksys y una wireless 3com en mi PC y funciona todo bien, la uso con WEP de 64 bits ( modesta seguridad si , y el que quiera romper el broadcasting que lo haga y lo dejo navegar 2 días por saber un pocquito :) )
;)

---

### Post by jajajavi on 2007-05-30
El plan es este:
[IMG]http://www.pxweb.com.ar/sitio/files/images/wifi_casa.preview.JPG[/IMG]

El Cisco677 se enchufa al Router y la pc se conecta a través de la placa ethernet. Al menos así dice el manual que funciona la cosa, el problema es que lo explica para windows. La placa wireless de la laptop funciona con ndiswrapper. ¿Por dónde empiezo?

---

### Post by jpmorelli on 2007-05-30
Perfecto ! Si ya tenés entonces la placa wireless configurada en la notebook tenés que ingresar al router wireless ( desde la PC ) para administrar la conexión WiFi.
Generalmente la administración es desde el navegador, en la dirección 192.168.0.1 o 192.168.1.1
Te va a preguntar usuario y contraseña y vas a entrar a la consola de administración del router.
En la parte de configuración wireless seteas el SSID, que no es más ni menos que el nombre que le vas a dar a tu red WiFi. Ponés el nombre que quieras, para identificar tu red en caso de que haya más de una dando vueltas por el aire. 
Seteá también que utilize algún protocolo de seguridad para que no cualquiera tenga acceso a tu red desde una inalambrica, yo empezaría por WEP, es simple y casi todas las placas tienen la opción. Elegí una contraseña de 64 bits o 128 ( dependerá de cuantos caracteres de clave quieras utilizar ) y grabás los cambios.
Desde la notebook habilitas desde network-manager la actividad inalambrica o te fijas con el comando :
iwconfig donde esta tu placa y seteas la misma para el SSID que elegiste, utilizar WEP  y modo DHCP. Cuando quiera conectar te va a pedir la contraseña WEP, la ponés y deberías estar conectado. :D
Cualquier cosa chiflá !

---

### Post by cerbexxx on 2007-06-07
Buenas, yo soy noob en el Ubuntu y ando queriendo hacer lo mismo. En cuanto a la configuracion del router wirelees o del modem ADSL, me las apaño bien.
 El problema es en la placa de red wirelees para la PC con Ubuntu. No se cual comprar de las que se consiguen en nuestro mercado.
 Es decir basicamente.:
                      ¿¿Cúal compro para no renegar como un animal, para que el Ubuntu me la reconosca??

 Despues de eso creo que con seguir los pasos de configuracion de la placa se logra una conexion. Despues tenía pensado ponerle al router wirelees que verifique la MAC de la placa de red para dejarla navegar y al router o al modem ponerle PAT con solo dos direcciones IP. La de la PC principal y la que tiene Ubuntu.

---

### Post by jajajavi on 2007-06-11
> **Gohalien said:**
> Yo tengo una TL-WN551G Chipset Atheros, si bien tuve problemas en la version Dapper drake (porque tenia los drivers madwifi desactualizado) en la version feisty simplemente no tuve que configurar practicamente nada y me funciona exelente, aunque por mi genio, no pude dejarle los drivers default y puse los ultimos drivers MadWifi (drivers para placas de red wireless con chipset Atheros) y tambien me anda exelente =)

Creeria que cualquier placa de red con chipset Atheros te tendria que andar bien. Para mas infomación podes leer:
[http://madwifi.org/wiki/Compatibility](http://madwifi.org/wiki/Compatibility)
Suerte !

aparecido en el post [SIZE="3"][COLOR="Red"][Que placa wifi me recomiendan?]("http://ubuntuforums.org/showthread.php?t=445153&highlight=wireless")[/COLOR][/SIZE]

---

### Post by jajajavi on 2007-06-13
Tenía la wifi funcionando perfectamente y anoche empezó a andar "a medias", andaban algunas páginas: google (aunque sólo los caché), gmail y no recuerdo qué otras más. Reseteé el modem adsl y el router inalámbrico y todo volvió a la normalidad, pero hoy empezó a andar de la misma forma, volví a resetear los aparatejos y sigue sin andar. Ahora estoy desde windows con el modem directamente conectado a la pc. Toda ayuda es bienvenida.

---

### Post by jajajavi on 2007-06-13
Bueno, ahora reinicio Ubuntu y vuelvo a poner los cables como antes (ver imagen) y la cosa funciona. Me gustaría saber qué puede estar pasando... disculpen las molestias.

---

### Post by mprizmic on 2008-01-05
hola jmorelli
hice lo que decìs en tu post pero no logro conectarme con seguridad WEP. 
mi configuraciòn es 
placa 
Broadcom BCM94311MCG wlan mini-PCI (rev 01)
Ubuntu es 7.10
El router es un LinkSys WRT54G

la configuro manualmente desde el ìcono de la taskbar. Luego desactivo y vuelvo a activar. Cuando voy a ver las redes inlàmbricas, la mìa me la reconoce inclusive me da el porcentaje de calidad de la conexiòn, pero el navegaro no llega a ningùn lado. 
Si no pongo clave WEP navego sin problemas
Que puedo hacer con esto? hice varias pruebas y no se me ocurre nada
Muchas gracias
Marcelo

---

### Post by faktorqm on 2008-01-05
jajajavi: perdoname pero lei tus posts 3 veces y sigo sin entender que queres hacer. de que imagen hablaS? 

marcelo: conviene usar wep-pk2 a 128 bits. eso lo habilitas en el router, despues en la placa de red. (en ambos ingresas la misma clave ;) )

a todos: a parte de la wep-pk2, habiliten el filtrado por mac, y desactiven el dhcp y servidores de impresion si tienen y todo tipo de conecciones remotas al router.


salu2!

---

### Post by mprizmic on 2008-01-06
faktorqm
el router linksys lo configurè asì:
en "esguridad inalàmbrica" le puse WEP con 128 bits. Todo ok.

En "configuraciòn inalàmbrica avanzada" dice que la configuraciòn puede ser tipo "clave compartida" o "automàtico" (que equivale a "sistema abierto"). Sonlas mismas opciones que tengo en el linux de la laptop que estoy tratando de conectar. Si selecciono "sistema abierto" entonces el help del router dice que no usa WEP ni en el emisor ni en el recptor para autenticar. Si uso "clave compartida", para que el WEP sea usado, entonces no conecta. 

Puse lo de la MAC address pero sacar el DHCP no me conviene porque si me voy con la laptop con IP fija a otra red, voy a tener que andar tocando la configuraciòn cada vez.

Un saludo
Marcelo

---

### Post by faktorqm on 2008-01-06
claro, hice eso exactamente en una pda de mi """"""""suegro""""""""" (jejejej) que corria windows mobile y cuando ponia clave compartida, me pedia la contraseña, le ponia la que habia puesto, reiniciaba esa cosa y cuando arrancaba conectaba de una. yo recuerdo haberlo hecho con 64bits wep-pk2. la verdad nunca tuve tecnologia wireless con linux, asi que hago un poco de agua en este tema. Capaz alguno con mas experiencia en esto te puede ayudar mejor, por ahora te diria que pruebes con 64 bits a ver que pasa.
Lo del dhcp, es un tema, o sea, si filtras por la mac de tu notebook (y/o de las compus que tengas conectadas) y por la clave wep, no deberias tener problemas de "robo" de señal. Yo vi por ahi 1500 herramientas para robar conexiones, la verdad son muy buenas, y hacen lo que dicen hacer, pero el filtro digamos mas "impasable" es la wep-pk2 a 128 bits.
Despues tambien vi unos routers que lo que hacian eran darte conexion por proxy con contraseña, pero eso es mas dificil configurarlo que la seguridad que te da, de todas maneras una vez conectado a tu red digamos que si se conectan a tu pc es lo mismo, por eso es importante el filtrado por mac, aunke como dije antes, con un linux y unas herramientas, es lo mismo que nada. Es todo un tema la seguridad con wireless :o
salu2!!

---

### Post by Duyos on 2008-01-06
hola, perdon que me entrometa pero es posible que tu ISP no te este asignando una IP fija, esto quiere decir que el loco te asigna una IP con fecha de vencimiento enganchada a la MAC Address de tu placa.
Yo tengo fibertel y pasa eso. La solucion, si tu router te lo permite, y calculo que si, es buscar un casillero que dice clone mac address. Esto hace que el ISP vea una sola mac conectada a la IP que te asigna. El resto de la configuracion va como te dijeron los chicos
salud.

---

### Post by mprizmic on 2008-01-07
Gracias a todos. Finalmente lo pude resolver y lo que terminé haciendo lo pueden ver en [aquí]("http://prizmic.blogspot.com/2008/01/configuracin-wifi-en-ubuntu-710.html").

---

