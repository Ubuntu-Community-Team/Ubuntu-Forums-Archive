---
title: "Linux Router Double WAN [OT]"
date: 2008-04-16
forum: Argentina Team
---

### Post by jclevien on 2008-04-16
Hola que tal,

Estoy buscando algún programita para usar una computadora como router, con 2 proveedores ISP para una red local LAN.

Por ejemplo: tengo a Fibertel y a Arnet. Los dos proveen cablemodems conectados a una computadora con este "Linux" raro, y de ese router se conecta una tercera placa con un switch para compartir las conexiones de Internet en la LAN. Simple.

Por supuesto, la gracia es que pueda hacer load balancing, failover, y demás temas importantes (si una red tiene bajo rendimiento, balancear el tráfico a la otra, si se cae una, la otra inmediatamente entra a operar, etc), así como una buena consola de administración, estilo Coyote Linux.

Yo pregunto: habrá algún paquete en Ubuntu para realizar este trab ajo?

Estuve averiguando precios, y un router LinkSys Double WAN, que sería algo equivalente a esto, estaría en el orden de los 1200 pesos. Quizás sería interesante ofrecer un servicio similar con Ubuntu, si es que existe la alternativa libre, claro.

Y si no, tendría que trabajar para hacer algo similar...


Saludos.


Juan

---

### Post by faktorqm on 2008-04-16
Se esta usando mucho eso ultimamente, y creo que hay una especie de "vacio" de software al respecto, no de hardware como vos nombrabas. Lo primero que se me viene a la mente, es usar algo de tipo squid. Lo que pasa es que moris en un proxy si o si, y eso no es bueno administrativamente hablando. Mas alla de que el programa ande mal, y que eso sea de publico conocimiento.
Estaría bueno que haya un programa que haga esto, y la verdad ahora no tengo mucho tiempo para investigar, pero si no existe estaria bueno programarlo... aunque creo que que darle a tan bajo nivel nos va a llevar mucho tiempo. Salu2!

---

### Post by Hei Ku on 2008-04-16
Podes probar por el lado de las distribuciones que se usan para los Linksys, OpenRouter, o algo asi.
En cuanto al squid, segun tengo entendido la performance es excelente, asi que tampoco es mala opcion, pero eso te cubre solo proxy. La parte grossa es en la gestion de routing, que no se cual puede ser bueno.

---

### Post by euzkoarima on 2008-04-17
Nosotros en la oficina cambiamos el linksys que teníamos por el [pfsense]("http://www.pfsense.com/") que es una distribución especializada en hacer de router basada en FreeBSD.
Durante un tiempo tuvimos dos proveedores, mucho no pudimos probar porque uno era ertach y andaba MUY mal, tanto que hubo que darlo de baja. Pero hasta donde pudimos ver funciona.

---

### Post by clasificado on 2008-04-17
podés pobar con el endian firewall

[http://www.endian.it/en/community/](http://www.endian.it/en/community/)

---

### Post by ariel on 2008-04-18
Cualquier distro linux ya trae todo lo que hace falta para hacer que la pc haga de router. 

Es mas, depende de lo que quieras hacer, es posible que ni siquiera tengas que instalar ningun package.

En lo mas basico, hay que activar IP forwarding in el kernel, 

echo "   Enabling forwarding.."
echo "1" > /proc/sys/net/ipv4/ip_forward
y despues configurar las IP routes etc.

Hay mil how-tos de como hacer esto con ubuntu.

Por ejemplo, este es uno:

[http://ubuntuforums.org/showthread.php?t=111972](http://ubuntuforums.org/showthread.php?t=111972)

---

