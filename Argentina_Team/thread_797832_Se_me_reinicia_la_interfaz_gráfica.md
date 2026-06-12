---
title: "Se me reinicia la interfaz gráfica"
date: 2008-05-17
forum: Argentina Team
---

### Post by elgatovolador on 2008-05-17
Hola Argentina Team.. 

Tengo alguna experiencia con Ubuntu, vengo usandolo desde la 5.04 y lo que me está pasando con Hardy no lo habia visto nunca..

Resulta que instale Hardy desde cero, en una DELL Inspiron 1721, a destacar la maldita tarjeta ATI Radeon X1270 (que creo causante del problema). 

El problema: La interfaz gráfica (Xorg) se reinicia de forma aleatoria, perdiendo todo lo que estaba haciendo. Me devuelve a la pantalla de login.

Pistas: Creo que puede ser algo de la pila, es lo ultimo que veo antes q se cierre sola las X. Dice algo como /rc.d/local no se que cosa, battery script.. Pero no se que Log debo revisar para ver bien el error.. 

Otra cosa que pudiera estar fallando es el driver de ATI, pero lo usaba en Gutsy e iba al ****, dandome incluso aceleracion grafica.. tenia hasta compiz funcionando..

Llevo 3 dias pidiendo ayuda en IRC (#ubuntu) y nada que me contestan.. :confused:

Agradezco enormemente la ayuda que me puedan prestar, de lo contrario, tendre que volver a Gutsy o a Windows :mad:

---

### Post by WanderingKnight on 2008-05-17
>  Pistas: Creo que puede ser algo de la pila, es lo ultimo que veo antes q se cierre sola las X. Dice algo como /rc.d/local no se que cosa, battery script.. Pero no se que Log debo revisar para ver bien el error.. 

Vimos algo parecido en la Flisol... aunque la verdad no sabría decirte a qué conclusión se llegó. Si alguno de los muchachos que ayudó a la persona que tenía este mismo problema en la máquina recuerda cómo se solucionó (si es que se solucionó), esperemos que posteen acá.

---

### Post by sajnox on 2008-05-17
> **elgatovolador said:**
> 

Agradezco enormemente la ayuda que me puedan prestar, de lo contrario, tendre que volver a Gutsy o a Windows :mad:

Yo estoy usando Hardy pero mantuve el kernel de Gutsy, en mi caso no reconoce la grabadora dvd.

Y de ultima mantener gutsy no es opcion comparable a volver a windows...cheeeeee

---

### Post by elgatovolador on 2008-05-17
Cierto, jejeje.. pero igual, si quisiera detectar el error.. no se a donde ir.. revise el log del kernel, de las xorg, etc.. y nada..

Por cierto, estoy usando Hardy de 64 bits, sera que pruebo la version de 32?

---

### Post by elgatovolador on 2008-05-19
Agregando algo por si alguien se apiada de mi..

Hoy al reiniciarse la interfaz grafica, pude copiar el mensaje en pantalla

Starting anac(h)ronistic cron anacron
Starting deferred execution scheduler atd
Starting periodic command scheduler crond
Checking battery state
Running local boot scripts (/etc/rc.local)

Y aqui se queda muerto..

---

### Post by Mister X on 2008-05-19
> **elgatovolador said:**
> Agregando algo por si alguien se apiada de mi..

Hoy al reiniciarse la interfaz grafica, pude copiar el mensaje en pantalla

Starting anac(h)ronistic cron anacron
Starting deferred execution scheduler atd
Starting periodic command scheduler crond
Checking battery state
Running local boot scripts (/etc/rc.local)

Y aqui se queda muerto..

eso no es un mensaje de error, eso te muestra por la terminal tty1 al arrancar (nunca lo ves porque tenes el splash con la barra de progreso), al morir la sesion grafica ves eso (si haces ctrl+alt+F1 estando en las X tambien verias lo mismo)

los log del Xorg estan en /var/log/Xorg.0.log

otra cosa, vos decis que se queda "muerto", el teclado no responde? que pasa si apretas ctrl+alt+F2  ???

---

### Post by elgatovolador on 2008-05-20
Mister X: Gracias por la ayuda y por la información. Nada, cuando me sale ese mensaje de error, antes regresaba solo a la pantalla de login (GDM si no estoy errado). Ahora se queda ahi, colgado. Le doy CNTRL + C (como para matar lo q este haciendo) y ahi si sigue y termina de reiniciar el equipo.. No he probado darle ctrl + alt + F2.

Seran problemas del kernel? :S 

Lei por ahi q hay gente q instala Hardy y luego regresa al kernel anterior.. por que?

---

