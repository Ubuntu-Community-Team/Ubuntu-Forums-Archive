---
title: "[SOLVED] hp530 y video"
date: 2007-11-19
forum: Argentina Team
---

### Post by ma_chro on 2007-11-19
Tengo una hp530, funcionaba bárbaro hasta que queriendo modificar el setting de pantalla para poder ver mejor todo en un cañon, ahora no puedo ver nada.
¿Puede alguien indicarme como volver a reconfigurar desde "recovery mode"? Tengo Gutsy. Muchas Gracias
__________________

---

### Post by Hei Ku on 2007-11-20
probaste a hacer:

sudo dpkg-reconfigure xserver-xorg

---

### Post by ma_chro on 2007-11-21
Gracias Hei Ku!
Te agradezco mucho tu ayuda!
Ahora, te hago una consulta:
Viste que en el setting de pantalla podés setear otra, yo tomo como que es la que colocás en la salida para monitor (tengo notebook), porque en la máquina tengo seteada la definición en 1280x800 y el cañón aceptaba hasta 800x600
¿Este segundo seteo es para estos casos o estoy entendiendo mal?
En cuyo caso cambio el seteo de la pantalla principal y listo ¿no?

Así y todo muchas gracias Hei ku.

---

### Post by Hei Ku on 2007-11-21
Por lo que entiendo, es para cuando usas dual-head, o sea dos monitores al mismo tiempo, como pantallas independientes, con xinerama o algo asi.

En tu caso, yo cambiaria la resolucion de la pantalla principal, porque la salida es una sola. (la placa de video manda la misma informacion al LCD y al proyector, se entiende?)

---

### Post by ma_chro on 2007-12-05
Muchas gracias, otra vez!!
La realidad que es muy loable que gente que sabe tanto como ustedes ayuden a otros de buena onda.
Saludos

---

### Post by pablo atheist on 2007-12-07
yo tengo una hp 530 y tengo instalado el ubuntu 7.04 , mi pregunta es:
es posible que me ande compiz fusion ya que la tarjeta gráfica no es ni ati ni nvidia , y el tutorial que vi para instalar compiz estaba orientado para esas tajetas...

---

### Post by facundocorradini on 2007-12-07
Hola Pablo

La hp530 tiene una placa intel... Eso no es problema. De hecho, las intel son las que más facil corren, ya que el driver es libre y viene con ubuntu... En teoría, debería funcionar barbaro simplemente activandolo desde preferencias-->efectos de escritorio...

---

### Post by pablo atheist on 2007-12-07
si eso de los efectos de escritorio me anda de novela, lo que no tenia ni idea que eso era compiz. Se ve que debe ser una versión vieja (la que viene instalda con ubuntu 7.04 )por que los efectos que tienen no le llegan ni a los talones de lo que eh visto. 
Para pasar a la nueva versión tengo que bajar ciertos paquetes instalarlos y ya queda listo???
saludos

---

