---
title: "problema con conexion a Speedy con modem xavi x8821r"
date: 2007-11-28
forum: Argentina Team
---

### Post by leo_7.10 on 2007-11-28
bueno la cuestion es q quiero hacer la conexion con ese modem y no puedo, ya intente de todo y sigo sin poder conectarme...me podrian ayudar 
hice un plog y àrece q hay un problema con el certificado PAP puede ser?
gracias

---

### Post by BiTFx on 2007-11-28
Hola, el modem es Ethernet o USB??

---

### Post by leo_7.10 on 2007-11-29
si es un modem ethernet. y repito hice todo para poder conectarme y nada...hice pppoeconfig y nada, hice gedit /etc/ppp/options (o parecido)  y reforme una entrada y nada... me pueden ayudar por favor?? 
gracias

---

### Post by faktorqm on 2007-11-29
te ayudamos, estamos para eso........................................................

tips antes de decirte exactamente que tenes que hacer:

1) pusiste un cable ethernet del modem a tu compu?
2) si pones el comando ifconfig en la consola que te muestra? por favor postea la salida
3) en windows, sin tocar nada ya estabas conectado o le dabas al iconito para conectarte?
4) que empresa tenes de conexion a internet?
5) version de ubuntu (innecesario, pero por las dudas)

c vemo!

---

### Post by leo_7.10 on 2007-11-29
1- si el cable conectado es de ETHERNET
2-al hacer ifconfig me parce q no salia nada...despues probare de nuevo y posteare lo q salga
3.-no en windows para conectar le doy al iconito
4- lo de la empresa jejej esta en el titulo : Speedy de telefonica argentina
5- es ubuntu 7.10 gusty gibbon (mal escrito me parece)

por favor espero q sea solucionable estoy bastante desperado!!
gracias

---

### Post by BiTFx on 2007-11-29
Hola, yo tengo un modem ethernet [SIZE=2]**Huawei** MT810 [/SIZE]y estos son los pasos que seguí para conectarme a través de Speedy:
 
 
Esto lo pongo de memoria, estoy en el trabajo y tengo win, cuando llegue a casa chequeo bien y corrigo los detalles, tal vez me confundo en la ubicación de algun menu, o algo por el estilo, pero tal vez te guie.

Primero que nada, vamos a ver la configuracion de tu placa de red, y si está habilitada:
 
**Sistema -> Administracion -> red** (seguramente te pida la contraseña de usuario, que es la que usas para loguearte en Ubuntu)
 
Ahi doble click sobre la placa de red que está conectada al modem de speedy, supongo que tenes una sola placa.
 
Ahora en la ventanita que se abre desmarcá la opción que aparece arriba a la izquierda (de la ventanita) y Seleccioná en la lista desplegable **IP Fija**, poné la ip que te proporciona speedy (en mi caso es **192.168.1.10**), **Mascara de subred** (hace click y se pone automaticamente 255.255.255.0) en puerta de enlace yo pongo **192.168.1.1**
 
Ahora en la solapa de la derecha (**Propiedades**) colocá los DNS que te dieron, los mios son: **200.51.211.7** y el secundario es **200.51.212.7**. 
 
Ahora cerrá la ventanita, y listo esta parte.
 
Encendé el modem de speedy y chequea que esté conecatdo el cable entre él y la placa de red de tu pc.
 
Ejecutar en la **Terminal**
 
**sudo pppoeconf** (Si no encuentra el comando ejecuta: **sudo apt-get install pppoeconf**)
 
Se abre una Interfaz, donde automáticamente detecta la placa de red que está conectada al modem, y te va guiando paso a paso (debés utilizar el teclado para avanzar e ir llenando los campos requeridos, el mouse no hace click aquí, si en algo tenés dudas, dejá seleccionada la opcion por defecto, y dale [enter]), luego te pide el **usuario** para conectarte a speedy, despues la **contraseña**, y los **DNS**, aunque no los puse nunca aquí, los configuré en la placa antes como te describí al principio.

Ahora te pregunta si querés conectarte YA, luego te pregunta si querés que Autoconecte al arrancar Ubuntu (yo le puse que no), y te da los comandos para **conectarte** y **desconectarte** (anotalos por las dudas), aunque en mi caso **aparecen accesos directos para esto** (**después que reinicies Ubuntu**) arriba a la derecha dodne está el iconito de 2 pc's haces un click y en Conexiones... (no me acuerdo el nombre del menu) vas a encontrar 2 opciones, conectar por modem y desconectar (creo que ese es el nombre, luego corrijo, perdón por los errores), pero en esa parte están, seguro que los encuentras, pero solo despues de reiniciar Ubuntu.

Bueno, espero que te sirva de algo esta improvisada guia de memoria.

Saludos.

---

### Post by leo_7.10 on 2007-11-29
ahora voy  a probar esto ultimo q me dijiste aunque no cre q funcione  (re desesperanzado) 
pero igual te pongo lo q  me pediste de la ifcong aca va lo q me aparecio:

eth0      Link encap:Ethernet  HWaddr 00:18:F3:D3:87:54  
          inet6 addr: fe80::218:f3ff:fed3:8754/64 Scope:Link
          UP DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Metric:1
          RX packets:17 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:1020 (1020.0 b)  TX bytes:5663 (5.5 KB)
          Interrupt:20 Base address:0xcc00 

eth0:avah Link encap:Ethernet  HWaddr 00:18:F3:D3:87:54  
          inet addr:169.254.8.56  Bcast:169.254.255.255  Mask:255.255.0.0
          UP DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Metric:1
          Interrupt:20 Base address:0xcc00 

lo        Link encap:Bucle local  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK CORRIENDO  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:2368 (2.3 KB)  TX bytes:2368 (2.3 KB)
 eso es-...igual como hago para poner ip fija si es dinamica'?? pongo la del servidor speedy?? no?

---

### Post by leo_7.10 on 2007-11-29
leo@leo-ubuntu:~$ plog
Nov 29 14:44:36 leo-ubuntu pppd[7695]: Plugin rp-pppoe.so loaded.
Nov 29 14:44:36 leo-ubuntu pppd[7697]: pppd 2.4.4 started by root, uid 0
Nov 29 14:44:36 leo-ubuntu pppd[7697]: PPP session is 1395
Nov 29 14:44:36 leo-ubuntu pppd[7697]: Using interface ppp0
Nov 29 14:44:36 leo-ubuntu pppd[7697]: Connect: ppp0 <--> eth0
Nov 29 14:44:36 leo-ubuntu pppd[7697]: Remote message: permission denied
Nov 29 14:44:36 leo-ubuntu pppd[7697]: PAP authentication failed
Nov 29 14:44:36 leo-ubuntu pppd[7697]: Connection terminated.

eso es lo q me dio el plog q hice. capaz q sirve de algo no se...lo pongo igual

---

### Post by leo_7.10 on 2007-11-29
[[IMG]http://img98.imageshack.us/img98/1328/dibujogw6.th.jpg[/IMG]](http://img98.imageshack.us/my.php?image=dibujogw6.jpg)

en esta imagen es lo q me deberia mostrar no?? (sin conexion inalambrica)
bueno la cuestion es q no me muestra asi me muestra conexion telefonica y otra q ahora no me acuerdo pero la de ethernet no me la  muestra...como hago para q la muestre??
 
me parece q tengo q instalar los drivers de esa tarjeta es una Realtek RTL8139/810x Family Fast Ethernet NIC

---

### Post by faktorqm on 2007-11-29
escuchame, no te desesperes, se que estar sin internet es desesperante, pero lo que hay que hacer es:

pasar el modem a modo "router" (esto te permite estar conectado de antemano, es decir, vos no clickeas sobre ningun iconito en windows para conectarte, prendes la compu y ya estas conectado, es igual en linux, y no usas el pppoeconfig que es re molesto).
despues habilitas el dhcp para la lan y lo habilitas en tu maquina tb, asi te olvidas de configurar algo.
hace una cosa, busca el manual del router y postea el link asi te digo paso a paso como se hace. no es que no lo quiera hacer yo, es que realmente no tengo tiempo. salu2!

---

### Post by leo_7.10 on 2007-11-30
encontre unos manuales decian q tenia q poner en la barra de direcciones  una direccion de ip i entrar pero la cosa es q no entra...como hago??

---

### Post by leo_7.10 on 2007-11-30
si ya pude entrar ahi pero como hago para cambiar a enrutador¿¿

---

### Post by faktorqm on 2007-12-02
pasame el manual por que cambia segun cada marca la manera. salu2!

---

### Post by leo_7.10 on 2007-12-02
[http://www.speedy.com.ar/soporte.php...o=216&root=132](http://www.speedy.com.ar/soporte.php...o=216&root=132)
aca esta el manual y ya lo intente y parece q no se puede...puede q haya problema con la placa de ethernet??

---

### Post by faktorqm on 2007-12-02
buenisimo, pense que no estaba el manual...
che si se puede, yo lo hice mil veces. que parte es la que no te anda?

acordate de resetear el modem a valores de fabrica antes de hacer el tutorial ese. una pregunta: estas entrando bien al tutorial? es el que dice en modo router -< xavi 8121 blabla en la page de speedy no?

sino podes o te detiene algo, resetea el modem a valores de fabrica, pone tu eth0 (si es la que esta conectada al modem) en dhcp y segui el tutorial. contame como te fue. salu2!

---

### Post by pablo0469 on 2007-12-04
Yo tengo ese modem, y antes de hacerlo configurar como router (te comento que es bastante complicado respecto a los demas, al que vino a casa le costo bastante), simplemente usaba el comando:

sudo pppoeconf

Eso si, jamas logre que funcionara la opcion de iniciar la sesion conectado. En los monitores tenia que hacer click en desconectar y correr de nuevo este comando.

En teoria, deberia funcionar, y te va a sacar del apuro.

Saludos.

---

### Post by pablo0469 on 2007-12-04
Algo mas:

Lamento comunicarte que segui muchos tutoriales para configurarlo yo mismo como router, pero ninguno funciono, cuando lo configuraron delante mio, a todos le faltaban mas de la mitad de las maniobras. En serio que no es nada simple poner como router a este xavi.

La mejor inversion que podes hacer, es llamar a alguien que sepa.

Saludos.

---

### Post by faktorqm on 2007-12-04
vamos muchachos animo que es re re facil !!!! les cuento, al que vos llamas a ese "que sabe", bueno, soy yo. Le doy soporte tecnico a oficinas de abogados, tengo un par de fabricas ahi por San Martin, y particulares. Y uno de mis clientes tiene ese modem y se le rompe cada 2 minutos. al final era el modem, llamo a speedy y se lo cambiaron.

los que van a tu casa a conectarte speedy o lo que sea no saben nada de nada, y te lo digo por que compañeros mios de la secundaria trabajaron haciendo eso y no sabian nada de nada, y si se les ponia dificil, reseteaban el modem, y le dejaban el rpppoe o alguno de esos y chau. (Argento style)
es mas, el que vino a mi casa de speedy aquel dia, lo hice conectar la conexion a la compu de mi vieja, el chabon la instalo asi no mas, yo fui, y lo deje todo en modo router. (igual es un zyxel, mas facil). aparte no queria ke me tocara la computadora ¬¬

bueno vieja configuralo dale no seas vago! si no te anda postea que te ayudo. (son $50 :P)

---

### Post by leo_7.10 on 2007-12-04
es q lo quise hacer tal como decia el manual y no pude!!!
aydame please...es q es un embroyo...

---

### Post by leo_7.10 on 2007-12-13
uy parece q nadie sabe como ayudarme...y todavia no me puedo conectar a internet :S 
no conoce nadie a alguien q sepa mucho??

---

### Post by faktorqm on 2007-12-14
todavia no pudiste?? postea exactamente en que parte del tutorial te quedas, si no podes es por que tenes ip dinamica en algun lugar, o el cable mal, o algo. pone ubuntu en dhcp y reinicia el modem a valores de fabrica (no alcanza con apagarlo y prenderlo) le tenes que dar al reset derecho. no te preocupes por las configuraciones, eso lo vemos despues. si tenes firestarter instalado desactivalo por completo, despues lo activamos si es que no sabes configurar el firewall del modem (lo cual suele ser lo mas recomendado). Salu2!

---

### Post by pablo0469 on 2007-12-16
Asi que laburas por San Martin, Faktorqm? Mira que casualidad, yo soy de esos pagos...

Y de verdad, el pibe que configuro este modem como router (sabe mucho) estuvo bastante tiempo y se metio en unas cuantas opciones en la IP del modem, que en los manuales y tutoriales ni figuraban. Segun me comento, es uno de los mas "dificiles" de configurar (poco practico y poco intuitivo).

Ojala puedas resolver este tema por aca. Tambien me interesa a mi aprender como cuernos se hace :)


Saludos.

---

### Post by leo_7.10 on 2007-12-20
no me trabo en ningun momento del tutorial...lo hago todo pero yame a speedy y me dijeron q el modem no es routeable..asi q no se va apoder...otra solucion no hay??
no puede ser un problema insolucionable...

---

### Post by leo_7.10 on 2007-12-24
va a llegar el 2008 y nadie ma sabe solucionar esto....
q mal

---

### Post by faktorqm on 2007-12-24
el modem si es routeable, sino no estaria en el tutorial en speedy. ¬¬ deberias saber que los que te atienden de soporte tecnico de las empresas no saben absolutamente nada de nada.

tenes que hacer todo lo que yo dije, sino va a ser imposible ayudarte. yo entiendo que no sabes nada de redes y que necesitas internet, pero tambien tenes que poner colaboracion de parte tuya, desesperandote, no vas a ningun lado.

creo q por tercera vez te repito: pone al windows o al ubuntu en dhcp y reinicia el modem a valores de fabrica, es lo mismo en cualquier sistema operativo. desde el navegador, (ie, opera, firefox) pone la direccion por defecto del modem, y hace toooodo lo que te dice en el tutorial. 
Aca una cosa, ASEGURATE AL 100% que estas poniendo bien los datos, y que te aparece EXACTAMENTE EN TU MONITOR LO MISMO QUE EN EL TUTO. tu user de conxeion, la pass al igual que los circuitos vpi y vci, el tipo de encapsulacion y el protocolo de autenticacion (CHAP/PAP) DEBEN ESTAR SEGUN EL TUTORIAL.
si tenes dudas sobre tu nombre de usuario y pass, LLAMA A SPEEDY.

Despues de eso, tiras "ipconfig" en win, o "ifconfig" en gnu/linux, y te fijas que tengas asignada una ip, una mascara, una puerta de enlace y unos dns. si tenes todo eso, te tiene que andar tranquilo internet.
Sino fijate en la parte de diagnostico del router, a ver si es problema de wan, de lan, de nombre de usuario, y esas cosas. feliz navidad para vos y tu flia. salu2!

---

### Post by leo_7.10 on 2007-12-27
ta gracias igualmente!!!
a el modem no es exatamente el modelo q apararece en la pagina de speedy...hice el tuto y cuando lo termino donde dice q en el tuto q tiene q aparecer la encapsulation "routing" y la direccion de ip mia no cambia esto sino q queda como antes...y otra cosa viste eso de la autenticacion CHAP/PAP bueno solo tengo la PAP o sea me viene faltando la CHAP 
se puede hacer algo al respecto??
gracias por ocuparte de mi tema sos el unico q lo hace...

---

### Post by jpmorelli on 2007-12-27
> **leo_7.10 said:**
> 
se puede hacer algo al respecto??
gracias por ocuparte de mi tema sos el unico q lo hace...

Leo, tratá de evitar éste tipo de comentarios, no todos tenemos las mismas configuraciones en nuestras casas y por ende es mejor no decir nada antes que marear con consejos que pueden no servirte.
Si estamos acá no es obligación contestar sino ayudar en lo que podamos y que nos ayuden cuando otros pueden.
Suerte con tu tema y no te preocupes que ya va a salir andando y vas a aprender un montón cuando lo logres. :)

---

### Post by faktorqm on 2007-12-28
Bueno pibe, más te vale que con esto lo saques andando por que sino te voy a ir a buscar a tu casa y voy a hacer que te conectes haciendo la parabolica humana.....   ajjajajjaja

01) Mira esta foto, se parece a tu modem no? si, si, es el tuyo! tenes que meter un clip en el agujerito que esta a la izquierda de la conexión ethernet. El que tiene el número 2. La leyenda dice "Resetea el modem a valores de fábrica si mantenes apretado este boton"
Creo que 10 segundos alcanza. Luego lo soltas.

[[IMG]http://img338.imageshack.us/img338/8773/deatrastq8.th.png[/IMG]](http://img338.imageshack.us/my.php?image=deatrastq8.png)

NOTA: No se si te fijaste, pero en el final del tutorial de speedy, te dice que metas un clip en el modem, blablabla, y te dice "3 veces en un segundo" que lo hagas..... jajajajaj la verdad me parece bastante improbable que esto suceda, pero bueno, vos dale hasta que reinicie, no sé....

02) El cable que va de la boca 3 a tu computadora, tiene que ser cruzado. Si esta a un switch, o un hub, tiene que ser cruzado. Si no sabes si tu cable está cruzado o no, agarrá las dos puntas, miralas del lado que no tiene la traba, y de izquierda a derecha tienen que tener distintos colores. Si ambos tienen los mismos colores en la misma ubicacion de izquierda a derecha, es derecho. Si no, es cruzado.

03) Una vez hecho esto, agarrás y te fijas si la luz de LAN del modem (La cuarta de izquierda a derecha, o la segunda de derecha a izquierda) está prendida. Si está prendida, agarrás y ponés en la placa de red configuración por DHCP. No importa en que sistema operativo estés, es lo mismo para todos. Entonces ahora, con el DHCP puesto y el modem reseteado, agarras una terminal o un "cmd" y escribis:

en ubuntu: ```
ping -c 4 192.168.1.1
```

en windows: ```
ping 192.168.1.1
```

Tanto en ubuntu como en windows, te tenes que fijar que el 100% de los paquetes hayan llegado a destino. Si llego todo, segui, si tenes problemas, cambia de SO, por las dudas, y postea el problema si es que sigue sin funcionar.

p.d.: si queres probar algo de ultima por si no te funciona, pone los siguientes datos:

dirección IP: 192.168.1.4
máscara de subred: 255.255.255.0
puerta de enlace: 192.168.1.1
DNS: 192.168.1.1

y luego de esto volves a probar lo del ping. A veces, te conviene reiniciar con el nuevo IP por que a veces no te lo toma, o ciertos SO's necesitan reiniciar para cambiarlo, etcetc vos fijate.

04) Ahora bien, ya tenemos la base establecida para poder empezar a configurar el bendito modem. Abris algun explorador de internet, y escribis en la barra de direcciones "192.168.1.1". Ahi te va a pedir, usuario y contraseña. Ponés de usuario "admin" y "admin" la password, SEGÚN EL MANUAL ORIGINAL. Entonces ahí entras a la configuracion del modem. SI NO PODES ENTRAR, PARA ACA Y POSTEA EL PROBLEMA.

[[IMG]http://img171.imageshack.us/img171/3526/confighomeof5.th.png[/IMG]](http://img171.imageshack.us/my.php?image=confighomeof5.png)

Si estas aca, estamos bien.

NOTA: A partir de acá, estoy escribiendo este tutorial según los datos del tutorial de speedy, pero con el manual del router, asi que quedate tranquilo que todas las configuraciones son las correctas.

05) Bueno ahora, hacemos click en la pestaña WAN, luego en ATM VC. Está a la derecha de DSL, justo abajo de donde dice WAN. Ahi te va a aparecer algo, acá en el manual dice que te aparece algo y se llama "aal5-0". Ahi le das al boton ADD.

[[IMG]http://img171.imageshack.us/img171/3893/atmvclb4.th.png[/IMG]](http://img171.imageshack.us/my.php?image=atmvclb4.png)

06) Ahi te aparece una ventana. 
En la casilla VC-Interface pones: aal5-2.
En la casilla VPI pones: 8
En la casilla VCI pones: 35
En MUX type va: LLC
La ultima no importa. NO LA TOQUES, dejala asi. (deberias encontrar un 2 como valor)

Ahora le das al botón SUBMIT. 

06) Volves a hacer click en WAN, y ahora seleccionas PPP. (exactamente a la derecha del anterior) y haces click sobre el boton ADD y te aparece una nueva ventana.

En la casilla ppp interface: pone ppp-1.
En la casilla ATM VC HAY QUE PONER LA QUE CONFIGURAMOS ANTES, O SEA, LA AAL5-2.
El resto deja todo como esta.
En la casilla protocol tenes que elegir: PPPoE
en Service name: lalala
use dhcp: Disable
use dns: disable
default route: enable
security protocol: PAP
login name:
password:

bueno en login name, por lo general va algo del estilo <nro de tel>@speedy y en la password la que hayas puesto. ES VITAL que sepas exactamente cual es tu nombre de usuario y tu contraseña, de lo contrario no servirá de nada.

Ahi le damos al botón SUBMIT. 

07) Ahora vas a la ficha ADMIN. y le das a lo que dice "commit & reboot". Te fijas que el reboot mode este en "reboot" y ahi le das a commit. Entonces ahora te deberias conectar a internet sin necesidad de ningun marcador. Si no te conecta, espera un toque por que capaz tarda un minuto o dos en establecer la comunicacion, eso depende. si no te andan las paginas web's, proba de hacer ping a google con "ping www.google.com" a ver que te dice. si te dice que no puede encontrar el nombre, el error es de dns o de conexion, asi tambien te recomiendo que reinicies la compu de paso.
Si seguis sin internet, podes entrar al modem del mismo modo que antes SIN REINICIAR A VALORES DE FABRICA y posteas la pantalla a ver que error te tira. si te fijas y en el status esta todo ok, podes ir a la ficha ADMIN -> system LOG y ver ahi cual es el problema.

Te dejo aca el manual original, para que lo veas si tenes alguna duda.

MANUAL: [http://rapidshare.com/files/79613606/25_User_Manual.pdf](http://rapidshare.com/files/79613606/25_User_Manual.pdf)
TUTO DE SPEEDY: [http://www.speedy.com.ar/soporte.php?event=detalle&idcontenido=216&root=132](http://www.speedy.com.ar/soporte.php?event=detalle&idcontenido=216&root=132)

Yo segui la parte del manual que dice "PPPoE Route Configuration", solo que la parte de NAT la omiti por que tenes una computadora sola. Si tenes mas computadoras, igual ahi te explica como tenes que hace,r el problema de eso es que asume IP fija por parte del proveedor de internet, cosa que no ocurre con Speedy.

Bueno espero que te haya servido, a ver si de una vez por todas configuras este modem y llegas al 2008 en paz. Salu2 y feliz año si no nos vemos. 

:guitar:

---

### Post by leo_7.10 on 2007-12-30
bueno perdon si ofendi pero me parecia extraño q en un foro tan grande uno solo se ocupe del tema...si tbm yo tengo un modem extraño y no cualquiera sabe de el ....

a gracias por el tuto tuve un problema solo al proceder cuando voy a WAN->ATM VC-> ADD y quiero poner todo lo q me decis me dice q la entrada ya existe, hay otro asi con la unica diferencia q el aal5-0 y no aal5-2 es lo msmo??

igual voy a seguir q ver q pasa...gracias +
y felis año nuevo a todos!!

---

### Post by Israphel on 2007-12-30
Ese modem es malisimo! y ahora speedy les da ese modem a todos (ya no entregan modems usb "por suerte"), pero te dan esa basura. En windows creas la conexion y haces conectar (o sea esta en modo modem, no router) y no podes acceder ni por navegador ni por telnet, así que no se como pasarlo a router y configurar los datos adentro para meterlo en un switch y bla bla.

El ppeoconf te dice que no encontro nada y dentro de poco lo tiro por la ventana.

---

### Post by faktorqm on 2007-12-30
> **leo_7.10 said:**
> bueno perdon si ofendi pero me parecia extraño q en un foro tan grande uno solo se ocupe del tema...si tbm yo tengo un modem extraño y no cualquiera sabe de el ....

a gracias por el tuto tuve un problema solo al proceder cuando voy a WAN->ATM VC-> ADD y quiero poner todo lo q me decis me dice q la entrada ya existe, hay otro asi con la unica diferencia q el aal5-0 y no aal5-2 es lo msmo??

igual voy a seguir q ver q pasa...gracias +
y felis año nuevo a todos!!

hola, lo que podes hacer, en lugar de crear uno nuevo es poner editar, que es el iconito del lapiz a la derecha de la conexion digamos. si no lo encontras fijate en el manual que te pase el link a ver si hay alguna foto que te muestre. Despues de que pones todos los datos, lo unico que cambia es que cuando vayas al PUNTO 6 de mi tutorial, lo unico que tenes que cambiar es, donde elegis "aal5-2" poner "aal-5-0".

Lo único que me llama la atención es que no puedas agregar uno nuevo, por que yo lo hice segun el manual original, no invente nada digamos... pero bueno, vemos como sale la cosa.

el modem, es dificil de entender, pero desde el punto de vista conceptual es muy facil, tenes varias interfaces logicas, otras fisicas, las configuras, y ya.

Si no otra cosa que se puede hacer es habilitar el control remoto por wan digamos para acceder a la interfaz de configuracion web. asi podria entrar yo desde mi casa a configurarlo, pero esa opcion no la vi en este router, y el de mi casa la tiene, deshabilitada obvio, pero la tiene.

Salu2 de fin de año, ojalá puedas tener internet. salu2!!

---

### Post by rbarbe on 2008-04-29
Segui las instrucciones de BiTFx, y me pude conectar enseguida con el módem XAVi X8821r.

Muchas gracias BiTFx!!!!!!!

---

