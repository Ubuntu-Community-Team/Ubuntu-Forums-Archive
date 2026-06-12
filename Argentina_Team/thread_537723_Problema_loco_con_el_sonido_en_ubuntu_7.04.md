---
title: "Problema loco con el sonido en ubuntu 7.04"
date: 2007-08-29
forum: Argentina Team
---

### Post by niko_3100 on 2007-08-29
Bueno gente le comento soy nuevo en el foro y tambien soy un usuario nuevo de ubuntu con dos meses de antiguedad jeje!!! Les coment mi problema me compre una compaq v3415 con placa de video nvidia y de sonido me reconoce dos, una HD nvidia (alsa) y la otra conexant. Lo raro es esto tengo dos SO uno el win xp y el otro ubuntu 7.04 entonces si enciendo la maquina de una y levanto el ubuntu me sale sonido por los parlantes pero si primero levanto el xp y luego reinicio o apago y vuelvo a levantar con ubuntu no me sale sonido por los parlantes. Pongo no me sale sonido por los parlantes porque sin embargo si me reconoce las placas de sonido y si me deja reproducir mp3s y videos todo joya pero como si estuviera en MUTE el volumen aunque esta al mango jeje!! Tambien les comento que buscando codecs y mejores programas de video y audio borre el Totem, el mplayer y el Rythmbox luego y luego volvi a instalarlos pensando que asi se solucionaria pero no, mi idea es volver a instalar todo de cero si no hay otra solucion posible pero por ahi es otro el problema y no tiene nada que ver instalar de cero o por ahi lo mejor seria instalando de cero. Como soy nuevo no se bien para que lado encarar por eso recurri a ustedes que la tienen mas clara. Muchas gracias.

---

### Post by sajnox on 2007-08-29
Hola,

Me parece que tu problema es comun y de facil solucion

1) En una consola escribi lo siguiente

$ asoundconf list

Te devuelve el nombre de la placa de audio que detecta, en este caso son dos.

2) Para activar la placa correcta como default

$ sudo asoundconf set-default-card CARD

CARD = Al nombre de la placa que queres que funcione y lo escribis TAL CUAL TE LO DEVUELVE EL asoundconf list

3) Fijate que los controles de sonido apunten en su configuracion a placa que habilitaste

Probalo y nos contas

---

### Post by niko_3100 on 2007-08-29
OKa pruebo eso y comento a ver como me fue, me tiene desconcertado porque no enteindo porque si primero levanto el xp despues en ubuntu no tengo sonido pero cuando levanto ubuntu de una si tengo sonido y va de 10.

---

### Post by niko_3100 on 2007-08-30
Bueno hice lo uqe me de dijiste y me tire solo una placa de sonido llamada para el sistema Nvidia la configure con el segundo comando pero me parece que eso no es, porque como dije si tengo sonido sin problemas el problema es cuand primero arranco en windows xp y despues reinicio la notebok y levanto el ubuntu ahi es cuando no me reconoce el sonido. Es como si fuera un bug de ubuntu o algo que esta haciendo el xp,  no vale decir SOLUCION: borra el windows xp jeje!!! porque lamentablemente todavia soy bastante dependiente del xp :(

---

### Post by leo_rockway on 2007-08-30
lo q te reconoce como placa de sonido y dice conexant tiene q ser un voice modem.

algo que quizas pueda ayudar es recompilar alsa siguiendo estos pasos [http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0](http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0) (estan en ingles, si necesitas ayuda chifla). no garantizo que funcione, pero tener la ultima version de alsa tp viene mal.

lo raro es q el hecho de bootear con xp influya en el sonido de ubuntu. es muy raro eso.

---

### Post by niko_3100 on 2007-08-30
Claro eso es lo que me tiene desorientado, mas alla que recien empiezo con ubuntu y esas cosas me parece raro poruqe pasas solo cuando booteo el xp primero. Por ahi el ubuntu se instalo mal  o me falto hacer algo pero por otro lado tengo mis mp3s, mis peliculas mis videos todo configurado con sonido y todo joya.

---

### Post by leo_rockway on 2007-08-30
sere curioso? como recuperas el sonido despues? rebooteas lignux?

---

### Post by niko_3100 on 2007-08-30
No, ojala mira probe reiniciando y elegir yo ubuntu y nada, despues probe reiniciando y que el grub elija solo ubuntu, despues probe apagando la maquina y eligiendo yo ubuntu y apagando y que el grub eliga solo. No funciono con esto entonces levante otra ves el xp y reinicie hice las dos eligiendo yo y que el grub elija y lo mismo apagando y nada, estando en linux sin sonido instale alsa-base alsa-source y un par de cosas mas de alsa y tamopco nada :( Lo unico que funciona es apagar la notebook venir al rato (no se bien cuanto tiempo) y levantar directo al ubuntu porque si primero levanto el xp fui.

---

### Post by Mister X on 2007-08-30
Cuando reinicias por soft, los dispositivos no pierden alimentacion, por lo tanto no se reinician 'de cero', evidentemente la placa de sonido queda en algun estado que hace que Ubuntu no la pueda reconocer

---

### Post by niko_3100 on 2007-08-30
Entonces vos decis de apagar, desenchufar de la corriente y volver a prender y bootear desde linux? Es una buena posibilidad pero por que??? buaaa!!!

---

### Post by Mister X on 2007-08-30
No digo que sea la solucion, seguramente es posible configurar desde Ubuntu para no necesitar apagar del todo la PC, pero lamentablemante yo no se como ;)

---

