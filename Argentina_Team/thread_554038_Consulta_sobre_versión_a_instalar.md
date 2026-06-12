---
title: "Consulta sobre versión a instalar"
date: 2007-09-18
forum: Argentina Team
---

### Post by vk-cdg on 2007-09-18
Por fin llegó mi disco de 160 Gb el cual está destinado a la instalación fresquita de ubuntu. 

La configuración de mi equipo es la siguiente:

Mother Asus M2N-E
1 GB RAM
AMD AM2 3800
Video Geforce 7300 GT
HDD 250 GB - Win XP
HDD 160 GB - Ubuntu 7.?

La consulta es ¿de acuerdo a esta configuración, que versión de Ubuntu me recomiendan instalar 7.04 x86 o 64 Bist? ¿o si me aconsejan esperar unos días mas e instalar el 7.10 y en ese caso lo mismo x86 o 64bits?

El uso que le voy a dar es simplemente hogareño, internet, mail, OpenOffice y diseño web, para lo cual uso en NVU principalmente y algunas cositas puntuales que corren bajo win las virtualizaré o usaré el XP instalado en el otro disco (que actualmente es la instalación que usa mi mujer)

Gracias de antemano.

---

### Post by Mauro22 on 2007-09-18
Hola!!


Desde mi punto de vista metele la 7.04 x86 por mis razones:

* Al ser 7.04 ya sabes que esta recontra estudiada, sabes lo que funciona y lo que no. Que hardware anda de 10 y cual de 1.
* Al ser x86, tenes muchisima mas compatibilidad con software/drivers y menos dolor de cabeza


* La 7.10 va a estar buena, seguro, pero yo la instalaria -o actualizaria- cuando haya pasado un tiempo. Yo tenia pensado en instalarla para fin de año.

Espero que te ayude a elegir!

---

### Post by por100pre1 on 2007-09-18
El socket AM2 es para un procesador de AMD 64 bit, El poder de esos procesadores se aprovecha al maximo con la versión 64 bit. Pueden haber dificultades con el plugin de Flash. La verison x86 no enfrenta esa situación. La tarjeta Video Geforce 7300 GT puede requerir configuración. Pasate por aquí de requerir ayuda. Los mucahchos aqui te pueden dar una mano.

---

### Post by Montsegur87 on 2007-09-18
64 bits es para quilombo.

---

### Post by Mister X on 2007-09-18
Yo te aconsejaria la amd64, yo la uso y funciona 10 puntos. El unico detalle es que hay que instalar un navegador de 32bits para poder instalar el plugin de flash, pero esto no trae ninguna dificultad.

---

### Post by tzulberti on 2007-09-18
Una cosa para que tengas en cuenta:
-> Yo tengo el mother M2N-E SLI, y la placa de sonido me funciona, pero solo puedo escuchar una cosa a la vez. Es decir, si escucho el amarok, el gaim no suena cuando alguien me manda un mensaje. Leyendo, encontre que esto se va a solucionar para Gutsy. Por lo tanto, te recomiendo que te bajes un livecd de Feisty para ver si te la detecta bien.


Sobre si usar 64 o 32, depende de que uses. Si usas flash, skype, codecs de videos, acrobar reader, etc... te recomiendo 32 bits porque instalar estos programas no es facil. Si no usas esos programas, entonces te recomiendo 64.

---

### Post by facundocorradini on 2007-09-18
Mi consejo es que esperes la release de Gutsy, 

Yo he probado las alphas y la verdad es que tiene muchas mejoras con respecto a Feisty.

En cuanto a 32 o 64, depende de cuánto te gusten los desafíos... si querés ahorrarte dolores de cabeza, elegí 32 bits.

--------------------------------------------------------------

> * La 7.10 va a estar buena, seguro, pero yo la instalaria -o actualizaria- cuando haya pasado un tiempo. Yo tenia pensado en instalarla para fin de año.

Parece respuesta a una consulta sobre windows... La verdad es que cuando sale una versión nueva de Ubuntu, esta está muy bien testeada (somos miles y miles de usuarios que probamos las alphas y betas) y es absolutamente seguro instalarla.

saludos

---

### Post by Mauro22 on 2007-09-18
> **facundocorradini said:**
> 
Quote:
* La 7.10 va a estar buena, seguro, pero yo la instalaria -o actualizaria- cuando haya pasado un tiempo. Yo tenia pensado en instalarla para fin de año.



Parece respuesta a una consulta sobre windows... La verdad es que cuando sale una versión nueva de Ubuntu, esta está muy bien testeada (somos miles y miles de usuarios que probamos las alphas y betas) y es absolutamente seguro instalarla.

saludos

La verdad que lo que dije antes, no parece a una respuesta a una de consulta de windows, sino que es. La verdad es que, esta es la primera vez que me mantuve en una Distro que va a lanzar una version mas nueva. (siempre estuve probando distintas). 
No pense que el testeo previo fuera tan exhaustivo.

:lolflag:

---

### Post by vk-cdg on 2007-09-18
> **por100pre1 said:**
> La tarjeta Video Geforce 7300 GT puede requerir configuración. 

La placa con instalarle los controladores propietarios sale andando en 1280x960 sin problemas.
De hecho ahora tengo un Fiesty instalado, pero en un disco prestado hasta que llegara el de 160. 
Ahora llegó, pero como estoy con parciales y TP en la facu, va a quedar para mas adelante, por eso no tenía problemas en esperar hasta la salida de Gusty

---

### Post by faktorqm on 2007-09-19
para mi, ubuntu 7.04 32 bits, /home en otra particion, cuando se te cante, cambias el ubuntu y no tenes ningun tipo de lios.

> **tzulberti said:**
> Una cosa para que tengas en cuenta:
-> Yo tengo el mother M2N-E SLI, y la placa de sonido me funciona, pero solo puedo escuchar una cosa a la vez. Es decir, si escucho el amarok, el gaim no suena cuando alguien me manda un mensaje. Leyendo, encontre que esto se va a solucionar para Gutsy. Por lo tanto, te recomiendo que te bajes un livecd de Feisty para ver si te la detecta bien.


perdon por desvirtuar el post: esa falla a mi tambien me pasa por ejemplo cuando abro dos reproductores de musica al mismo tiempo, lo poco que pude averiguar es que es por que el dispositivo esta siendo utilizado, tonces si dos programas usan alsa, no hay problema por que el alsamixer se encarga justamente de mezclar, pero si uno usa oss y el otro alsa, ahi viene el conflicto. vos investigaste algo? salu2!

---

### Post by tzulberti on 2007-09-19
> **faktorqm said:**
> 
perdon por desvirtuar el post: esa falla a mi tambien me pasa por ejemplo cuando abro dos reproductores de musica al mismo tiempo, lo poco que pude averiguar es que es por que el dispositivo esta siendo utilizado, tonces si dos programas usan alsa, no hay problema por que el alsamixer se encarga justamente de mezclar, pero si uno usa oss y el otro alsa, ahi viene el conflicto. vos investigaste algo? salu2!

La verdad es que no averigue nada, pero cuando llegue a mi casa me fijo que cliente esta usando el pidgin y cual esta usando el amarok. Lo que si note es que si tengo el totem abierto (viendo o no un video), el amarok se queda tildado porque me dice que el algun dispositivo esta siendo usado... 

Gracias,
TZ

---

