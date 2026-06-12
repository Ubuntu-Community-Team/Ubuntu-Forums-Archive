---
title: "mensaje de error cuando deseo abrir .avi"
date: 2008-05-04
forum: Argentina Team
---

### Post by AndreaSant on 2008-05-04
Desde que cargué hardy mis parlantes no funcionan,he probado con otros y el problema subsiste.
Ahora cuando quice visualizar algo bajado con aMule me pidió codecs nuevos,que instale de inmediato,pero cuando quice ver lo bajado me aparece el siguiente cartel:"Failed to connect stream:Invaled argumnet",como no sé si están relacionados,no entiendo mucho inglés y en ambos casos aparece la palabra stream pido ayuda,además quería saber si alguien cerca de mi hogar,es en Lanús que pueda ver mi máquina,sino a este paso mi nieto va a ver Shrek III cuando los hijos del ogro sean abuelos.
Desde ya agradecida por la ayuda.Andrea.

---

### Post by Hei Ku on 2008-05-04
con que programa quisiste verlo? Eso depende mucho, basicamente porque los programas son en realidad visualizadores, y el que realmente hace el trabajo de transformar el archivo a algo visible son motores de visualizacion (xine, gstreamer, etc) y cada uno tiene sus trucos.
Asi que es importante en estos casos saber que programa usaste. Es mas, algo que podes ver en VLC (por lo q se uno de los que se banca casi todo) quizas no lo puedas ver en Kaffeine. La libertad de elegir a veces tiene estas cosas, que lo complican un poco.

---

### Post by AndreaSant on 2008-05-05
> **Hei Ku said:**
> con que programa quisiste verlo? Eso depende mucho, basicamente porque los programas son en realidad visualizadores, y el que realmente hace el trabajo de transformar el archivo a algo visible son motores de visualizacion (xine, gstreamer, etc) y cada uno tiene sus trucos.
Asi que es importante en estos casos saber que programa usaste. Es mas, algo que podes ver en VLC (por lo q se uno de los que se banca casi todo) quizas no lo puedas ver en Kaffeine. La libertad de elegir a veces tiene estas cosas, que lo complican un poco.

Lo suyo FABULOSO puedo ver el video,aunque no lo puedo oir,cualquier sugerencia para los parlantes es muy apreciada por mí ,desde ya muchas gracias por tu ayuda (creo que el grito de alegria se debe haber escuchado por la red,por que es la primera vez que arreglo algo siguiendo directivas y me sale solita)Andrea.

---

### Post by faktorqm on 2008-05-06
Por el tema del parlante:

a) Están prendidos? Bien enchufados? el enchufe anda? si el enchufe es usb, se prenden las lucecitas? si no tiene lucecitas, yo que vos probaria otros parlantes o unos auriculares. Si el enchufe es tipo de adaptador y va a tras de la pc, ese enchufe anda? 
b) a donde esta conectado? deberian estar en el enchufe verde en la parte de atras de la compu. Hay 3 conectores (o mas dependiendo si es 5.1), uno celeste, uno verde y uno rosa. Deberian estar conectados en el verde.
c) en windows, se escucha? si no tenes windows, conecta SOLO la ficha de los parlantes a una radio/walkman/equipo de audio/ipod/mp3/mp4 y pone el volumen al taco. si se escucha, josha, descartamos problemas de parlantes.
d) En el "tray" busca el icono del parlante, hace click derecho y pone "Abrir control de volumen". Maestro, PCM y FRONT lo tenes que tener arriba de todo al 100%, y fijarte que en el iconito de abajo que es otro parlantito este "normal" Y NO CON UNA X ROJA. por que eso quiere decir que es mudo (mute). Si todo esta arriba cerramos. :D
e) Anda a sistema -> preferencias -> sonido. Ahora fijate donde diga eventos de sonido, musica y peliculas, y apreta el boton "probar" y asi con los otros. Ahi se tiene que escuchar un "piiiiiiiiiiiiiiiii" hasta que vos le des aceptar. SI TE TIRA UN ERROR, POSTEA CUAL ES EL QUE TIRA. Si no queres escribir, apreta la tecla "Impr pant" y subi a algun lado la imagen y postea el link. 

Creo que es exhaustiva la guia, si me olvide de probar algo posteen no tengan miedo. Salu2!!

---

### Post by AndreaSant on 2008-05-06
> **faktorqm said:**
> Por el tema del parlante:

a) Están prendidos? Bien enchufados? el enchufe anda? si el enchufe es usb, se prenden las lucecitas? si no tiene lucecitas, yo que vos probaria otros parlantes o unos auriculares. Si el enchufe es tipo de adaptador y va a tras de la pc, ese enchufe anda? 
b) a donde esta conectado? deberian estar en el enchufe verde en la parte de atras de la compu. Hay 3 conectores (o mas dependiendo si es 5.1), uno celeste, uno verde y uno rosa. Deberian estar conectados en el verde.
c) en windows, se escucha? si no tenes windows, conecta SOLO la ficha de los parlantes a una radio/walkman/equipo de audio/ipod/mp3/mp4 y pone el volumen al taco. si se escucha, josha, descartamos problemas de parlantes.
d) En el "tray" busca el icono del parlante, hace click derecho y pone "Abrir control de volumen". Maestro, PCM y FRONT lo tenes que tener arriba de todo al 100%, y fijarte que en el iconito de abajo que es otro parlantito este "normal" Y NO CON UNA X ROJA. por que eso quiere decir que es mudo (mute). Si todo esta arriba cerramos. :D
e) Anda a sistema -> preferencias -> sonido. Ahora fijate donde diga eventos de sonido, musica y peliculas, y apreta el boton "probar" y asi con los otros. Ahi se tiene que escuchar un "piiiiiiiiiiiiiiiii" hasta que vos le des aceptar. SI TE TIRA UN ERROR, POSTEA CUAL ES EL QUE TIRA. Si no queres escribir, apreta la tecla "Impr pant" y subi a algun lado la imagen y postea el link. 

Creo que es exhaustiva la guia, si me olvide de probar algo posteen no tengan miedo. Salu2!!

1)los parlantes funcionan es t{an bien enchufados,probé 4 juegos de parlantes distintos que funcionan en otras máquinas y en esta no,desde que instalé el sistema nuevo el 26/4 aparece el parlantito tachado y cuando pongo probar aparece audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument,Desde ya agredecida por tu ayuda Andrea

---

### Post by faktorqm on 2008-05-06
ok, anda a sistema -> preferencias -> sonido, se ve algo asi?

[[img=http://img227.imageshack.us/img227/9306/pantallazooi2.th.png]](http://img227.imageshack.us/my.php?image=pantallazooi2.png)

por que a mi me tira el error que vos nombras cuando uso pulseaudio:

[[img=http://img227.imageshack.us/img227/8760/pantallazo1gb4.th.png]](http://img227.imageshack.us/my.php?image=pantallazo1gb4.png)

Fijate de ir cambiando y/o de postear una imagen a ver que esta pasando. Salu2!!

---

### Post by sajnox on 2008-05-06
Me sumo a lo que dice faktor, en sonido pone todo en alsa que va a andar

---

