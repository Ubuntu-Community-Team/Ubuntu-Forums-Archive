---
title: "Red casera"
date: 2007-08-02
forum: Argentina Team
---

### Post by Apipote on 2007-08-02
La cosa es asi, para no pelear mas con mis hijos, decidi comprar otra pc.
En la mia tengo xubuntu ( que amo ) y en la de ellos xp ( para sus juegos y demas ), y una impresora. Solo eso.
Que router barato me recomiendan ? ( he visto un noga de 80 mangos ).
He visto samba instalado en xubuntu, y en win el asistente de redes, todo listo para usarse.
Como hago?
Gracias por adelantado.

---

### Post by aceki on 2007-08-02
Mira de router te recomiendo low-prifile los encore o tp-link (ambos superiores en precio y en prestaciones que el noganet) traen firewall, NAT, son muy buenos. 

Ahora no se bien el tema de samba, nunca lo use, tengo que poner a verlo yu que en redes siempre estube con win

---

### Post by faktorqm on 2007-08-02
Hola, antes que nada, que tipo de conexion a internet tenes? (te pregunto por que no se si sabes de redes o no, y si tenes adsl no necesitas router, necesitas switch, en cambio, si tenes cablemodem, necesitas router)
El que no se si es barato, es el D-LINK DI-604. Es un super caño, trae funciones bastante avanzadas y lo normal,  NAT, firewall, dhcp, etcetc. y clonador de MAC, que no se si todos los router lo traen (en caso de tener fibertel, lo vas a necesitar).
Si queres routear asi sin mas, comprate el mas barato que encuentres, asegurandote que tenga NAT y firewall y listo el pollo.
Te recomiendo que te fijes que onda, por que por ejemplo, yo tengo Speedy, y el modem adsl que me dieron es un Zyxel 630, que calienta y se resetea solo. Ahora no por que tamos en invierno, pero en verano, se cuelga cada 2x3. Perdona el post largo. salu2!

---

### Post by Apipote on 2007-08-03
D-LINK DI-604 sale 40 mangos mas, si vale la pena compro ese.
Y tengo una conexion wireless ( es una antena y una caja en el techo que es un router que actua como cliente, de un nodo a 1km de mi casa ), que baja a mi placa de red y se conecta como pppoe

---

### Post by faktorqm on 2007-08-03
Hola, no entendi. Si te conectas como pppoe (Point to Point Over Ethernet) entonces lo que tenes es adsl.
Segun lo que  me decis deduzco que tendras:

linea de telefono -> modem adsl -> emisor de antena -> aire -> receptor de antena -> placa de red de tu pc.

Ahora bien, si tenes esta configuracion propuesta por mi lo que te recomendaria es lo siguiente, en el modem de adsl te convendria configurarlo en modo router, (esto es, el tipo marca solo y te olvidas de cualquier marcador en tu pc) y en la bajada de la antena que tenes en tu placa de red, pones un switch.

Si estamos todos de acuerdo en que tenes adsl para mi NO necesitas router, por que el modem de asdl ya trae uno. (en realidad es modem y router todo en uno) Lo que necesitas es un switch, y setear modo router en lugar de puente.
Si no sabes como se hace, pone el modelo y la marca del modem adsl, y la empresa que usas y lo vemos. Cualquier duda no dudes en postear. Salu2!!

---

### Post by Apipote on 2007-08-03
En la casa de un amigo hay un nodo ( isp) con una antena que manda señal a mi antena en el techo de casa.
Mi antena tiene una caja, y ahi hay un router wireless configurado como receptor, de ahi sale un cable de red que se enchufa a mi placa de red en la pc.
Es un sistema de ****** pero no queda otra en la zona que vivo.
Que me sugeris entonces?

---

### Post by faktorqm on 2007-08-04
ammm ok, y vos podes entrar al router wireless? si podes, entonces me tendrias que decir marca y modelo asi me fijo si se puede configurar como router/marcador. (lo mas probable es que si se puede, pero viste como son estas cosas, nunca se sabe.)
Si se puede, lo unico que tendrias que hacer es poner el cable que va a tu pc al uplink del switch, y del switch un cable derecho a tu pc, otro a la otra pc. Entonces el router haria el trabajo del pppoe y no tendrias que usar ningun marcador. Entonces te independizas de ese tema, y cuando prendes la compu, ya estas conectado. Cualquier compu, sin necesidad de que una este prendida ni cosas raras. Salu2!!

---

### Post by Apipote on 2007-08-04
Si puedo, tengo la ip y cuando entro veo la web para setearlo.
Es un acces point edimax ew-7209apg pero esta en el techo de mi alta casa de 2 pisos.
Tengo que subir ahi???
:(

---

### Post by faktorqm on 2007-08-06
Hola, te salvaste (creo). Si tu "coso" es identico al que aparece aca y aca: 

[http://www.edimax.com.tw/html/english/products/EW-7209APg.htm](http://www.edimax.com.tw/html/english/products/EW-7209APg.htm)
[http://www.dooyoo.es/equipos-de-red/edimax-ew-7209apg/details/](http://www.dooyoo.es/equipos-de-red/edimax-ew-7209apg/details/)

NO TENES QUE COMPRAR NADA. lo unico que tenes que hacer, es subirte y enchufar un cable igual al que llega a tu pc a otra boca. calculo que debe ser un cable derecho. Y con el tema del pppoe dejame investigarlo un toke. Perdona el cuelgue, pero el finde sali vier y sab y futbol a la tarde y .... todos sabemos. Salu2!!

Che, me baje el manual de tu coso, es una masa, pero ......... sigo sin entender como lo tenes puesto. Fisicamente ya entendi, el tema es logicamente. HAce una cosa, decime, el ip del router, la mascara, el ip de tu pc, la mascara, el gateway, y los dns. 
Sino sabes como entrar a tu router, user: admin,  password: 1234, ip por defecto 192.168.2.1 (lo saque del manual xD)
Que empresa de internet tenes? si usas pppoe tengo que creer que usas adsl, estoy en lo cierto? Por favor, responde una a una todas mis preguntas por que hasta que no te ande todo no voy a dormir en paz XD salu2!

Tercera edicion :S En el manual al menos no aparece nada, revisa adentro del router si en alguna parte te aparece una opcion de poner usuario y contraseña, vpi/vci, tipo de encapsulacion, o algo asi. otra pregunta, del otro lado de la antena, que hay? o sea, a vos te llega una señal y tu router la capta, esa señal, de donde viene? 
Salu2!!

---

### Post by Apipote on 2007-08-06
Uy para que me mareaste. No tengo tus conocimientos, soy ginecologo che !!!!  :)
A ver, sin duda es ese que mencionas.
Hay una antena receptora, de ahi sale un cable que entra a una caja de plastico y se conecta al AP, y del AP sale un cable de red que baja a mi pc.
Y si, entro a la web que lo controla por la ip.
Me conecto a la casa de un amigo porque se su mac adress.
El isp ni idea, a el le llega internet y reparte desde su nodo y nos cobra a todos un abono.
O sea que no compro un ****** ? y hago lo que me decis? Tiene este AP otra boca para conectar otra pc?

Esto es lo que lei entrando al router:

Attain IP Protocol  	 Fixed IP
IP Address 	192.168.1.87
Subnet Mask 	255.255.255.0
Default Gateway 	192.168.1.87

Mi placa de red, esta en "auto"

---

### Post by Hei Ku on 2007-08-06
cual es la direccion de tu placa de red?

podes averiguarla poniendo ifconfig en la consola.

Tambien serviria saber como dice el networkmanager que tenes configurada la placa, si manual, DHCP, o de otra manera.

---

### Post by Apipote on 2007-08-06
Mi placa DHCP

Y el ipconfig tira esto:

eth0      Link encap:Ethernet  HWaddr 00:17:31:96:58:12  
          inet addr:192.168.1.24  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:31ff:fe96:5812/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:35730 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30462 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16289262 (15.5 MiB)  TX bytes:4658293 (4.4 MiB)
          Interrupt:22 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1424 (1.3 KiB)  TX bytes:1424 (1.3 KiB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:172.16.16.5  P-t-P:172.16.16.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1488  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:54 (54.0 b)  TX bytes:329 (329.0 b)

ppp1      Link encap:Point-to-Point Protocol  
          inet addr:172.16.16.5  P-t-P:172.16.16.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1488  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:122 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:54 (54.0 b)  TX bytes:8713 (8.5 KiB)

ppp2      Link encap:Point-to-Point Protocol  
          inet addr:172.16.16.5  P-t-P:172.16.16.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1488  Metric:1
          RX packets:128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:179 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:9186 (8.9 KiB)  TX bytes:13227 (12.9 KiB)

javier@Sexta:~$

---

### Post by Hei Ku on 2007-08-06
ok, por lo que entiendo, el AP te da una direccion a traves de DHCP, y despues usas el pppoe para conectarte a lo de tu vecino. Si es asi, no deberias tener problema en poner un router al medio, para poder conectar mas computadoras.

---

### Post by faktorqm on 2007-08-07
si, entonces va router definitivo. ahora, lo ultimo antes de comprarlo, como vas a compartir internet entre las maquinas? sino preguntale a tu vecino si tenes que hacer lo del pppoe en las dos pc. 

ALTO FURSIO: escribiste "I[SIZE="3"]P[/SIZE]CONFIG" JAJAJAJAJAJAJAJAJ salu2!!

---

### Post by Apipote on 2007-08-07
Gracias chicos

---

### Post by faktorqm on 2007-08-08
de nada! salu2!!

---

### Post by Apipote on 2008-03-01
Estimados a mi red casera, le agregué otro edimax 7209 ponteciado. Me gustaria meterle mano, pero no puedo entrar a la pagina de configuración siguiendo el manual, sin ningun error.
Alguna sugerencia??
Gracias.

---

### Post by faktorqm on 2008-03-03
explayate mas capo! a donde no podes entrar? a la pagina de configuracion? no tenes la contraseña? si le haces ping te responde? si por defecto el "coso" (no pusiste que es :P) esta en la red 10.0.0.X asegurate de estar en la misma red. Salu2!

---

### Post by Apipote on 2008-03-03
Descubri lo que pasó. El edimax 7249 (pro) esta potenciado  con un firmware que lo lleva a 400. Una masa, lo que es este acces point.
Pero ese firmware le cambia la ip por default a 192.168.1.1. El manual esta escrito para la versión standard.
Gracias.
Slds

---

