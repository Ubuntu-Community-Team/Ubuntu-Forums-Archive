---
title: "[SOLVED] Internet - Como conectarme con un modem zyxel 660"
date: 2008-04-13
forum: Argentina Team
---

### Post by losoollenos on 2008-04-13
Ante todo saludos para todos. Los molesto porque acabo de instalar ubuntu 7.10 (no sin grandes dificultades),al que espero empezar a entender de a poco preguntando. Y para poder conectarme a internet ya busqué por todos lados pero no lo pude lograr. Tengo speedy de Argentina, el moden es un zyxel 660 (se conecta a la placa de red) y bue, agradecería mucho cualquier aporte lo más claro posible.
Desde ya muy agradecido, saludos para todos y hasta pronto....

---

### Post by Mauro22 on 2008-04-13
Hola!!    

Para ayudarte necesitamos mas datos.


1) Ubuntu 32 o 64bits?

2) Placa de red Onboard?

3) Marca/Chipset/Motherboard (si es onboard)



:guitar:

---

### Post by leonardo83 on 2008-04-13
Bueno mi estimado, lamentablemente yo no tengo ubuntu, es decir lo tenia pero ahora no funcioan y bue, mejor no entrar en detalles... :(:(:(
Te cuento como hice yo para conectarme, mimso modem, mismo proveedor, etc :

1) abris la consola y escribis sudo pppoeconf (si no encuentra el comando ejecuta: sudo apt-get install pppoeconf)
2) esto te va a abrir una ventana de fondo azulado donde empezas a configurar la conexion, por ejemplo te detecta la placa ethernet y demas
3) solo resta cargar los datos que te piden, hay que borrar user y cargar ***@speedy o el usuario que tengas y en pass lo mimso, el dni del titular seguro
4) si en algun paso tenes dudas mandale lo que esta elegido por defecto que no hace falta cambiar nada
5) luego te dice si queres conectarte en ese mimso moento, ponele si o no segun te parezca.
Despues te va a preguntar si queres que se conecte solo al iniciar ubuntu, elegi lo que te parezca, y despues de reiniciar la pc se te va a crear dos iconos en la parte donde esta el icono de la pc, arriba a la derecha.

Creo que con esto mas o menos te vas a poder guiar, suerte man decinos como te fue. Un abrazo metalico! :popcorn:

---

### Post by faktorqm on 2008-04-14
leonardo83: haciendo lo que vos propusiste, tenes 2 problemas bastante grandes:

1) estas utilizando recursos de tu pc para conectarte cuando el modem lo puede hacer perfectamente, y te digo mas, en una instalacion, como haces? y/o si por algun motivo el programa no anda? :(

2) haciendo eso vos estas "directamente" conectado, es decir, no podes agregar una pc a tu red ( apesar de que necesitarias un hub/switch) y encima tu firewall es el que "ve" internet, asi que definitivamente la respuesta es NO.

La solución más correcta, es hacer que el modem marque y se conecte solo y activar el firewall del mismo, asi no me tengo que preocupar por nada y que haga NAT.

No te lo tomes a mal leo, no soy muy diplomatico para decir las cosas, pero me interesa que aprendas y que la próxima notes vos mismo las diferencias :KS

Aclaraciones con respecto al método: Es lo mismo hacerlo desde windows o desde linux, lo que si AMBOS deben tener la misma configuración de red.

Para esto hacemos: 
1) Resetea el modem a valores de fábrica, si nunca lo tocaste, no hagas nada.

2) En tu placa de red pone:

Dirección IP: 192.168.1.2
Máscara: 255.255.255.0
Enlace: 192.168.1.1
DNS: 192..168.1.1

Según este tuto la red es la 0 en lugar de la uno, si tu manual (el del modem) se corresponde a este tuto, deberias poner:
[http://www.adslzone.net/tutorial-20.11.html](http://www.adslzone.net/tutorial-20.11.html)

Dirección IP: 192.168.0.2
Máscara: 255.255.255.0
Enlace: 192.168.0.1
DNS: 192..168.0.1

3) Abri un explorador y escribi "192.168.1.1" ó "192.168.0.1" y te tiene que aparecer una pagina preguntandote la contraseña. Si tenes el manual del modem fijate cual es la que trae por defecto, sino creo que es usuario: admin y contraseña: 1234.

4) Ahora seguís el tuto como dice ahi.

NOTA: La última parte de los DNS no lo hagas, y en usuario de adsl deberia ir tu numero_de_telefono@speedy y la contraseña que hayas elegido, por lo general 123456.

Reinicias el modem, y listo! sin tocar nada ya tenes internet. Para abrir puertos en el firewall, en la ventana principal del router, vas a NAT y luego a SUA only, y te aparece la tabla.

Espero que te haya servido, y que muchos hayan aprendido :D Salu2!!

---

### Post by oktubrer on 2008-04-14
> **faktorqm said:**
>  La solución más correcta, es hacer que el modem marque y se conecte solo y activar el firewall del mismo, asi no me tengo que preocupar por nada y que haga NAT.

A mi entender, no es "la solución más correcta" sino cuestión de gustos.  Si tenés solo una PC, los recursos que utilizas realizando la conexión por pppoeconf son mínimos y natear el modem no te agrega mucho.
Es más, si queres usar un p2p probablemente tengas que habilitar los puertos necesarios (y en algunos modems no funciona del todo bien).

Ahora si tenés más de una pc tenés razón, no solo es más correcta, es la única solución (a menos que quieras usar alternadamente la conexion en una u otra.)

---

### Post by losoollenos on 2008-04-14
Señores, agradezco todos sus aportes...y les cuento. Tengo ubuntu 7.10, en la parte de Red aparecen dos opciones: modem y cable. En propiedades de opción cable aparece la ventana con opción Itinirante tildada; la destildo y selecciono configuración automática, con lo cual ya no se pueden completar los espacios de ip, máscara,etc.
Luego abro firefox, le pido que conecte con 192.168.1.1 y .0.1 pero da Not found.
Entonces probé como lo dijo Leonardo y se conectó, pero al resetear la pc para ver si aparecían los dos íconos no se conectó más ni tampoco aparecieron los íconos. Puede ser que no esté detectando el modem?, disculpen si dije una barbaridad, toy más perdido que....
Ayúdenme por favor a repasar las configuraciones porque pude haber tocado algo sin saber....
Saludos

---

### Post by oktubrer on 2008-04-14
En uno de los pasos del pppoeconf (casi al final) te pregunta si queres que se conecte automáticamente al inicio.
Le tendrías que poner que si, al reiniciar si tenés el modem prendido y sincronizado se conectaria solo.

---

### Post by faktorqm on 2008-04-14
> **oktubrer said:**
> A mi entender, no es "la solución más correcta" sino cuestión de gustos.  Si tenés solo una PC, los recursos que utilizas realizando la conexión por pppoeconf son mínimos y natear el modem no te agrega mucho.
Es más, si queres usar un p2p probablemente tengas que habilitar los puertos necesarios (y en algunos modems no funciona del todo bien).

¿Para que voy a ocupar el 0,1% de mis recursos si el modem lo hace solo, o sea, el 0,0%? No tiene ningún sentido... Lo que los modem no funcionan tb es muy cierto, pero eso digamos que escapa a nuestras posibilidades.... el huawei wi-fi que da arnet es el ejemplo del ANTI-router jajajaj 
Aclaracion: hay modems que no soportan el modo router y tenes que morir si o si en el pppoeblabla feo.
Aparte reitero que el firewall de tu SO es el que se ve de afuera, ocasionando ciertos riesgos de seguridad.

Losoollenos: Si le pones configuración automática, debería de andar de todas maneras posibles, pero para eso abri una consola (aplicaciones -> accesorios -> terminal) y escribi "ifconfig". Vendria a ser el equivalente al ipconfig de windows. Ahi te fijas que ip te dio, si estas en la red 10.0.0.X la pagina de configuracion va a estar en 10.0.0.1.

El método según leonardo83 es el equivalente en windows a darle al botón conectar cuando terminas de meter el cd de speedy. Lo podes configurar para que cada vez que arranque te conecte, bueno en linux seria lo mismo. Yo no uso ese tipo de scripts, alguien que lo tenga t va a ayudar mejor. Salu2!

---

### Post by losoollenos on 2008-04-15
La verdad no logré conectarme más de ninguna forma. faktorqm, hice lo de ifconfig y me tiro una lista larga de items que sinceramente no le veo mucha diferencia con el chino.
No quiero abusar de tu paciencia, pero si podés dame explicaciones más básicas, una vez que pueda conectar internet ya me abrirá más posibilidades y no los **** tanto !!!
Gracias y saludos a todos !!

---

### Post by oktubrer on 2008-04-15
Ayudaría un poco que nos digas que pasa cuando seguís el pppoeconf, si da un error, en que momento, si llega hasta el final ok y no conecta, etc.

Ahora no estoy en casa como para hacerte un "paso a paso", pero lós unicos datos que tenés que tener son usuario, clave y me parece que los dns (de speedy son 200.51.211.7 y 200.51.212.7)
El usuario por lo general es tu_línea@speedy (o @speedy1m , o 2m, etc, depende el servicio contratado)

---

### Post by faktorqm on 2008-04-15
Pregunta: nos estas escribiendo desde la misma pc con windows? si es asi, ¿Como te conectas? "sin tocar nada" o conectandote con algun programa? Y de paso cañazo, si y solo si estas conectado "sin tocar nada" hace inicio -> ejecutar, luego escribi "cmd" y luego "ipconfig" y copia y pega la salida (entre tags de code por favor).

"sin tocar nada" es equivalente a que realmente no tocas nada, NO ES que pusiste el programa para que te arranque directamente sin preguntarte nada, vale la aclaracion :D salu2!

---

### Post by losoollenos on 2008-04-15
Si faktorqm, escribo con la misma máquina con windows. Creo que se conecta por medio de programa, porque antes usaba modem usb y sin hacer nada cambié el modem y uso el mismo acceso directo del escritorio.
Lo de tags de code ni idea a que te referís. Igualmente te paso por si acaso lo del cmd:

Microsoft Windows XP [Versión 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.
C:\Documents and Settings\Claudio>ipconfig
Configuración IP de Windows
Adaptador Ethernet Conexión de área local         :
        Sufijo de conexión específica DNS :
        Dirección IP de autoconfiguración : 169.254.16.169
        Máscara de subred . . . . . . . . : 255.255.0.0
        Puerta de enlace predeterminada   :
Adaptador PPP speedy               :
        Sufijo de conexión específica DNS :
        Dirección IP. . . . . . . . . . . : 190.51.94.211
        Máscara de subred . . . . . . . . : 255.255.255.255
        Puerta de enlace predeterminada   : 190.51.94.211

Saludos !!!

---

### Post by pol666 on 2008-04-15
Por favor estoy perdidisimo, Segun yo tenia entendio que los modem ethernet no consumen recursos...

Yo tengo uan sola PC, no esta en red local, me conecte mediante sudo pppoeconf.

Eso influye en mi velocidad de internet? :confused:

---

### Post by oktubrer on 2008-04-15
> **pol666 said:**
> Por favor estoy perdidisimo, Segun yo tenia entendio que los modem ethernet no consumen recursos...

Yo tengo uan sola PC, no esta en red local, me conecte mediante sudo pppoeconf.

Eso influye en mi velocidad de internet? :confused:

El tema de los recursos es porque estás corriendo un proceso que establece la conexión y la mantiene, a diferencia de un modem routeado que directamente se conecta solo. Pero es mínima la diferencia y no debería afectar tu velocidad de conexion.

---

### Post by faktorqm on 2008-04-15
Apoyo el último comentario de oktubrer.

Con respecto al ipconfig, los tags de code son los que te aparecen con el simbolo numeral (#) en la barra de herramientas de donde escribis para postear.

Ahi lo que estas haciendo es conectarte como si fuera pppoeconf pero en windows. Tenes 2 opciones, dejarlo asi y configurarlo en linux, o cambiarlo en los 2 para no usar software. La mejor (para mi) es la ultima, vos diras. Asi sé si te tengo ke postear un manual de pppoeconf u otro sobre el modem :D salu2!

---

### Post by losoollenos on 2008-04-16
Ayudame configurando el modem por favor, es la opción más lógica....
En el cd del modem hay un manual pero sólo para windows y creo que para mac, pero si necesitás algun dato de ahí te lo paso.
Muchas gracias

---

### Post by faktorqm on 2008-04-16
Por lo general no leo los manuales hasta que no se la contraseña por defecto del modem :D

Bueno, vamos por partes, como decia mi amigo Jack :P

Primero y antes que nada, si te sentis mas seguro en windows, hacelo desde ahi que es lo mismo. Yo igual te pongo los comandos para los dos.
Lee primero esta pagina que te explica como resetear el router a valores de fabrica.[http://www.adslzone.net/tutorial-20.20.html](http://www.adslzone.net/tutorial-20.20.html)

Segundo, agarras la placa de red en windows y le pones configuracion automatica a todo. (esto es en, click derecho sobre mis sitios de red -> propiedades. click derecho sobre "conexion de area local" -> propiedades, ahi en la ventana que te abre seleccionas "Protocolo TCP/IP" y le das a propiedades)
En linux, lo mismo, y por lo que tengo entendido ya lo hiciste.

Tercero, MIRA ESTE VIDEO:
[http://www.adsltodo.com/videopop.php?vid=1148327550&url=http://www.adsltodo.com](http://www.adsltodo.com/videopop.php?vid=1148327550&url=http://www.adsltodo.com)

Lo único que tenes que cambiar es el usuario y la contraseña, lo que ahi aparece como
adslblabla@telefonicanetpa lo tenes que cambiar, por 41260100@speedy, speedy1m o speedy2m (puse cualquier tel) y como contraseña OBVIAMENTE la que te dieron.
TAMBIEN TENES QUE CAMBIAR EL QUE SE LLAMA VCI, ahi aparece 32 PERO EN ARGENTINA ES 35.

Si no entendiste, no te parecio convincente el metodo, desde linux o windwos haces "telnet 192.168.1.1" y seguis este tutorial:

[http://www.adslayuda.com/Zyxel650-configuracion_multipuesto_ip_dinamica.html](http://www.adslayuda.com/Zyxel650-configuracion_multipuesto_ip_dinamica.html)

Ahora bien, si ya estas conectado a internet con los dos SO sin ningun problema, a partir de ahi ponemos ip fija para poder usar emule y esas cosas a maxima velocidad. Primero conectate y despues seguimos. Si te quedaste en algun punto, pateaste el modem, se te enfermo el perro, :lolflag:, DETALLA que fue lo que paso, y bajo que circunstancias, y que ingresaste vos en cada caso. Salu2!!

---

### Post by oktubrer on 2008-04-16
> **faktorqm said:**
>  a partir de ahi ponemos ip fija para poder usar emule y esas cosas a maxima velocidad 

¿Quisiste decir lo que dijiste? Ip fija? por más que el ISP te de ip dinámica?  Si se puede, quiero saber eso! :D

---

### Post by losoollenos on 2008-04-16
Bueno, sólo pude resetear el modem (desde el botón trasero del mismo), cuando le pido que busque 192.168.1.1 no lo hace ni desde EJECUTAR ni desde el explorador, tanto windows como linux.....

---

### Post by oktubrer on 2008-04-16
Es que lo encontraría solamente si tiene habilitado el dhcp, es más facil configurar la placa de red para que esté en la misma red que el modem.
Para esto, desde conexiones de red, hace un click con el botón derecho en "red de area local" y dale a propiedades.
Ahi hacele doble click al TCP-IP y configura lo siguiente:
Dirección IP: 192.168.1.5
Puerta de enlace o default gateway: 192.168.1.1
Máscara de subred: 255.255.255.0

Creo que con eso alcanza, ahora deberías poder conectarte con el modem y seguir el instructivo que te pasó faktorqm

---

### Post by faktorqm on 2008-04-16
> **oktubrer said:**
> ¿Quisiste decir lo que dijiste? Ip fija? por más que el ISP te de ip dinámica?  Si se puede, quiero saber eso! :D

Supongo que me entendiste mal, o que yo escribi mal, o ambos. Lo que quise decir es que si vos tenes dhcp no podes redireccionar puertos a tu placa, entonces a la compu le tenes que poner ip fija, y abrir los puertos en el modem, entonces ahi te conecta en alta el emule. Eso por un lado.
Lo del ISP es relativo, dependiendo del leasing time de la direccion ip que te den, nunca me meti a investigar pero podes "tocar" los paquetes para "mentirle" al reloj ese y quedarte con la misma ip por mas tiempo, pero esas son cosas de los geeks de assembler y nunca lo hice, pero me dijeron que se puede estirar  mucho el tiempo de refresco. Eso por otro lado.
Lo de la IP dinámica contra IP fija lo podes saltear usando DNS dinámicos (**QUE NO ES LO MISMO QUE IP FIJA**) para, por ejemplo, poner tu propia pagina web en tu casa.
Entonces vos pones [www.oktubre.com.ar](www.oktubre.com.ar) y el DNS te lo asocia a tu ip. Cuando el proveedor te cambia la IP, el tipo va y actualiza los DNS, y te asocia el nombre con tu nueva IP, y asi sucesivamente, entonces yo siempre entro a la pagina, pero vos cambias de ip todo el tiempo.
Hay 150000 de trucos para que emule ande mas rapido, si buscas en la web hay miles, pero capaz perdes un finde entero hardeneando el emule y de buenas a primeras tenes que reinstalar.... o algo y perdes todo....

losoolenos: capaz esta en otra red, justo el modelo tuyo, hace una cosa, prende la compu, y fijate el ipconfig en que red estas. LA IP QUE TE DIGA LA PUERTA DE ENLACE, ES LA QUE TENES QUE PONER EN EL EXPLORADOR.

ejemplo: >ipconfig
direccion ip: 192.168.1.2
mascara: 255.255.255.0
PUERTA DE ENLACE: 192.168.1.1 (ESTE NUMERO ES EL QUE TENES QUE PONER EN EL NAVEGADOR)

te paso las redes tipicas, para mas o menos lo veas. 

192.168.0.1 - 192.168.1.1 - 10.0.0.1 - 10.0.1.1

Salu2 y no dudes en preguntar.

---

### Post by oktubrer on 2008-04-16
Ta, hablabas de la ip fija en la pc, yo asumí que hablabas del router, y a pesar de haber dado soporte muuuuucho tiempo de adsl siempre asumo que hay cosas que no sé, asi que por las dudas te pregunté si habías querido decir eso.
Tema aclarado, del resto (dns dinámicos) ya estaba al tanto.
Saludos!

---

### Post by faktorqm on 2008-04-16
ahh mira vos, y para que empresa? por lo general (capaz no es tu caso) nunk saben nada los pibes que te atienden, y siempre te dicen, resetea el modem, pone el cd, hace esto y lo otro. yo siempre que tengo un problema termino hablando con un supervisor, y una vez hable con el supervisor del supervisor jajajaj me tenian podrido.
(ahora me rio, pero en ese momento les grite mucho)

te pregunto no para saber si sabes, sino para que si tenes manuales, "trucos", sugerencias, etc estaria bueno contar con eso. aca habia un pibe que laburaba en una empresa, y dijo que si necesitabamos nos daba manuales y esas cosas. Salu2!!

una cosa me olvide: por ejemplo, si siempre me van cambiando el ip dentro de una misma subred, y yo lo fuerzo a estar en esa subred, no es como tener ip fija y los gateways? sabes como funcionan "del otro lado" digamos?

---

### Post by oktubrer on 2008-04-16
Puf! pase por varias hasta que colgué el maldito headset.  Arnet, triste paso por AOL, Sinectis (luego Uol sinectis y luego la nada) y termine en Speedy pero gracias al cielo para empresas y grandes clientes, que no es lo mismo que atender a Doña Rosa.
Con respecto a los manuales, nada que no esté en internet, igual fui tirando todo, hace 3 años que dejé de ser soporte (en el laburo, con los conocidos uno nunca deja de ser soporte técnico)

> **faktorqm said:**
> una cosa me olvide: por ejemplo, si siempre me van cambiando el ip dentro de una misma subred, y yo lo fuerzo a estar en esa subred, no es como tener ip fija y los gateways? sabes como funcionan "del otro lado" digamos?

¿A que llamás "forzar una subred"?
El único beneficio de una ip fija es poder montar la cantidad de servidores que quieras sin necesidad de los programejos que mencionaste antes que te ofrecen dns dinámicos.  Pero si el isp te da una dinámica cada vez que te conectas, no hay nada que puedas forzar para que te de la que vos queres.

---

### Post by faktorqm on 2008-04-16
Claro, lo que yo decia era una avivada mas que nada, es decir, si un dia me dan la (tiro cualquiera) 152.145.35.21, pasado la 152.145.23.240, despues la 152.145.12.14 con mascara 255.255.252.0, estan todas en la misma subred. Entonces que pasa si yo pongo 152.145.24.14/20 y no la cambio: ¿no deberia forzar la existencia de ese ip en la red y tener el servicio igual que si tuviera dhcp? no creo que los chabones anden cambiando mucho de mascara a menos que usen vlsm. (o abusen de...) 
Capaz nada que ver... no sé. Salu2!

---

### Post by Hei Ku on 2008-04-16
te arriesgas a entrar en conflicto con otra IP. En general, en ese caso, la interfase se desactiva cuando encuentra el conflicto. Asi que no te conviene. :D
Por eso es que en el DHCP se configuran rangos asignables, para que las IP fijas esten fuera de ese rango.

---

### Post by losoollenos on 2008-04-16
Nuevamente les agradezco los aportes, yo sigo peleándola. Si hago como dice oktubrer, escribiendo en propiedades de tcp-ip los valores de ip, máscara, etc, se comunica con el modem y lo configuro tal cual el video y/o la guía. acepto, reseteo, reinicio, de todo un poco pero nada de internet. La única forma que se conecta es creando la conexión en forma manual con el asistente de windows.
Si dejo todo automático ni siquiera se comunica con el modem (poniéndole 192.168.1.1); respecto del valor de puerta de enlace el ipconfig no me da ninguno, el único valor que se mantiene es el de 169.254.16.169 (no me acuerdo de cual de los items era) pero por las dudas lo probé y tampoco me conecta al modem.
Qué hago?, no aflojen por favor.....

---

### Post by oktubrer on 2008-04-17
La placa de red dejala configurada como te dije antes:
ip 192.168.1.5
máscara 255.255.255.0
gateway 192.168.1.1

No hace falta que le cambies la configuración en ningún momento, dejandola así te tiene que funcionar con el modem routeado o con la conexión de windows normal.

Después seguí este tutorial
[http://www.speedy.com.ar/soporte.php?event=detalle&idcontenido=197&root=132](http://www.speedy.com.ar/soporte.php?event=detalle&idcontenido=197&root=132)

Desde donde dice "Configuración" y empieza a hablar del Telnet.
Es lo mismo que configurarlo por web, pasa que no encuentro ningún paso a paso ya configurado para Argentina.

faktorqm, con respecto a lo de forzar la ip, sería bueno, pero en el momento en que se establece la conexión, el dslam (equipo adsl del lado isp) te asigna una ip de su pool que tenga libre.  Si tu equipo no la acepta directamente no te conectas.
No es una negociación de dos vías como para que vos le puedas imponer la ip.
Además de que en el hipotético caso que pudieras, si justo esa ip la tiene asignada otro cristiano entrarías en conflicto como dice Hei Ku

---

### Post by faktorqm on 2008-04-17
[SIZE="5"]192.168.1.1 EN EL DNS[/SIZE]

muchachos!! me extraña! si hiciste todo bien la configuracion del video y no tenes internet es por eso!! Salu2!

---

### Post by oktubrer on 2008-04-17
Como se me pasó eso! ¿nos estabas poniendo a prueba? :lolflag:

---

### Post by losoollenos on 2008-04-17
LIIISSSTOOOO !!!!, no lo puedo creer. Muchachos millones de gracias !!!!, ya estaba obsesionándome, pero bue, no hay duro que no se ablande.
Cuando me relaje empezaré a investigar el ubuntu, pero no se preocupen (todavía), prometo no molestar hasta ......
Lo único que lamento es darle una parte del logro a speedy, en fin, les mando muchos saludos y abrazos para todos....

---

### Post by oktubrer on 2008-04-17
Buenísimo que haya salido al fin, aclará que fue lo que terminaste haciendo asi queda para alguna otra persona que tenga un problema similar, y  cambiá el thread a [SOLVED] asi se ve que está resuelto sin necesidad de entrar.
Un abrazo!

---

### Post by losoollenos on 2008-04-17
Vos decís que cambie el título?

---

### Post by losoollenos on 2008-04-17
A ver si es así oktubrer....
En realidad no les puedo decir exactamente que faltaba o qué es lo que lo hizo andar. Nada más seguí la guía de speedy y agarró viaje !!!

---

