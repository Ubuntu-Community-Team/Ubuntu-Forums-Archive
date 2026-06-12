---
title: "Sonido bajo en Ubuntu?"
date: 2006-11-28
forum: Argentina Team
---

### Post by Nemesis Teufel on 2006-11-28
Nuevamente yo.

Es algo que no solo me pasa a mi. Es que en ubuntu tengo que el volumen como mas bajo.. le tengo que subir el volumen al equipo a todo lo que da para escuchar masomenos fuerte, cosa que con windows no, ya a 3/4 explota el equipo..

les pasa lo mismo? tengo el sonido en ALSA.

la placa de sonido es onboard(?)

---

### Post by TattooedFish on 2006-11-28
A mí me pasa lo mismo, mi placa también es on-board, aunque no representa un problema; tengo que poner los controles de sonido bien altos (master y PCM) pero como no distorsiona, lo dejo así. Se nota más en alguna que otra canción que ya viene con volumen medio bajo; aunque cuando le juego al Quake3 el sonido se escucha bien fuerte y claro. Será que el juego lo maneja de otra manera.

---

### Post by jpmorelli on 2006-11-28
lo mismo por aca, el sonido es bastante debil, habra alguna manera de aplicar un booster ? como por ejemplo el comando xgamma para el video?

tuxar!

---

### Post by felipelerena on 2006-11-30
tenes que ir a la consola y abrir > alsamixer, ahi subir el volumen de todo y listo... hay algunas cosas en segundo plano que el mixer de GNOME no muestra.

Saludos

---

### Post by Nemesis Teufel on 2006-11-30
listo! ahora patea que da calambres..
gracias felipe!!

---

### Post by felipelerena on 2006-11-30
de nada, no sabes lo que putee hasta darme cuenta de eso

---

### Post by jpmorelli on 2006-11-30
Buenisimo, si no me equivoco para guardar esas opciones en alsamixer como predeterminadas hay que correr:

sudo alsactl store

---

### Post by felipelerena on 2006-12-01
eh???

y eso ultimo?

las opciones se guardan solas...

---

### Post by jpmorelli on 2006-12-01
> **felipelerena said:**
> eh???

y eso ultimo?

las opciones se guardan solas...

La verdad ni idea, en mis épocas de slackware para que funcione el sonido tenia que hacer:

alsaconf (para detectar la placa)
alsamixer (para setear los vol)
alsactl store ( suponía que para dejar los seteos como predeterminados)

---

### Post by felipelerena on 2006-12-01
Epocas de slackware??? gracias Ubuntu por la magia, jajaja

---

### Post by jpmorelli on 2006-12-01
> **felipelerena said:**
> Epocas de slackware??? gracias Ubuntu por la magia, jajaja

Slackware ! Noooooo eso es re dificil me decían...
Te puedo asegurar que es mucho más fácil de lo que creen y si querés probar algún día la verdadera velocidad que puede tener un Linux, probalo, es in-cre-i-ble los pocos recursos que consume, a costa de chau apt-get y comunidades masivas que explican con lujo de detalle las cosas, etc. Es por eso que pasé por Mandriva, Fedora y hasta que llego Ubuntu 5.04 y desde ahi me enamoré.
Aguante Ubuntu !

---

### Post by Gideon26 on 2007-04-13
En cuanto a tu comentario de Slackware si estoy totalmente de acuerdo con vos es una excelente distro muy estable y eficiente y muy rapido eso es cierto quizas si requiere un poquito mas de conocimiento que ubuntu pero vale la pena probarla. yo tengo puesto el slackware 11.0 y te puedo asegurar que es excelente me lo recomendo un amigo mio (CCNA, CCNP,CCIE) son algunas de las certificaciones que tiene, digamos que conoce bastante del tema. Por lo demas ami Ubuntu me gusta mucho es mas lo estoy usando bastante, y para aquellos que quieren migrar de Windows, les recomiendo que elijan Ubuntu. quees muy bueno. (sin desmerecer las otras distros slackware, SuSE, Mandriva, etc.)



bueno saludos.

---

### Post by kalel on 2007-04-13
Si van a las preferencias del control de volumen (en la icon tray) pueden agregar todas las opciones que les muestra cuando ejecutan alsamixer en consola.

---

### Post by MeduZa on 2007-04-14
Hola, yo te cuento lo que me paso a mi  cuando me pase a ubuntu desde linux, venia de 0, instale todo y empieze con la gran lista de cosas para hacer andar o mejorar de modo que quedaran como a mi me gustan.
Cuando llegue al sonido, yo estaba usando el onboard porque pensaba que era mejor que mi SB live 5.1 ya que tenia (en windows) las mismas cosas pero era 7.1 (q no lo usaba porque mi equipo de audio es 5.1)
Cuando empece a probar con el alsa me di cuenta q el audio salia mal, mas bajo o por los canales incorrectos, me lei medio foro de ubuntu (en ingles aun no sabia de este :P )
para hacertela corta: con un comando de linux (no me acuerdo cual) lei las caracteristicas de hardware de la placa onboard (era la compatible con intel 850 o algo asi) saque de una caja la SB live 5.1 q no la usaba desde hacia tiempo y la puse, ahi me di cuenta la trementa kk que era la onboard, todo lo que tiene es mentira, necesita ser simulado por software, tenia solo 1 canal de audio a la vez para salida y 1 para entrada, la SB tenia muchisimos.
La cuestion es que ahora uso la SB y la otra la desactive en la bios, el sonido ahora es brutal! y sale por donde deberia

---

### Post by kalel on 2007-04-15
yo por suerte, 0 drama, todos los mothers que use con placas onboard 5.1, 7.1, el audio sale por donde debe, con ubuntu, con gentoo =)

---

