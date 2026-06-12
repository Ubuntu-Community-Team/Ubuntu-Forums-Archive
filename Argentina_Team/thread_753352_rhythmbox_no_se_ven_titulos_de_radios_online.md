---
title: "rhythmbox no se ven titulos de radios online?"
date: 2008-04-12
forum: Argentina Team
---

### Post by MeduZa on 2008-04-12
Queridisima comunidad, acavo de encontrar un problema que posiblemente mas de uno ya vio y por ahi sabe como solucionarlo o tiene nocion de que es lo que lo causa.
El problema solo ocurre con radios online (broadcast) y es que el rhythmbox te muestra la radio que estas, el titulo, el autor de la cancion e incluso el album de tenerlo, pero el rhythmbox-client por consola solo te muestra la el nombre de la radio y nada mas.
para lograr el error hagan asi:
se conectan a una radio online.
en el rhythmbox arriba ven que diga el nombre de la cancion
abren una terminal y ponen:
rhythmbox-client --print-playing

espero alguno me sepa responder porque esa es la unica manera que tengo de parcear la informacion de que es lo que esta haciendo el rhythmbox

Saludos y muchas gracias.
PD: adjunto foto del problema

---

### Post by MeduZa on 2008-04-13
bueno viendo que nadie da pie con bola de que es, postie en el foro en ingles a ver si alguno alla sabe algo.
[http://ubuntuforums.org/showthread.php?t=754300]("http://ubuntuforums.org/showthread.php?t=754300")

---

### Post by oktubrer on 2008-04-13
Probaste con  --print-playing-format (Print formatted details of the song) en lugar del --print-playing  ???
Las opciones están en el man, pero las más interesantes son:

%at    Album title
%aa    Album artist
%tt    Track title
%ta    Track artist
%tn    Track number
%td    Track duration
%te    Elapsed time of track

---

### Post by MeduZa on 2008-04-13
> **oktubrer said:**
> Probaste con  --print-playing-format (Print formatted details of the song) en lugar del --print-playing  ???
Las opciones están en el man, pero las más interesantes son:

%at    Album title
%aa    Album artist
%tt    Track title
%ta    Track artist
%tn    Track number
%td    Track duration
%te    Elapsed time of track

yo probe, ¿a vos te funciona de alguna manera (la que sea)? porque a mi no y ya probe todo, repito solo pasa con radios online

---

