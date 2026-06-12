---
title: "Problemas con un router Ethernet"
date: 2007-07-27
forum: Argentina Team
---

### Post by Aswang on 2007-07-27
Buenas, miren yo tengo un problema con un Router Ethernet con el tema de "Cortafuegos" (yo ando buscando algo para sacarlo o desactivarlo porque es medio molesto). Digamos que no puedo usar el aMule o otros programas de descargas.
Yo tengo un amigo que usa un router usb y no tiene drama y yo que tengo uno de LAN tengo problemas :mad:.
Alguno me prodria informar algo o ayudarme? :d


Gracias :d

Atentamente yo xD

Pd: Yo puse el firestarter y me caco la configuracion (digamos que no me sirvio de mucho xD), tambien no puedo hostear en games o recivir archivos por gaim por el tema este. (HUAWEI SmartAX MT882)

---

### Post by Hei Ku on 2007-07-27
fijate si el router tiene la opcion de hacer port forwarding, que es lo que te va a permitir usar el emule y otras cosas.

---

### Post by valucha on 2007-07-27
> **Aswang said:**
> Buenas, miren yo tengo un problema con un Router Ethernet con el tema de "Cortafuegos" (yo ando buscando algo para sacarlo o desactivarlo porque es medio molesto). Digamos que no puedo usar el aMule o otros programas de descargas.
Yo tengo un amigo que usa un router usb y no tiene drama y yo que tengo uno de LAN tengo problemas :mad:.
Alguno me prodria informar algo o ayudarme? :d


Gracias :d

Atentamente yo xD

Pd: Yo puse el firestarter y me caco la configuracion (digamos que no me sirvio de mucho xD), tambien no puedo hostear en games o recivir archivos por gaim por el tema este. (HUAWEI SmartAX MT882)

[COLOR="DarkOrchid"]
Mira, hoy instale Ubuntu en una compu con un modem Huawei SmartAX MT881,  no creo que haya mucha diferencia :P. El modem se conectaba a la pc mediante ethernet.
Lo que hice fue correr en la consola **sudo pppoeconfig** . Y seguí todos los pasos, después de eso el Amule funcionaba perfectamente, bajaba rapidísimo y no aparecia nada de Firewalled ni nada de eso. Probá, capas te sirve.[/COLOR]

---

### Post by Hei Ku on 2007-07-28
El tema es que el cortafuegos esta en el router, correcto?

Proba de conectarte con el firefox a la direccion del router. En algunos casos, con eso podes acceder a la configuracion, y con suerte, desactivarle el firewall. En general, la clave por defecto es admin/admin

---

### Post by marianom on 2007-07-28
O admin/password

---

### Post by faktorqm on 2007-07-28
En esta pagina te dice todo. 

[http://www.adslzone.net/tutorial-46.2.html](http://www.adslzone.net/tutorial-46.2.html)

Consejo 1: el firewall NUNCA lo desactives, por si no sabias existen 65535 puertos tcp y otro tanto udp. por lo tanto tu pc es una coladera si no tenes ningun firewall.
Consejo 2: cuando abras los puertos, no abras los del emule por defecto, inventate uno vos. (por ejemplo, yo tengo, el 7000 tcp, 7003 tcp, y 7010 udp) Para que ande super el emule, tenes que abrir siempre un puerto adicional, que es el que eligiste tcp mas 3. Salu2!

---

### Post by guillermolisi on 2007-07-28
Faktorqm

Cuales serian las ventajas de habilitar otros puertos para el eMule que no sean los que se sugieren por defecto, considerando que hay un firewall activo en la PC ?

---

### Post by Hei Ku on 2007-07-28
que al menos te libras de los ataques mas ligeros, sobre puertos conocidos. Obviamente, siempre te pueden entrar con un escaneo de puertos al azar, pero es solo cuestion de complicarla un poco. Como usar ssh por un puerto que no sea el 22, no te libra de todo, pero es una medida mas de proteccion.

---

### Post by faktorqm on 2007-07-29
> **guillermolisi said:**
> Faktorqm

Cuales serian las ventajas de habilitar otros puertos para el eMule que no sean los que se sugieren por defecto, considerando que hay un firewall activo en la PC ?

Hola. No entiendo tu pregunta. El firewall va a estar uses el puerto por defecto, o uno "tuyo".
La idea de no usar los puertos por defecto que trae el emule, es la siguiente: El tipo que programo emule, para que funcione de primera, tenia que establecer puertos por defecto. Todos los panchos instalan, y no entienden nada, y ni se fijan ni les importa los puertos, lo primero que hacen es empezar a bajar como locos. Lo cual no esta tan mal, pero que pasa, a nuestras queridisimas empresas de telecomunicaciones (telecom, telefonica, telmex, iplan, redes del sur, y etcetc) no les conviene que miles de usuarios lo hagan todos al mismo tiempo. Entonces como no te lo pueden "cortar" de una, empiezan a poner filtros de balance de carga por todos lados, para puertos en particular. Si, adivinaste, los que trae por defecto el emule son los primeros de la lista. Entonces? baja lento cuando bajan todos! o sea, siempre.
Como se soluciona esto? y bueno, lamentablemente creo que no se puede, ¿como le explicas a doña rosa que se compro su dell con ubuntu que tiene que cambiar los puertos por defecto del amule para que le funcione mas rapido? no tiene la menor idea de que es un puerto seguro.... con suerte de que es ubuntu.... xD

La unica solucion para "los que sabemos" es cambiar los puertos por defecto, y la diferencia se nota y mucho.
Si te fijas en la lista de servidores del emule (server.met creo ke era) los servidores no tienen el mismo puerto. Tienen todos distintos. El firewall de ubuntu por defecto, creo que trae todo abierto. (digo creo por que no se, no lo toque nunca por que tengo un router con firewall y los puertos los administro yo, asi que esta todo cerrado menos 80, 20, 21, 25, 110, 7000, 7003, y 7010. listo, ya me pueden hackear. jajajajaj)

Si te llama la atencion del puerto tcp mas 3, eso lo saque de los foros del emule, desgraciadamente no tengo el link, y mucho menos las ganas de buscarlo, pero si lo encontras vas a ver una movida que emule usa un "puerto escondido" que es el tcp mas 3 para no se que bola, y que si lo abris, anda mas rapido. Capaz es leyenda y soy un nabo, me tendria ke fijar con un ethereal a ver que onda.

Espero haberte contestado, si tenes dudas pregunta. salu2!

Una preg ya que estamos, alguien conoce un "ethereal" para linux? Salu2!!!

---

### Post by Hei Ku on 2007-07-29
Una sola aclaracion. En el caso de un "packet shaping" (asi se llama cuando el ISP te baja el ancho de banda para ciertos puertos) lo hacen por el encabezado del paquete, y no por el puerto del servicio, asi que en esos casos no sirve de nada. Pero por suerte, todavia nuestros ISPs en algunos casos son muy ingenuos. :D

---

### Post by Aswang on 2007-07-29
Gracias gente, Ahora me estoy fijando como puedo hacer y estoy mirando las info de ustedes.

Gracias de verdad :d

Saludos.

Atentamente yo xd.

---

### Post by faktorqm on 2007-07-29
Hei ku: muy interesante lo que contas, la pregunta que me cabe ahora es, si los tipos del servidor del emule ponen un proxy, o un dns, como hacen para filtrarlo? por que en el encabezado viaja el destino, si el destino es algo que saca ese encabezado y lo manda a otro lado es imposible detectarlo. (caso router). salu2!

---

### Post by guillermolisi on 2007-07-29
Bueno, mi pregunta iba por el lado de la seguridad. Nunca la pense por el lado del packet shaping, filtering o lo que hagan los ISP.

Tambien tenia entendido que ISPs como FIbertel, hacen un packet droping a partir de los encabezados y no de los puertos.

Muy buenas las dos aclaraciones. Gracias !

---

### Post by SLA_leandrin on 2007-07-29
> **faktorqm said:**
> En esta pagina te dice todo. 

[http://www.adslzone.net/tutorial-46.2.html](http://www.adslzone.net/tutorial-46.2.html)


En esa página te dice q la dirección IP de router por defecto es [http://192.168.1.1/](http://192.168.1.1/) pero por lo menos en el mío, que es el mismo módem, no abre ninguna página de configuración, entonces de ahí para abajo (o sea, todo) no puedo hacer nada... 
Como puedo averiguar cuál es el IP del router??

Saludos.

---

### Post by Hei Ku on 2007-07-29
> **faktorqm said:**
> Hei ku: muy interesante lo que contas, la pregunta que me cabe ahora es, si los tipos del servidor del emule ponen un proxy, o un dns, como hacen para filtrarlo? por que en el encabezado viaja el destino, si el destino es algo que saca ese encabezado y lo manda a otro lado es imposible detectarlo. (caso router). salu2!

Lo que se fija en el encabezado del paquete no es la direccion, sino de que tipo es. El encabezado tiene bastante informacion sobre el contenido real del paquete, entre otras el protocolo de aplicacion, para que la PC del otro lado sepa en que "lenguaje" esta hablando. A partir de esta información es que hacen el packet shaping.

---

### Post by faktorqm on 2007-07-30
> **SLA_leandrin said:**
> En esa página te dice q la dirección IP de router por defecto es [http://192.168.1.1/](http://192.168.1.1/) pero por lo menos en el mío, que es el mismo módem, no abre ninguna página de configuración, entonces de ahí para abajo (o sea, todo) no puedo hacer nada... 
Como puedo averiguar cuál es el IP del router??

Saludos.

T pueden pasar 2 cosas, al mismo tiempo, o por separado.

Lo primero, si no estas seguro de tu modem, pegale una reiniciada. Desenchufalo y volvelo a enchufar, si esto no funciona, busca el boton de reset. Una vez reiniciado (bien reiniciado) vas a estar seguro de que por lo menos el modem va a estar segun la guia.

Segundo, ahora bien, lo segundo que cabe destacar, es, que tu pc debe estar en la misma red que el modem reseteado. Es decir, si en la guia dice que el modem esta en 192.168.1.1, esa es la direccion ip del modem por defecto, la RED es 192.168.1.0, la mascara de subred es 255.255.255.0 (correspondiente a red clase C)
Ahora bien, en tu pc tenes que configurar tu placa de la siguiente manera:

ip: 192.168.1.X (donde x puede ser un numero de 2 a 254, por que el 1 es tu modem.)
mascara de subred: 255.255.255.0
default gateway: 192.168.1.1

Una vez seteado esto, abris un terminal y escribis:

```
ping -c 4 192.168.1.1
```

Debe mostrarte esto (o algo parecido): 

```
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=254 time=0.398 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=254 time=0.421 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=254 time=0.392 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=254 time=0.543 ms

--- 192.168.1.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3002ms
rtt min/avg/max/mdev = 0.392/0.438/0.543/0.064 ms

```

Si t muestra esto:

```
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3008ms

```

Es por que algo no anda del todo bien, revisa cable, resetea el modem, resetea tu pc y volve a probar.

Si te muestra que el ping esta ok, abri en el explorador la direccion 192.168.1.1 y listo. Y fijate que no te abra "www.192.168.1.1.com" ni cosas raras.
Si seguis con problemas, no dudes en consultar, y pone, que cable estas usando, (puede ser derecho, o cruzado, si estas usando una sola pc va cruzado), un print screen del comando "ifconfig" (sin comillas) en un terminal, y version de ubuntu. Asi t ayudamos mejor.



Hei ku: Operan sobre tramas de capa 2 los tipos?!?!?!?! leen los bits de protocolo y dropean paquetes?!?!? contra eso que se puede inventar? xD

Espero que t haya servido, sino pregunta. salu2!

---

### Post by jorgito on 2007-07-30
Hola, 

faktorqm:> El Ethereal ahora se llama WireShark y me parece haber visto el icono (que es como una pantallita de osciloscopio que muestra una aleta de tiburon) mientras usaba el "agregar quitar programas" en feisty.

Saludos!

---

### Post by faktorqm on 2007-07-30
grosso, ya lo instale. en agregar y quitar NO está, simplemente hice 

```
sudo apt-get install wireshark wireshark-common wireshark-dev
```

obviamente busque los nombres de los paquetes con 

```
aptitude search wireshark
```

Salu2 y gracias!!

---

### Post by SLA_leandrin on 2007-07-30
Ok ahí va el resultado de ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 00:0A:E6:45:F7:BB
          inet addr:10.0.0.3  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:e6ff:fe45:f7bb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:384587 errors:0 dropped:0 overruns:0 frame:0
          TX packets:384939 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:183580285 (175.0 MiB)  TX bytes:41021818 (39.1 MiB)
          Interrupt:5 Base address:0xc400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:13179 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13179 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:490481 (478.9 KiB)  TX bytes:490481 (478.9 KiB)

```

---

### Post by Hei Ku on 2007-07-30
ok, proba entonces poner la direccion 10.0.0.1 en el browser. Esa debe ser la direccion del router. Si no, fijate en el Network Manager cual es la direccion del gateway y pone esa.
Por alguna razon, tu router esta configurado para entregar direcciones de la red 10.0.0.x, que no es común para redes caseras.

---

### Post by SLA_leandrin on 2007-07-30
Bien, entonces es como yo me imaginaba.
Seguramente los de Arnet le han modificado el soft del módem, porque no se parece en nada a los menúes q salen en la guía, miren el screen:

[IMG]http://img211.imageshack.us/img211/6803/putamadre1lc3.th.png[/IMG]

Por otro lado, correr "pppoeconf" no me resulta, ya que me da el siguiente error:

```

                               &#9474;                                                          &#9474;
                               &#9474; Lo siento, se consultaron 1 interface, pero no           &#9474;
                               &#9474; respondió el concentrador de acceso de su proveedor.     &#9474;
                               &#9474; Por favor, verifique sus cables de red y del módem.      &#9474;
                               &#9474; Otra razón del fallo puede ser también que esté          &#9474;
                               &#9474; ejecutándose otro proceso pppoe y que éste esté          &#9474;
                               &#9474; controlando el módem. 
```

hice "sudo killall knetworkmanager" y "sudo killall networkmanager" pero me sigue dando el mismo mensaje, y funcionando la conexión :lolflag:

---

### Post by Hei Ku on 2007-07-30
para que necesitas el pppoeconf? Por lo que pusiste de tu configuracion, te conectas por DHCP, asi que no te hace falta. Para que lo queres utilizar?

---

### Post by SLA_leandrin on 2007-07-30
JEJE la verdad que ni idea. 
De redes no se mucho, como lo podrán apreciar, del resto me doy maña bastante. Pero no logro desactivarle el LowId en el mule ni el firewall propio del router.... en el menú de la fotito de más arriba no hay ninguna opción referida al port-forwarding o similares.

---

### Post by Hei Ku on 2007-07-30
volve a pegar la foto del router que no salio bien. solo se ve la imagen chica, pero sin link para agrandarla. Quizas viendo en el menu pueda haber una opcion similar.

Por lo que contas, en tu maquina no tenes que tocar nada, es un tema del firewall que tiene configurado el router. Veremos que se puede hacer. Quizas alguien tiene mas experiencia con esta clase de routers y te puede dar una mano.

Eso si, el pppoeconf en este caso creo que no tiene nada que ver, asi que no te preocupes por eso.

---

### Post by SLA_leandrin on 2007-07-31
OK ahi está mas grande:

[IMG]http://img211.imageshack.us/my.php?image=putamadre1lc3.png[/IMG]

[LINK]("http://img211.imageshack.us/my.php?image=putamadre1lc3.png")

---

### Post by Hei Ku on 2007-08-01
Si vas a configuracion inicial, que opciones te aparecen?

---

### Post by faktorqm on 2007-08-01
fijate en esto ke onda:

[http://www.adslayuda.com/foro-viewtopic-t-53368.html](http://www.adslayuda.com/foro-viewtopic-t-53368.html)

EN ESTE FORO encontre mejor info, cuanto menos es argentina:

[http://forum.telecomsucks.com/index.php?showtopic=4178](http://forum.telecomsucks.com/index.php?showtopic=4178)

en este sitio, te dice como para varias versiones de tu modem:

[http://www.portforward.com/english/routers/port_forwarding/Huawei/SmartAX-MT882/default.htm](http://www.portforward.com/english/routers/port_forwarding/Huawei/SmartAX-MT882/default.htm)
[http://www.portforward.com/english/routers/port_forwarding/Huawei/SmartAX-MT882v2/default.htm](http://www.portforward.com/english/routers/port_forwarding/Huawei/SmartAX-MT882v2/default.htm)
[http://www.portforward.com/english/routers/port_forwarding/Huawei/SmartAX-MT882v3/default.htm](http://www.portforward.com/english/routers/port_forwarding/Huawei/SmartAX-MT882v3/default.htm)

Bueno, espero que te sirva, si tenes dudas no dudes en postear. salu2!!

---

### Post by SLA_leandrin on 2007-08-01
> **faktorqm said:**
> 
EN ESTE FORO encontre mejor info, cuanto menos es argentina:

[http://forum.telecomsucks.com/index.php?showtopic=4178](http://forum.telecomsucks.com/index.php?showtopic=4178)


Que grande faktorqm, ese link es el que corresponde al modem mio... ahora a meter mano!!

---

### Post by guisheca on 2008-01-29
Que tal a todos los muchachos, soy nuevo por acá, me registré hace mucho tiempo en el foro pero nunca participé.
En fin sin mas preambulos yo tengo la respuesta a los problemas de apertura de puertos en este modem (huawei SmartAX mt882).
La respuestá está [acá]("http://guisheca.wordpress.com/?s=huawei+SmartAX+mt882") lo descubrí yo con el tiempo ya que no existe tutorial al respecto para el modem en cuestión, por alguna razón los que hay para este modelo no coinciden con lo que realmente tenemos.
Pero acá está, para todos los argentinos que tenemos arnet y el modem huawei SmartAX mt882 con esto se solucionan los problemas de apertura de puertos y por ende las id bajas en la mula.
Nos vemos. Espero que no sea tan tarde.

---

