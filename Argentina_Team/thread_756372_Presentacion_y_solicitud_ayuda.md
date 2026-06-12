---
title: "Presentacion y solicitud ayuda"
date: 2008-04-15
forum: Argentina Team
---

### Post by karolyna on 2008-04-15
Desde Buenos Aires, un saludo a la comunidad. En principio, disculpas porque tal vez este post esté incorrectamente ubicado. Esto de leer (a medias, muy poco) en inglés y español, me confunde bastante.
Hace una semana que estoy leyendo documentacion sobre Ubuntu, me decidí, descargué LiveCD y finalmente instale la ultima versión.
La PC es compartida, por lo que tamaño desastre hice en el disco rigido. Reinstalé Win, en algún lugar de la partición quedó la instalación de Ubuntu y yo quedé maravillada por lo poco que vi y con ganas de seguir...
Bien... las preguntas son muchas: 1) como desinstalo Ubuntu y recupero el espacio de la particion? 2) Estoy descargando Ubuntu Lite, para una Pentium MMX con 96 de Ram ¿será posible que funcione?

Gracias por su valiosa colaboración. Recién empiezo, espero algún día, poder tener yo la respuesta... y así seguir...

---

### Post by sartrejp on 2008-04-15
Hola, yo soy medio nuevo también, pero hice una macana parecida a la tuya. Yo lo solucioné con el partition magic o algún programa para gestionar particiones, 
Fijate en [www.softonic.com](www.softonic.com) que hay varios. 
En cuanto a tu otra parte de la pregunta tendrás que esperar alguien que conozca bien eso porque no tengo idea,  Por ahí podés ver en la página de ubuntu los requisitos para instalar, y te sacás la duda sobre la Ram.
Nos vemos.
Suerte

---

### Post by leo_rockway on 2008-04-16
Podes usar GParted desde el live cd para gestionar particiones, pero Grub te va a dar error si formateas la partición de Ubuntu (igual eso no es difícil de arreglar).

No conozco los requerimientos mínimos de Ubuntu Lite. La mejor forma de saber si te funciona es probándolo.

---

### Post by sajnox on 2008-04-16
Con 96mb de ram podes hacer andar xubuntu, si te gusta Ubuntu quedate dentro de lo desarrollado por Canonical, sino vas con Xubuntu ahi si mandate por otros caminos

---

### Post by leo_rockway on 2008-04-16
Xubuntu con 96 de ram? Pensé que era un poco poco... (igual no hablo desde la experiencia).
EDIT: desde el sitio de xubuntu [0] "Once installed, Xubuntu can run with 192 MB RAM, but it is strongly recommended to have at least 256 MB RAM."

Otra alternativa más parecida a Ubuntu Lite y con sabor Ubuntu (aunque no Canonical) sería Fluxbuntu que usa Fluxbox en lugar de Openbox. Fluxbox lo probé y me gustó mucho, Openbox nunca lo probé, aunque me imagino que debe ser parecido.

[0]: [http://www.xubuntu.org/get](http://www.xubuntu.org/get)

---

### Post by sajnox on 2008-04-16
Gracias Leo por la aclaracion, estaba MUY convencido que xubuntu corria con 64mb de ram (lo que corre con 64mb es la instalacion con el alternate CD), No se para que quiero instalar con 64mb si igual necesito 192 para correr.

Coincido con la recomendacion de ir para el lado de Fluxubuntu

---

### Post by karolyna on 2008-04-24
Muchas gracias por las orientaciones. A esta altura, ya recuperé las particiones DOS. Con la máquina más pequeña, todavía no experimenté. Ya les avisaré cómo fue la cosa...

¡gracias!

---

### Post by clasificado on 2008-04-24
La nueva versión de ubuntu (esa que sale hoy) viene con WUBI. 

Osea que podés instalar ubuntu desde windows y no te toca una sola partición.

Esta bueno para cuando querés experimentar.

Me olvidaba. Por las versiones de Linux para menos de 128 mb de ram, me gustaria advertirte: La versión que hizo famoso a Ubuntu es la principal, Ubuntu con gnome. El resto de las versiones si bien pueden compartir el nombre, son considerablemente diferentes y hasta pueden ser mas complicadas. 

Esa fue mi experiencia con Xubuntu: al ser la tercera distribución de cannonical, tiene puesto encima muuucha menos atención que al ubuntu original.

Lo que tiene de bueno, es que como es siempre Linux, la potencia es exactamente la misma. Pasa que a medida que vayas cambiando de distribución hay cosas que te vas a ir encontrando que se hacen por consola (al modo linux) y no con los paquetes gráficos que tanto se esmeró cannonical en agregarle al ubuntu, y que lo hacen ser lo que és.

Si es por aprovechar la pc al máximo, la linea ubuntu no es la que mas rinde. podrias partir desde Debian, o correrte un poco y salirte hacia DSL. Este último me dió muy buenos resultados cuando dejé de esperar un ubuntu en una pc de 128 mb de ram.

clasificado

---

