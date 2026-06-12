---
title: "[SOLVED] Con windows navego, con ubuntu no"
date: 2008-04-16
forum: Argentina Team
---

### Post by margori on 2008-04-16
Estimados amigos:

Tengo un problema que es una bomba. Realmente me ha desconcertado y termino por perdirles ayuda.

La cosa es que tengo instalado Ubuntu y Windows XP en dual boot. Con Windows internet anda muy bien, ningun problema. Ahora bien en Ubuntu no anda ni a palos. Lo mas bonito es que escribo en un terminal "ping www.google.com.ar", resuelve el nombre y tiene respuestas de unos 300ms. Pongo firefox, resuelve la direccion, dice conectando, pero no se conecta.

Pidgin tampoco anda, Liferea tampoco anda. Incluso se me ocurrió probar telnet con esta linea "telner bbs.rafastd.org" y nada. La prueba en Windows y anda bien.

Como es la red? Creo que es así:
- Mi computadora tiene una placa de red onboard
- Luego un switch wireless, con el que me conecto al ISP por microondas. Tiene filtrado las conexiones por nº de MAC.
- Ya del lado del servidor no se muy bien, pero creo que por lo menos hay 2 routers.
- Cablemodem a Arlink bbt. (Estoy en Mendoza)

Esto realmente me ha dejado desconcertado. Por un lado porque todo estuvo andando bien hasta hace unos dias, y otra es que se resuelven los dns pero no navega, incluso con ningún otro protocolo aparte del http. Incluso me tome la molestia de reinstalar Ubuntu a Gutsy pensando que era problemas de Hardy, y nada.

Espero alguien pueda ayudarme al menos a encontrar la punta del hilo.

Gracias.

---

### Post by beuno on 2008-04-16
Sospecho que hay un proxy en el medio, que, por alguna razon, en windows lo tenes configurado.
Fijate que no tengas nada en los settings de proxy de windows (porque DNS tenes, asi que parece ser algo que te patea en el puerto 80)

---

### Post by oktubrer on 2008-04-16
Si fuera solo el puerto 80 el telnet se conectaría igual, pero aparentemente también afecta al 23

---

### Post by MeduZa on 2008-04-17
tenes mal setiado el gatewate address o como dicen arriba es algo de puertos trabados (posible iptables? )

---

### Post by margori on 2008-04-17
Estimados Amigos:

El problema a sido resuelto. Fue debido a conflictos en la política de firewall de mi proveedor.

La razon de esta politica es un virus que se está transfiriendo desde las computadoras que tiene windows en nuestra red local wireless. Hay clientes que como tienen problema con el MSN Messenger y el firewall, desactivan el firewall, ni hablar de antivirus, y esas computadoras son un hervidero de virus.

El virus que está actualmente genera paquetes basura en toda la red local, molestando particularmente a las computadoras desprotegidas.

Conclusión, no era un problema de compatibilidad de routers, windows y linux, solo un problema de promiscuidad que windows fácilmente te permite.

Yo por suerte con Ubuntu, de no haber sido por este problema, ni me hubiera enterado. :-)

---

### Post by MeduZa on 2008-04-17
> **margori said:**
> Estimados Amigos:

El problema a sido resuelto. Fue debido a conflictos en la política de firewall de mi proveedor.

La razon de esta politica es un virus que se está transfiriendo desde las computadoras que tiene windows en nuestra red local wireless. Hay clientes que como tienen problema con el MSN Messenger y el firewall, desactivan el firewall, ni hablar de antivirus, y esas computadoras son un hervidero de virus.

El virus que está actualmente genera paquetes basura en toda la red local, molestando particularmente a las computadoras desprotegidas.

Conclusión, no era un problema de compatibilidad de routers, windows y linux, solo un problema de promiscuidad que windows fácilmente te permite.

Yo por suerte con Ubuntu, de no haber sido por este problema, ni me hubiera enterado. :-)

windows CON VIRUS? no te lo puedo creer!! estas seguro? :lolflag::lolflag::lolflag::lolflag:

te puedo preguntar como hiciste para darte cuenta?

---

### Post by margori on 2008-04-17
> **MeduZa said:**
> te puedo preguntar como hiciste para darte cuenta?

Soy amigo del administrador de la red local. El me dijo que supone que es un virus, ya que tiene un montón de trafico en la red de paquetes "fantasmas". El llamo "flood".

La solución que el probo es restringir los puertos de las computadoras de donde salen esos paquetes, aunque le sugerí que no era la mejor solución, quizás sea mas sencillo capacitar a los clientes con windows promiscuos y sin protección o que les sugiriera instalar Ubuntu. La segunda opción le gusto mas, aunque debemos reconocer que si un usuario windows no le da bola al firewall poca esperanza queda para una migración a Linux. :(

---

