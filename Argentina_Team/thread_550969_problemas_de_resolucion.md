---
title: "problemas de resolucion"
date: 2007-09-14
forum: Argentina Team
---

### Post by mordelones on 2007-09-14
Hola, bueno mi problema es el siguiente, no puedo cambiar la resolucion grafica ,la actual es 640x480 , y no me da opciones de otra resolucion,ni menor ni mayor.
la verdad es que yo no entiendo nada de programacion, recien hoy entendi lo que era una consola, pero me gusta linux, y no quiero rendirme y volver al xp, les pido por favor si me pueden alludar de alguna forma a cambiar la resolucion. gracias

---

### Post by FlyerDie on 2007-09-14
Hola, antes que nada bienvenido ;)

Te podemos a**Y**udar, pero antes necesitariamos un poco de informacion, ya que por lo visto es un problema de drivers...que placa de video tenes? que monitor es? es una maquina de escritorio o una notebook?
Aporta la mayor informacion posible del hardware y version de linux que estas utilizando, sino estamos medio a ciegas ;)


Saludos!
:guitar:

---

### Post by mordelones on 2007-09-14
Gracias me sentia perdido, bueno la verdad es que se me complica un poco tener mucha informacion de la placa, es onboard, yo en xp usaba el everest para sacar la info del sistema cpu etc, aqui no se muy bien como, pero actuare por memoria e intuicion:ahi va

monitor
mv520 compaq

ubuntu:7.04(feity)
memoria:629.6mib
Procesador:intel celeron cpu 2.00GHz

yo en xp como driver de la placa de video usaba  uno que me baje de la pagina de intel al quemarce el cd de pc chip que es este  Intel(R) 845G Chipset 

no se de que otra forma puedo darte info, pero vos decime y yo lo hago por que estoy perdido en esto y no quiero resignarme.

gracias.

---

### Post by faktorqm on 2007-09-14
hola, intel tiene drivers para linux. te lo bajas de aca:

[http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2102&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21](http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2102&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21)

ni idea que te baja, si te baja un tar.gz postea y te ayudamos a instalarlo.

Te recomiendo para empezar, que instales un instalador de cosas que se llama automatix. este programa no es tan bueno como parece, pero para vos que recien empezas en esto te va a servir mucho. despues de 1 año lo vas a terminar insultando y desinstalando, pero por ahora es la mejor opcion.

[http://www.getautomatix.com/](http://www.getautomatix.com/)

despues vas a installation y ahi te dice como hacer para ubuntu feisty 7.04.

bienvenido al club. :D salu2!

---

### Post by mordelones on 2007-09-14
si es un tar.gz y el automatic ya lo tengo , ahora espero tus intrucciones

graciasssss

---

### Post by mordelones on 2007-09-15
queridos amigos e intentado absolutamente todo pero me resulto imposibleee, no encontre ni en castellano, ni en ingles ni en portugues una forma facil de instalar un tar.gz simplemente no puedo, no se usar la consala quiza ahi este el problema pero en fin,lo dejo en sus manos, gracias
y por favor ayudaaaaa:confused:

---

### Post by FlyerDie on 2007-09-15
[http://www.intellinuxgraphics.org/download.html](http://www.intellinuxgraphics.org/download.html)

> Note: **If you have a 945** or older graphics controller, your distribution will already have the right drivers included. 

segun lo que dice ahi ya las distros actuales tienen los drivers, es mas...yo en mi notebook tengo una 945 tambien, y no hizo falta ponerle ningun driver, ya que Feisty la reconocio.
Para mi te esta mostrando la resolucion soportada por un monitor desconocido...calculo que tendras que cargar los parametros de tolerancia del monitor a mano.

---

### Post by mordelones on 2007-09-15
gracias, de todas formas es el 845g, que tan dificil es cambiar eso manualmente, o instalar el tar.gz?
gracias

---

### Post by Hei Ku on 2007-09-15
te recomendaria que pegues el contenido de tu archivo xorg.conf. Ese tiene la configuracion del X, el servidor de video.

Esta en /etc/X11/xorg.conf

Con eso quizas podemos ver si es un problema de drivers o de monitor.

---

