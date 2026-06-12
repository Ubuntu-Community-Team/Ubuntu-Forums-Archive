---
title: "Problema raro con placa de TV"
date: 2007-02-10
forum: Argentina Team
---

### Post by TattooedFish on 2007-02-10
Hola muchachos,

Quisiera hacerles una consulta, primero en esta sección antes de mandarla al nivel superior (en inglés) con la esperanza de encontrar a alguien que pueda aportar una solución que funcione.

El tema es el siguiente: tengo una placa sintonizadora de TV, un poco vieja, la compré en el año 2000, una PixelView PV-BT878P+ 2e2f.

La placa me funcionó (y sigue funcionado) siempre en Windows, en todas las versiones que usé desde el 98 hasta el XP.
Hace unos 3 o 4 meses que dejé el Win y me pasé a Ubuntu Linux.
Pero en Ubuntu 6.10 no me funca. *"No signal"* es básicamente y en pocas palabras, lo que siempre obtengo.
Lo raro de todo esto, es que cuando uso el Live CD de Knoppix, con el XawTV veo la televisión perfectamente, de una... y en Ubuntu 6.10 no puedo. Ni con XawTV, ni con TvTime ni nigún otro, porque no me capta la señal en la placa.

¿Hay alguna solución? ¿Alguien pasó por una experiencia parecida?

O de últma: ¿cuáles placas funcionan **seguro** para la Argentina en Edgy?

Desed ya muchas gracias por leer y por cualquier aporte que puedan hacer al respecto de este tema.

---

### Post by tzulberti on 2007-02-10
Preguntas boludas:
1) Configurastes bien el modulo del kernel para esa placa
2) Configurastes el TvTime para que lea PAL-NC, y use Cable

Si queres fijate aca:
[http://www.ubuntuforums.org/showthread.php?t=304444](http://www.ubuntuforums.org/showthread.php?t=304444)

---

### Post by TattooedFish on 2007-02-10
> **tzulberti said:**
> 1) Configurastes bien el modulo del kernel para esa placa
No toqué nada (no sé cómo hacerlo) pero estaba pensando que debe ser algo por ese lado. El Scantv tampoco detecta nada.

> **tzulberti said:**
> 2) Configurastes el TvTime para que lea PAL-NC, y use Cable
Sí, en el TvTime probé todas las opciones y no hubo caso.

> **tzulberti said:**
> Si queres fijate aca:
[http://www.ubuntuforums.org/showthread.php?t=304444](http://www.ubuntuforums.org/showthread.php?t=304444)
Ya mismo voy a leerme todo ese tema y probar las soluciones varias que hay.

Muchas gracias.

---

### Post by tzulberti on 2007-02-11
Para que las placas de video funcionen, uno tiene que configurar algun modulo del kernel. Este depende de que placa de video se este usando. No tengo ni idea sobre que modulo usa la tuya, por lo que te aconsejo que busques en internet

---

### Post by TattooedFish on 2007-02-17
Aunque ya antes de postear este tema había buscado por internet pero de forma más genérica, ahora hice una búsqueda más específica y encontré algo ([esto, click acá]("http://www.burghardt.pl/wiki/articles/pixelview_playtv_pro_pv-bt878p_9x")), con lo cual la hice funcionar a la placa... pero me detecta solamente canales del 60 para arriba (Multicanal) y sin sonido. :(  :confused: 

Por lo menos es un avance, algo se ve... habrá que seguir investigando.

---

### Post by tzulberti on 2007-02-17
Que programa estas usando para ver tele? Como lo configurastes?

Saludos,
TZ

---

### Post by TattooedFish on 2007-02-17
Gracias por seguir respondiendo.

Uso TvTime.

Primero hice *dpkg-reconfigure tvtime*. Norma Pal-nc, *frequency table*: cable.

Dentro del Tvtime: *enable signal detection, scan channels for signal*. Me da todos *"no signal"* excepto del 60 para arriba.
*Frequency table*: cable
Norma: Pal-nc
Sonido: mono (probé stereo pero es igual, no escucho nada).

El scantv sigue diciéndome *device has no tuner*.


Me debo estar perdiendo de algo... aclaro que soy relativamente nuevo en Linux, llevo 4 meses en esto, algunas cosas las voy aprendiendo pero en la mayoría todavía me quedo corto, es muy probable que se me esté pasando algún detalle básico.

---

### Post by tzulberti on 2007-02-18
Al tvtime, en la herramientas de configuracion, hace lo siguiente:
-> en la parte de Input Configuration elegi tv Mono
-> en la parte de channel management, hacele un scan channel

Saludos,
TZ

---

