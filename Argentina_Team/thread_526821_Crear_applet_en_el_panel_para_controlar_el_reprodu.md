---
title: "Crear applet en el panel para controlar el reproductor de musica."
date: 2007-08-15
forum: Argentina Team
---

### Post by valucha on 2007-08-15
[COLOR="DarkOrchid"]Bueno el tema es que vi en un lugar de alguien que enseñaba a crear un applet con estos botones  [http://superupload.fire-lion.com/download.php?file=d1d6bdde2357924653c708220c3641b9](http://superupload.fire-lion.com/download.php?file=d1d6bdde2357924653c708220c3641b9)
y lo creabas de forma manual para que puedas manejar desde ahi el reproductor de música.
Yo uso Listen ahora.. quisiera que me ayuden a identificar esos comandos... osea como es el comando de play, stop y para ir para atrás y adelante.
Si alguien puede hacerlo con el Rhythmbox no importa, trato de verlo con el Listen o me cambio al Rhythm porque total son muy parecidos.

Porbé ejecutando el listen desde terminal a ver que me decia cuando ponía play y eso y no dice nada...

Me ayudan?

Gracias desde ya.[/COLOR]

---

### Post by faktorqm on 2007-08-17
buena esa! parece que nadie la sabia! yo tampoco jajajajajajaj 

Para reproducir o pausar la canción:

```
listen --play-pause
```

para ir a la canción anterior:

```
listen --previous
```

para ir a la siguiente:

```
listen --next
```

pero tenemos un problema! no hay comando para parar la cancion. Lo que hay es un parche escrito por los propios desarrolladores, y en esta pagina te explica lo que tenes que agregar, en que linea, y en que archivo. sentite todo un programador men!

[http://www.listen-project.org/attachment/ticket/485/add_stop_button_and_commandline_option.patch](http://www.listen-project.org/attachment/ticket/485/add_stop_button_and_commandline_option.patch)

es de ortiva lo que te voy a decir: lo encontre en google poniendo en el buscador "comandos listen linux", asi que mira que kbza que soy!! ;) :D

---

### Post by valucha on 2007-08-17
> **faktorqm said:**
>  es de ortiva lo que te voy a decir: lo encontre en google poniendo en el buscador "comandos listen linux", asi que mira que kbza que soy!! ;) :D
[COLOR="DarkOrchid"]Pucha entonces no sé buscqar... yo siempre ponia applet listen ubuntu
music applet panel
etc.. pero nada de eso :(

Igualmente yo poniendo ese comando y no haciendo nada de lio como me dijiste puedo parar y reproducir con el mismo botón[/COLOR]

---

