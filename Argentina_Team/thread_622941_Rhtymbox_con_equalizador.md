---
title: "Rhtymbox con equalizador??"
date: 2007-11-25
forum: Argentina Team
---

### Post by niko_3100 on 2007-11-25
Gente alguien conoce un plugin o una liberia o algo para que el rhtymbox tenga equalizador?? Creo que es lo unico que le falta para ser completisimo y no tan pesado jeje, tengo ua notebook con la tecla Fn de todas las notebooks y el rhtymbox me reconoce los accesos directos a play, forward, backward, pause y eso y me es re comodo probe el xmms player pero no me reconoce los accesos directos solo me reconoce los acceso directos que vienen por defecto en la configuracion del xmms y cuand esta maximizado usandose si lo minimizo no me reconoce los accesos directos a part ede eso el rhtymbox me es mucho mas lindo, me encanta pero quiero un equalizador es lo unico que el falta, alguien conoce algo?? Gracias.

---

### Post by margori on 2007-11-25
Pues yo pensaba lo mismo que vos, con respecto a Rhythmbox, hasta que probe Amarok y compere los comsumos de memoria y prestaciones.

---

### Post by niko_3100 on 2007-11-25
En serio? que obtuviste? el amarok tiene equalizador? Nunca lo quise bajar porque como es para kde.... que se yo...

---

### Post by santiagoward2000 on 2007-11-25
Sino podés probar el Exaile. Es parecido al Amarok, pero para GTK y más liviano, y también tiene ecualizador.
Saludos.

---

### Post by margori on 2007-11-25
Si bien Amarok esta pensado para KDE, cuando lo queres instalar en GNome, me parece, baja tambien una "libreria" para que se ejecute usando las GTK+.

La cosa es que probe Exaile y Amarok y el primero consumia 19MB mientras que Amarok usaba 21MB. Me parecio poca diferencia y muchas mas ventajas.

Conclusion, proba los dos y quedate con el que te guste.

---

### Post by facundocorradini on 2007-11-25
Pues mi duda es la misma.

Yo pasé por todos los reproductores que me crucé por el camino (includo Amarok), y la verdad es que me quedo más cómodo con Rhythmbox.

Pero es cierto, el hecho de no tener un ecualizador es realmente molesto, más aún para mí (trabajé varios años en sonido, tengo muy "afinado" el oido...)

Alguien conoce una forma de agregarle un buen EQ al rythmbox?

---

### Post by margori on 2007-11-26
Consegui la informacion mas importante para entender porque Rhythmbox no trae equalizador y no lo va a traer:

"An application like Rhythmbox relies on GStreamer to decode sound files from compressed form into raw audio. GStreamer in turn passes the audio down to ESD, and ESD delivers it to the ALSA hardware driver." (Desde [http://www.linux.com/feature/119926?theme=print](http://www.linux.com/feature/119926?theme=print))

GStreamer es el que trae el plugin de analisis de espectro, equalizador pero aun esta en desarrollo (Cito [http://bugzilla.gnome.org/show_bug.cgi?id=415627](http://bugzilla.gnome.org/show_bug.cgi?id=415627) ; [http://bugzilla.gnome.org/show_bug.cgi?id=426562](http://bugzilla.gnome.org/show_bug.cgi?id=426562) )

Programas como Xine o XMMS se encargan de hacer todo el trabajo sucio y darle a ALSA o ESD todo digerido para que lo pueda mandar al hardware. En cambio Rhythmbox hace un parte, otra GStreanmer, otra ESD, otra ALSA y por ultimo a los parlantes.

Espero sea util. Espero opiniones.

---

### Post by facundocorradini on 2007-11-26
pues eso es un punto a favor de quienes dicen que los desarrolladores de Gnome son vagos...

No hay que ser muy genio para darse cuenta que una aplicación de sonido necesita tener un ecualizador propio. Usar una EQ global no  me parece para nada la solución óptima.. De hecho, soy de los que en epocas de Winamp ya ponía ecualizaciones distintas para cada tema..

en fin, creo que voy a darle una aportunidad a amarok...

---

### Post by niko_3100 on 2007-11-26
Que bajon eso, creo que un reproductor que se diga ser bueno tiene que tener como minimo un equalizador pero bueno... probare otros a ver que onda jeje!! Nadie sabe como  hacer para que el xmms me reconozca las teclas que configure en sistema-->preferencia--> combinacion de teclas  ?? son amante de los accesos directos con combinacion de teclas, ejemplo para ver el escritorio ctrl alt +D esas combinaciones jeje pero el xmms no me las reconoce.

---

