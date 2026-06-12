---
title: "adsl + wifi con funcionamiento extraño"
date: 2007-06-19
forum: Argentina Team
---

### Post by jajajavi on 2007-06-19
Como comentaba anteriormente tengo mi pc conectada por cable al router wifi que a su vez está conectado al modem adsl. El problema es que eventualmente se cae la conexión y no encuentro forma de reestablecerla, en algún momento reseteaba modem y router y todo volvía a la normalidad. Otro método que me funcionó últimamente (no sé por qué) consiste en volver a conectar el modem a la pc (sin el router wifi) y conectar desde windowz ya que en éste conservo la configuración que usaba antes para conectarme. Otra cosa extraña es que actualmente los únicos sitios que cargan son google y los que tengo en live bookmarks, de modo que puedo postear en este foro pero no puedo ver ningún otro sitio. No puedo usar el gaim para que algún amigo nerd que me ayude, tampoco puedo usar el thunderbird para enviar. Tocando de oido hago un ping que me da lo siguiente:
```

~$ ping ubuntuforums.org
PING ubuntuforums.org (82.211.81.186) 56(84) bytes of data.
64 bytes from 82.211.81.186: icmp_seq=1 ttl=50 time=255 ms
64 bytes from 82.211.81.186: icmp_seq=2 ttl=50 time=263 ms
64 bytes from 82.211.81.186: icmp_seq=3 ttl=50 time=267 ms
64 bytes from 82.211.81.186: icmp_seq=4 ttl=50 time=251 ms
...
...
64 bytes from 82.211.81.186: icmp_seq=75 ttl=50 time=265 ms
64 bytes from 82.211.81.186: icmp_seq=76 ttl=50 time=266 ms
64 bytes from 82.211.81.186: icmp_seq=77 ttl=50 time=265 ms

--- ubuntuforums.org ping statistics ---
77 packets transmitted, 77 received, 0% packet loss, time 400557ms
rtt min/avg/max/mdev = 251.957/263.752/305.576/6.142 ms
```

¿Alguien sabe qué ca**jo pude estar pasando? Desde ya muchas gracias...

---

### Post by jajajavi on 2007-06-19
Ahora estoy en la laptop conectado mediante wifi en la que tenía una actualización descargando que no pudo continuar porque (aparentemente) no tengo conexión y el resto de las páginas me dan "Servidor no encontrado", aunque ubuntuforums.org funciona perfectamente...

---

### Post by jajajavi on 2007-06-19
En este momento estoy conectado desde winxp sin el router wireless, con la pc enchufada directamente al modem, tal como lo explicaba anteriormente. Ahora reinicio, lo vuelvo a conectar y probablemente tenga la red inalámbrica funcionando desde Ubuntu...

[editado] Efectivamente, estoy conectado y tengo wifi. Si alguien sabe qué puede estar pasando le agradezco me lo informe.

[editado] Ahora volvió a dejar de andar "Servidor no encontrado" en todos los sitios (excepto los mencionados), aunque el Informe meteorológico y el Checkgmail del panel se actualizan sin problemas.

---

### Post by Al_maverick on 2007-06-19
Podria ser un problema de DNS? Fijate que sucede si corres el nslookup desde la consola (si estas familiarizado con este comando)
Si no, fijate que la configuracion de Windows y Ubuntu sea la misma para los servidores DNS. No es seguro que sea asi, pero tuve un problema similar hace unos dias, y era un problema en los DNS del ISP.

---

### Post by jajajavi on 2007-06-20
> **Al_maverick said:**
> Podria ser un problema de DNS? 
No sé qué tipo de problema es, pero fui a la solapa DNS en Configuración de Red y decía 192.168.1.1, entonces se me ocurrió entrar a http:// 192.168.1.1 / donde hice la configuración inicial, ponerle ok a todo (no hice ningún cambio) y al menos por ahora funciona...

[editado] Funciona pero cada tanto se vuelve a caer, pero ahora en lugar de reiniciar y cambiar cables de lugar reseteo desde firefox en 192.168.1.1... es un avance (?)

---

### Post by Al_maverick on 2007-06-20
me parece que el problema esta en que tenes como servidor DNS el router o lo que sea que tengas en 192.168.1.1, que es raro, salvo que tengas algo mas armado. Te fijaste en windows que es lo que tenes? Seguramente toma todos los datos desde el DHCP, y eso es lo que deberias tener.

---

### Post by ariel on 2007-06-20
hacer andar bien wifi en linux es todavia una cuestion de arte y suerte.

Hay chipsets malditos como el ralink2500 que tienen un driver linux nativo muy berreta (ejemplo: placa linksys wmp54g, mismos problemas que tenes vos), usando los drivers de windows con ndiswrapper mejora la estabilidad, pero trae otros problemas.

Hay chipsets benditos como los de intel (ipw3945) que tienen un driver linux nativo buenisimo y andan 'out of the box'. 

Bienvenido al fantastico mundo de wifi en linux. Y nisiquiera te pregunte si intentaste activar encripcion con WPA2...

Para placas wifi PCI, Netgear WG311T  tiene uno de los chipsets benditos (doy fe).



> **jajajavi said:**
> No sé qué tipo de problema es, pero fui a la solapa DNS en Configuración de Red y decía 192.168.1.1, entonces se me ocurrió entrar a http:// 192.168.1.1 / donde hice la configuración inicial, ponerle ok a todo (no hice ningún cambio) y al menos por ahora funciona...

[editado] Funciona pero cada tanto se vuelve a caer, pero ahora en lugar de reiniciar y cambiar cables de lugar reseteo desde firefox en 192.168.1.1... es un avance (?)

---

### Post by jpmorelli on 2007-06-23
Es un problema de DNS seguro, los DNS son los encargados de resolver los nombres de internet o sea: cuando yo pongo [www.google.com](www.google.com) el servidor de nombres (DNS) me resuelve a que dirección tiene que ir a buscarlos. Hasta acá bien ? ok... no podés tener como DNS el router local, esta mal, en tu PC tenes que tener "fowardeados" digamos, los DNS que el router resolvió para tu conexión. A veces los proveedores te los dan fijos, otras veces te los resuelve el propio router al conectar via DHCP ( asignación de IP dinámica a tu conexión de internet ) , pero te los tiene que enviar a tu compu, que también se las arregla solo.
Conclusión: chequeá porque tu PC no está recibiendo los DNS correctamente, tanto desde los seteos de tu PC como desde tu router, intentá que todo lo resuelva automaticamente siempre que la conexión a tu proveedor pueda funcionar de ese modo.
Una manera de chequearlo facil es poniendo en Ubuntu los DNS de tu proveedor a mano y sacar el 192.168.1.1, vas a ver como ahí anda todo.
Suerte !

---

### Post by jajajavi on 2007-06-29
Bueno, hacía un tiempo que no fallaba pero en estos días volvió a caerse la red, cosa que resuelvo reseteando el setup desde 192.168.1.1. Como decía jmorelli mi pc no está recibiendo los DNS correctamente, aunque en este momento estoy conectado normalmente. Lo que no entiendo es lo siguiente, si es el router es el que hace que el modem marque para conectarse y dar internet a la pc vía cable y a la laptop por aire... mmm... no sé cómo explicarlo, pero bueno, supongo que tendré que poner los DNS de ciudad internet en Configuración de Red y alguna cosa más que mi condición de neófito desconoce. Disculpen la ignorancia, pero en cualquier momento me vuelvo a quedar sin red. Gracias a todxs!

---

### Post by Al_maverick on 2007-06-29
> **jajajavi said:**
> Bueno, hacía un tiempo que no fallaba pero en estos días volvió a caerse la red, cosa que resuelvo reseteando el setup desde 192.168.1.1. Como decía jmorelli mi pc no está recibiendo los DNS correctamente, aunque en este momento estoy conectado normalmente. Lo que no entiendo es lo siguiente, si es el router es el que hace que el modem marque para conectarse y dar internet a la pc vía cable y a la laptop por aire... mmm... no sé cómo explicarlo, pero bueno, supongo que tendré que poner los DNS de ciudad internet en Configuración de Red y alguna cosa más que mi condición de neófito desconoce. Disculpen la ignorancia, pero en cualquier momento me vuelvo a quedar sin red. Gracias a todxs!

Basicamente, la cosa es asi:
el modem y el router son el gateway, lo que te permite conectarte a internet a traves de direcciones IP. Pero ninguno guarda los nombres comunes que uno utiliza para conectarse. Esos los guardan los servidores DNS. Asi que al configurar tu red, tu gateway es el router y los servidores DNS tenes que poner los del ISP que corresponda. Los de ciudad en este caso.

---

### Post by jajajavi on 2007-06-30
Ok, algo voy entendiendo, en este momento hay dos laptops accediendo a internet por aire, pero la PC que se conecta al router por cable no puede acceder. Pregunta: **¿a los DNS los tengo que cambiar en Configuración de Red y/o en algún otro lado?** Gracias nuevamente.

---

### Post by Al_maverick on 2007-07-02
en la configuracion de red deberian estar los servidores de dns.

otra cosa, el router deberia tener dhcp, deberias probar si lo configuras ahi, y despues desde las pcs simplemente te conectas con dhcp y ya esta.
que router tenes? yo tengo una configuracion similar con un linksys y anda barbaro. tambien tengo ciudad, que no es ninguna maravilla, pero es la ****** que tengo paga por el edificio.

---

### Post by jajajavi on 2007-07-02
El router es un Asus 240 MIMO wl-566gm, el modem un Cisco 677 y ciudad flash es una p*a. En Configuración de la red actualmente tengo el DNS 192.168.1.1 que es el router, por lo que entiendo tengo que poner los DHCP y los DNS del proveedor en el setup del router, o no?

Por ahora funciona... gracias por la paciencia!

---

### Post by Al_maverick on 2007-07-03
los dns siempre tienen que ser los del proveedor, salvo que configures especialmente un servidor dns dentro de tu red, pero con una red chica no tiene sentido.

---

