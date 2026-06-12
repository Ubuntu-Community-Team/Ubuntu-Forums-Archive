---
title: "placa de red nvidia/gigabyte para compartir internet con XP"
date: 2007-10-17
forum: Argentina Team
---

### Post by steve_ignorant on 2007-10-17
bueno otra vez yo, parece que estoy como molestando un poco con esto. pero es que las cosas me urgen en cierta forma, necesito si me pueden ayudar  a como configurar para que yo desde mi maquina o linux pueda compartir internet con otra maquina que tiene XP(en una oficina, que dice "antivirus desactualizado"y me preguntan imaginense si les pongo linux) 

pero bueno el tema es el siguiente, tengo una mother A7N8-E deluxe, con dual lan.  tengo la red conectada, el ubuntu la reconoce(a la placa y a la red que esta conectada). pero no le pasa internet a la otra pc. tambien el XP reconoce cuando esta pc esta prendida(reconoce que esta conectada la red, pero no recibe internet)

si me pueden dar un how to o una ayuda de como hacer se los agradezco.

---

### Post by el_itur on 2007-10-17
Respuesta corta:
[Google es tu amigo]("http://www.google.com.ar/search?q=compartir+conexi%C3%B3n+a+internet+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:es-AR:official&client=firefox-a")

Respuesta larga:
Usá iptbles. es un firewall que viene con ubuntu y que te permite hacer ruteo.
En este hilo describen bien como hacer
[http://www.ubuntu-es.org/index.php?q=node/10513](http://www.ubuntu-es.org/index.php?q=node/10513)

Tengo tu mismo hardware y anda de perlas. De cualquier manera no es aconsejable usar un desktop como router. Mejor comprate uno, son más baratos que tu compu en caso de que se queme o algo.

Salute

---

### Post by steve_ignorant on 2007-10-17
tengo modem usb si lo decis por el ruteo

A la maquina la tengo hace un año andando con el puente de red que fabrica el xp, igual mente es una sola maquina(es una red de 2 pc's. la que provee internet a la otra).  

vos decis que existe algun riesgo de que se queme o algo por el estilo la mother o algo?, hasta el momento yo sabia que se podia quemar el modem pero cuando era proxy, si me podes responder esto la verdad que me sorprenderia bastante porq solo me dijeron que podia llegar a pasar con el proxy.:confused:

te dejo mas info de mi pc. 

AMD athlon XP(barthon-32bits) 2600+/ 512Mb RAM/ GeForce TI 4200(DDR samsung 128 ) fabricada por "INNO3D/Tornado"/ MT A7N8-E deluxe/ SATA samsung 120Gb/Modem USB speedTouch 330.


bueno solo te puedo agradecer, todavia no lo instale en el linux, cuando lo haga te digo si funciono o no. gracias de ante mano. 

agur!

---

### Post by faktorqm on 2007-10-18
hola, hay un par de cosas que no entendi, pero bueno. tenes proxy o compartis internet con el xp "libre"? por que no es lo mismo.

si se te kema algo o cae un rayo en la linea de telefono, se te va a kemar todo igual si tenes windows, linux, unix, qnx, solaris, mac os, o dos. (chiste ;))

para compartir la conexion tambien podes usar una interfaz grafica que hay para iptables, (si no te gusta la consola) que se llama firestarter. lo instalas con "sudo apt-get install firestarter" (sin comillas) 

creo que 150000 tutoriales que explican como compartir internet con firestarter, asi que busca cualquiera y contanos como te fue. salu2!!!!

---

### Post by el_itur on 2007-10-18
> tengo modem usb si lo decis por el ruteo

A la maquina la tengo hace un año andando con el puente de red que fabrica el xp, igual mente es una sola maquina(es una red de 2 pc's. la que provee internet a la otra).  

Bien. Entendí mal la topología de la red, Lo que yo te sugerí sirve si tenés el modem conectado por red (clásico cablemdem) en una de las placas de tu linux y compartís a un switch o a otra compu a travez de la otra placa 

> vos decis que existe algun riesgo de que se queme o algo por el estilo la mother o algo?, hasta el momento yo sabia que se podia quemar el modem pero cuando era proxy, si me podes responder esto la verdad que me sorprenderia bastante porq solo me dijeron que podia llegar a pasar con el proxy.:confused:


Cuando tenés una máquina como casi siempre querés que esté activa para que elresto de tu red tenga internet. Mientras más tiempo tenés el equipo prendido más lo exponés a bajones de tensión, apagones y ese tipo de cosas. Claramente te va a molestar menos exponer un router (~$300) que una compu ($2500+). Simplemente por eso era el comentario.

@faktorqm: firestarter es un front end para iptables. así que básicamente le estamos diciendo lo mismo.

Nunca compartí una conexión a internet que utilize un modem usb (básicamente porque los modem usb apestan.) Así que no te aseguro que lo que te haya dicho hasta el momento te sirva, pero bueno, no está de más probar.

Augur :)

---

### Post by steve_ignorant on 2007-10-18
> **faktorqm said:**
> hola, hay un par de cosas que no entendi, pero bueno. tenes proxy o compartis internet con el xp "libre"? por que no es lo mismo.

decime que es lo que no entendiste y te lo explico.
por la conexion si, tengo una conexion que  no es por proy, la pc que recibe internet, se conecta a internet atraves de la red(supongo que tendra  IP fija la pc que recibe conexion x red)  

> si se te kema algo o cae un rayo en la linea de telefono, se te va a kemar todo igual si tenes windows, linux, unix, qnx, solaris, mac os, o dos. (chiste ;))

no me hables de eso que ya me paso con un modem dial up, cuando tenia la pc en garantia y me tiraron todas las cajas a labasura, lo que hice fue reprochar a quien lo hizo y consegui un modem intel 56K (antes que el pirulo que venia por defecto), justo a 6 meses de que mi viejo se habia ido a vivir a españa y la unica forma de hablar era por msn

> para compartir la conexion tambien podes usar una interfaz grafica que hay para iptables, (si no te gusta la consola) que se llama firestarter. lo instalas con "sudo apt-get install firestarter" (sin comillas) 


interesante entonces voy a ver si lo puedo hacer con eso, si es grafico mejor porq asi me resulta mas facil y mas familiar cuando configuraba la red x güindous

> 
creo que 150000 tutoriales que explican como compartir internet con firestarter, asi que busca cualquiera y contanos como te fue. salu2!!!!

bue.... gracias, me voy a fijar a ver que pasa...

---

