---
title: "problemas con ENLTV en argentina"
date: 2007-07-14
forum: Argentina Team
---

### Post by Bandidox on 2007-07-14
Hola gente, este es mi primer post, asi que comoenzemos con un saludo para todos y les explico mi problema.

Migre totalmente a Ubuntu 7.0.4 hace mas de una semana y he logrado hacer funcionar todo, menos la placa capturadora de tv que tengo, es una ENLTV con chip saa7130, que ya logre que reconosca e instale el tvtime y hasta ahi todo bien, pero no logro hacer que se vean todos los canales, paseando por los foros, pase por el de españa, y ahi todo el mundo la hizo andar, pero despues en foros de tucuman, me entere que tenemos en argentina una norma unica "pal-nc", por lo tanto estoy sin poder ver la television o poder capturar video.

Desde ya se agredece toda la ayuda que puedan brindarme

---

### Post by Mauro22 on 2007-07-15
```
una pregunta:

Tienes la ENTLV-FM??


Porque en la pagina de encore dice que no es compatible con linux, y si es esa, como hiciste para hacerla andar.??


Salu2!
```


Editado:

mirate esto: [http://mfireweb.wordpress.com/2007/02/12/tutorial-para-placa-tv-encore-tv-fm-enltv-fm/](http://mfireweb.wordpress.com/2007/02/12/tutorial-para-placa-tv-encore-tv-fm-enltv-fm/)

por ahi te funciona!

Salu2

---

### Post by Bandidox on 2007-07-15
No Mauro 22 tengo la ENLTV sola sin radio, pero hay un monton de tutorariales para tu placa. 

fijate este si te sirve 

Saludos. 

[/...]("http://mfireweb.wordpress.com/2007/02/12/tutorial-para-placa-tv-encore-tv-fm-enltv-fm/")

---

### Post by etitor on 2007-10-07
> **Bandidox said:**
> No Mauro 22 tengo la ENLTV sola sin radio, pero hay un monton de tutorariales para tu placa. 

fijate este si te sirve 

Saludos. 

[/...]("http://mfireweb.wordpress.com/2007/02/12/tutorial-para-placa-tv-encore-tv-fm-enltv-fm/")

Yo tengo una placa Encore ENLTV-FM. Pero no todas son iguales. La que está definida con el número 107 en la lista de tarjetas más actualizada del driver saa7134 se identifica con un subsystem 1131:2004, y en cambio la mía se identifica con un subsystem 1a7f:2004.

Estoy cargando el módulo saa7134 con los parámetros card=107 y tuner=37. Veo todos los canales de Cablevisión con tvtime y con MythTV, pero de la placa no sale ningún sonido. Lo he comprobado: tengo conectada la salida de sonido de la Encore a la entrada de la placa de sonido y nada; conecto unos auriculares de modo directo a la salida de sonido de la Encore, y nada.

Creo que acá existe un problema de distinto hardware bajo la igualdad de marca y modelo. Cuando la Encore ENLTV-FM se identifica como subsystem = 1a7f:2004 (la mía), el driver más actual de saa7134 no le da sonido. El autor del módulo de la ENLTV-FM para el driver saa7134, Juan Pablo Sormani, podría quizá darnos una mano si se enterara...

---

### Post by tzulberti on 2007-10-08
Tenes una placa que usa el mismo chip que la mia. 
Aca en su momento abri un tema para ver algo sobre esa placa.
[http://ubuntuforums.org/showthread.php?t=304444](http://ubuntuforums.org/showthread.php?t=304444)

Fijate que en la respuesta #34 tenes un mini how-to de como configurarla.

---

### Post by MeduZa on 2007-10-09
Hola

debe ser problema de configuracion de alsa perdon que no pueda aportar nada mas pero se me da que es algo por ese lado! si tu placa es onboard capas q el problema sea por ahi!

Las placas onboard trabajan con todo por software y a veces los puertos se setean virtualmente (y alsa no lo hace o lo hizo mal)

filate si otra cosa que metas por line in te sale por los parlantes y ya con eso te sacas la duda

Suerte

---

### Post by Mauro22 on 2007-11-15
> Hola, revivo este post!

quiero saber si existe alguna forma de volver a atras.

He bajado el v4l-dvb para poder ver tv usando la ENLTV-FM.

despues de cientos de pruebas salio andando. Pero solo hasta reinciar/apagar.

Despues nunca mas.


Quisiera saber (luego de haberle sacado todo el jugo a google) si puedo hacer algo para "volver a empezar" como si nunca hubiera compilado el v4l-dvb ni haber puesto la placa, etc etc!

SOLVED

---

