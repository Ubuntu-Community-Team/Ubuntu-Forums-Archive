---
title: "Pantalla Blanca en Compiz Fusion con tarjeta onboard VIA"
date: 2007-08-21
forum: Argentina Team
---

### Post by lean1984 on 2007-08-21
Hola, soy nuevo por aca porque generalmente posteaba en ubuntu-es hasta que me di cuenta que hay un ubuntu-ar jaja. Repito un post que puse allá porque es un problema con una mother que se consigué acá y quizas a alguien le paso.

Estube evangelizando a mis amigos y dos de ellos instalaron Ubuntu Feisty. El problema está en que una de las máquinas al querer correr compiz fusion muestra una pantalla blanca y no queda otra que reiniciar. Al reiniciar vuelve a metacity y todo anda Ok. Me estube matando en Google por encontrar alguna respuesta pero el problema está en que la tarjeta onboard es de una marca muy poco popular. La mother es una Asus P5VD2-MX y la tarjeta onboard parece ser VIA P4M890. No se si será un problema de drivers, en ese caso no tengo fe de poder encontrarlos . Yo por mi parte corro sin problemas compiz fusion en una tarjeta Intel onboard, pero por lo que vi Intel tiene mucho mas soporte que VIA, de hecho no encontre ninguna referencia a esta marca.

Si alguien conoce una solución por favor que me de una mano. Otra idea que tengo es probar instalar Beryl, pero si el problema son los drivers de la tarjeta esto no va a servir de nada. Igual lo probaré en los proximos dias.

Saludos y espero que alguien pueda ayudarme con esto.

---

### Post by faktorqm on 2007-08-21
Hola!! Yo en el laburo tengo la misma mother con la misma placa de video. Obvio que no anda, ni compiz, ni compiz-fusion, MENOS beryl, ni nada de nada. Es mas, tengo la certeza de que metacity va lento tb........ :(
Te cuento todo lo que investigue al respecto: hay drivers, hay tutoriales de como instalarlos (miles), pero no hay caso che, no lo puedo hacer andar :(:(:(
ahora instale un nuevo ubuntu de 32 7.04 e iba a empezar esta semana a tratar de probar por enesima vez. asi que obvio hago un tutorial, pero si me sale. Aparte es como que hay drivers para 2d y 3d y no entiendo nada.
Voy a tratar de poner al menos los 2d. despues veo el resto. deseame suerte! :D

---

### Post by santiagoward2000 on 2007-08-24
Hola lean1984. No sé si esto te sirva, pero a mí me pasaba lo mismo cuando intentaba instalar beryl desde los repositorios oficiales de beryl o con los que ya vienen en feisty. Pero cuando lo instalé desde el repositorio de Treviño me anduvo bárbaro.
Igual, yo tengo una placa ATI Radeon Xpress 200m, así que no sé si es el mismo problema.

---

### Post by lean1984 on 2007-08-25
Hola, buenisimo, me estaba siendo casi imposible encontrar a alguien con esta placa. Tampoco encuentro los drivers, si me podes tirar algun link, estube googleando pero no tuve suerte. Yo estoy seguro de que es un tema de drivers porque cuando haces glxinfo tambien te tira un error:
$ glxinfo
name of display: :0.0
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  16
  Current serial number in output stream:  17

bueno te deseo suerte!

---

### Post by faktorqm on 2007-08-25
bueno, me fue menos mal de lo que pensaba.
Te cuento, segui la guia  de ubuntu, la de compilar el drm directamente, me dio todo ok (lo cual es un milagro) pero..... cuando pongo el driver via en el xorg.conf, tira un error de que no hay screen. o sea, mal.
Despues encontre un tuto de bajar un driver, compilarlo, blabla, hice todo ok (tambien milagrosamente) y cuando voy a arrancar, SIGSEGV. (por si no sabes que es SIGSEGV, es una violacion de segmento de memoria, o sea, estoy haciendo una referencia a un bloque de memoria que no esta asignado, por lo tanto no mne deja acceder, y te bloquea)
Lo ultimo que probe, fue el famosisimo xserver-xorg-via-unichrome y cuando lo puse me dice "este dispositivo todavia no esta soportado". asi que todo mal, por que deci aque lo bancaba. despues lei en muchos foros que se kejaban por eso y que en realidad no funcionaba.
Entonces agarre y probe la cuarta cosa, un driver que anda en debian para esa placa, y anda bien. pero tengo un tema, cuando intente compilarlo, me tira error el gcc, hay errores en unas bibliotecas de tipos. Intente corregirlas a manopla, pero sinceramente habia sido mucho para mi en un solo dia, asi que me fui a la casa de mi novia a despejarme. :guitar:
Como hasta el lunes no welvo al trabajo, hasta el lunes no habra novedades. Salu2!!

---

