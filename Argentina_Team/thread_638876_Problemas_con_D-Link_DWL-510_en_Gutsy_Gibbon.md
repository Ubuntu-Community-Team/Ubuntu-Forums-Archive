---
title: "Problemas con D-Link DWL-510 en Gutsy Gibbon"
date: 2007-12-12
forum: Argentina Team
---

### Post by Marcos on 2007-12-12
Hola a todos.
Utilizo Ubuntu desde la salida de Warty Warthog. Desde aquellos tiempos que tengo una tarjeta PCI Wireless D-Link DWL-510, la cual en su momento no era detectada, por lo cual había que utilizar *ndiswrapper* junto con los drivers de Windows, cosa que nunca fue de mi total agrado. Por ello desistí de usarla.
Hoy (siendo usuario de Gutsy Gibbon) me picó el bicho de la curiosidad y decidí conectar dicha tarjeta nuevamente. Para mi sorpresa, "creo" que Gutsy la detectó, pues al hacer clic en el ícono de *networkmanager* vi una serie de redes inalámbricas listadas.

El problema, es que al seleccionar una red protegida (de la cual conozco su contraseña) e ingresar, al momento de intentar establecer la conexión mi Ubuntu se congeló (puntero del mouse e ícono animado de networkmanager congelado, y luces de las teclas Bloq Mayús y Despl parpadeando). Tras reiniciar, lo intenté una segunda vez con un poco más de paciencia, esperando a que se descongelara, pero no ocurrió.

Abrí mi terminal y empecé a recolectar información:
> $ lspci |grep Wireless
00:09.0 Ethernet controller: D-Link System Inc DWL-510 2.4GHz Wireless PCI Adapter (rev 20)


> $ iwconfig
wlan0     802.11b  Mode:Managed  Frequency:2.467 GHz  
          Access Point: Not-Associated   Bit Rate:11 Mb/s   Sensitivity=80/85  
          Retry:on   Fragment thr:off
          Power Management:off
          Link Quality=1/100  Signal level=-81 dBm  Noise level=-157 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Quisiera saber si existe alguna solución para este problema (sin pasar por utilizar *ndiswrapper*) o si nuevamente deberé exiliar la DWL-510 al rincón de la pieza.

---

### Post by melvinlopez06 on 2007-12-17
pues mira marcos que raro lo que te pasa, porque generalmente cuando se apagan y encienden las lucecitas del teclado solo significa una cosa, kernel panic (hasta donde yo se).

Yo tengo una D-Link DWL-G520 y todo anda de maravilla aunque no he probado con redes protegidas, no creo que deba existir problema alguno, pero deberias mirar los syslog (/var/run/syslog) a ver si encontras algo.

Tambien averigua si tu tarjeta acepta los standares 802.11b y g, y tambien la encriptacion en que debes de meter la Wep.

---

### Post by tech9 on 2007-12-17
> **melvinlopez06 said:**
> pues mira marcos que raro lo que te pasa, porque generalmente cuando se apagan y encienden las lucecitas del teclado solo significa una cosa, kernel panic (hasta donde yo se).

Yo tengo una D-Link DWL-G520 y todo anda de maravilla aunque no he probado con redes protegidas, no creo que deba existir problema alguno, pero deberias mirar los syslog (/var/run/syslog) a ver si encontras algo.

Tambien averigua si tu tarjeta acepta los standares 802.11b y g, y tambien la encriptacion en que debes de meter la Wep.

Concuerdo, la prueba que mira los troncos de sistema.

---

### Post by Marcos on 2007-12-18
Puede que sea kernel panic, realmente lo desconozco pues es la primera vez que me ocurre.
La red está encriptada en WEP hexadecimal de 128 bit. La tarjeta soporta 802.11b, pero no sé si soporta 802.11g.
Ahora no sé si el router tenga que tener alguna especificación (es un DI-714P+).

Sobre los syslog, no los encontré, al parecer no tengo.

---

### Post by melvinlopez06 on 2007-12-18
pos mira, deberias de meterte en las paginas de los fabricantes de las 2 cosas para ver y tener una idea de que te puede dar problema.

A mi me pasa que conozco la contraseña wifi de mi red de casa y usando una tarjeta de red usb SMC con ndiswrapper no me conecta y no se porque, quiza sera otra especificacion de encriptacion, o la tarjeta no la soporta !!

Puede que te pase algo asi a vos !!
Lo mejor es que busques las especificaciones del router y la wifi en los sites de los fabricantes.

---

### Post by jpmorelli on 2007-12-18
Marcos, acabo de comprar una D-Link 510 con chipset Ralink y la instalé en mi Kubuntu Gutsy 7.10 y está andando perfecta !!! No tuve que cargar nada, todo fué reconocido automáticamente y para empezar con la configuración desde 0 nuevamente y sin problemas lo único que hice fué renombrar ( por si acaso ) el archivo /etc/network/interfaces y reiniciar. A partir de ahí knetworkmanager me mostró mi SSID ( en mi caso uso WEP hexadecimal 64 bits con un router linksys ) y todo perfecto !!!

Asi que a vos te debería funcionar tambien, sino avisame con lo que te pueda ayudar.
Suerte !

---

### Post by cirorodrigues on 2008-03-22
Hola Marcos,
yo utiliso una DWL-G510 pero ella trabaja con ndiswrapper. En su "identification nativa" por Gutsy yo no podia acesar una rede wpa.  Pero esto se pasa bien con ndiswrapper.
Saludos.

---

### Post by mrierab on 2008-04-05
Hola,

He encontrado este mensaje buscando exactamente el mismo problema al instalar Linux-Mint (basado en Ubuntu 7.10).

Tengo la misma tarjeta Wifi D-Link 7.10, el archivo interfaces lo tengo solo con el looppback i exactemente igual al meter la clave al cabo de unos segundos se congela el sistema y parpadean las luces de Scroll y Pausa.

Que solucion aplicaste?.

Gracias

---

### Post by ariel on 2008-04-09
Yo use wireless cards D-Link PCI y me experiencia fue mailisima, andaba remal incluso en windows con los drivers del fabricante (esto fue hace muchos anios, cuando todavia tenia dual boot). 

La termine cambiando por una linksys basada en ralink, hace unos 2 anios, el driver nativo de linux de ralink era bastante malo, se colgaba de las maneras mas extranias, y ndiswrapper tambien.

La solucion a los problemas de wireless para mi fue una Netgear WG311T que compre usada. El chipset atheros tiene un grupo de soporte espectacular en linux, los pibes de madwifi. Hace dos anios que no veo una colgada o un corte de conexion.

---

