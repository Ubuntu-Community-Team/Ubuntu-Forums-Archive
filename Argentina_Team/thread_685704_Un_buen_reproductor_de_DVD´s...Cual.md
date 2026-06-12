---
title: "Un buen reproductor de DVD´s...Cual?"
date: 2008-02-02
forum: Argentina Team
---

### Post by atari130xe on 2008-02-02
Gente, encontré LinDvD un paquete de Mandriva (RPM) "transformado" a DEB, lo instalé y funca, pero... no logro hacer que reproduzca el disco al insertarlo en la bandeja, el que se "abre" automáticamente es Totem pero me tira un error y no logro reproducirlo, cual sería la mejor opción? y como hacerlo claro :)
Gracias

---

### Post by sajnox on 2008-02-02
En mi opinion hay una sola respuesta a tu pregunta

sudo apt-get install vlc

Saludos

---

### Post by atari130xe on 2008-02-02
Si, lo tengo instalado pero no puedo reproducir los dvd, no se que debo configurar para que eso sea posible.

---

### Post by marianom on 2008-02-02
Por  lo menos para usar Totem con DVD es medio un problema y para nada intuitivo.
Hay un paquete que te exige el Totem al intentar ejecutar un DVD y en el unico lugar que está es en medibuntu (o al menos el único lugar en donde lo encontré con poco tiempo y dialup).
Concretamente ahora no recuerdo que fue lo que tuve que instalar pero con aptitude veo que tengo libdvdcss2, libdvdnav4 y libdvdread3 instalados.

Los repos eson estos:
```
deb http://packages.medibuntu.org/ gutsy free non-free
deb-src http://packages.medibuntu.org/ gutsy free non-free

```

Igual Totem te va tirando los mensajes de error y así sabes que paquete falta.

---

### Post by Mauro22 on 2008-02-02
> **sajnox said:**
> En mi opinion hay una sola respuesta a tu pregunta

sudo apt-get install vlc

Saludos


:guitar:
Se banca lo que viene el VLC!!

---

### Post by santiagoward2000 on 2008-02-02
> **marianom said:**
> Igual Totem te va tirando los mensajes de error y así sabes que paquete falta.

Hola!
Sobre el Totem, la verdad que tratar de ver DVDs con** totem-gstreamer** me volvió loco. A mí me resultó mucho más fácil y cómodo usar el **totem-xine**. Me anda sin ningún problema! :)
Saludos!

---

### Post by leo_rockway on 2008-02-02
tal como dijo mariano necesitas libdvdcss2 para ver dvds...

yo en general uso mplayer en su sabor smplayer.

hasta ahora no me dejo de reproducir ningun archivo el mplayer; es algo asi como un vlc, pero mas lindo (no me gusta que en vlc la barra de progreso/desplazamiento sea tan poco cooperativa a al hora de saltar escenas y tp me gusta como se ven los subs)

---

### Post by atari130xe on 2008-02-03
Okis tomo en cuenta sus recomendaciones :)

---

### Post by marianom on 2008-02-03
Por otra cuestión llegué hasta [este documento]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs") del wiki de ayuda de Ubuntu y pensé que te podría interesar.

---

### Post by jpmorelli on 2008-02-04
Todavía sigo sin comprender porque sacaron  un motor como el Gstreamer que tiene tantos problemas con formatos como el DVD, Está bien que son formatos privativos pero acaso el Xine no se rige bajo los mismos conceptos ?
Alguien hizo funcionar el totem-gstreamer para poder ver el menú y los subtitulos de un DVD ?

---

### Post by aregnando on 2008-02-04
Hola atari130xe, yo instalé Kaffeine en mi Ubuntu y la verdad es que funciona perfectamente bien, tenés posibilidad de controlar todo lo que quieras con este programa, incluso tiene un ecualizador para mejorar el sonido.
Para instalarlo simplemente desde synaptic podés hacerlo sin ningún tipo de problema.
Saludos.

---

### Post by kowal on 2008-02-04
> **aregnando said:**
> Hola atari130xe, yo instalé Kaffeine en mi Ubuntu y la verdad es que funciona perfectamente bien, tenés posibilidad de controlar todo lo que quieras con este programa, incluso tiene un ecualizador para mejorar el sonido.
Para instalarlo simplemente desde synaptic podés hacerlo sin ningún tipo de problema.
Saludos.

Claro, porque Kaffeine usa el motor Xine (y no Gstreamer)

---

### Post by hernan blau on 2008-02-05
Luego de varios intentos me quedé con el Kaffeine. Suerte!!

---

