---
title: "Gutsy: lento y oscuro arranque"
date: 2007-10-20
forum: Argentina Team
---

### Post by hernan blau on 2007-10-20
Como les conté, instalé Gutsy Gibbon en mi portátil, la cual tiene un procesadobasa Intel Celeron M420. Desde que aprieto el botón de encendido hasta que suenan los tambores transcurren casi 3 tres minutos. Además, a partir de la aparición del Grub hasta los tambores la pantalla permanece en negro. Tarda bastante más en arrancar que Feisty. Cordialmente, HB.

---

### Post by freed0m on 2007-10-20
Lo que haria en tu caso sería editar la linea de kernel dentro del grub y le borraria  "quiet splash" y bootearia.
Con este cambio ayudará a ver más allá del simple "esperar unos minutos" sin saber que pasa o que es lo que está haciendo más lento el booteo de tu laptop.

Saludos.

---

### Post by dj_isaco on 2007-10-20
pero como se entra alli, perdon no soy el del problema pero me gusta aprender
:popcorn:

---

### Post by freed0m on 2007-10-20
> **dj_isaco said:**
> pero como se entra alli, perdon no soy el del problema pero me gusta aprender
:popcorn:

Este link puede servirte: [http://www.l3jane.net/doc/linux/suse/suselinux-adminguide_es/ch06s04.html]("http://www.l3jane.net/doc/linux/suse/suselinux-adminguide_es/ch06s04.html")

Justamente la parte donde se titula **6.4.1.3. Modificar las entradas de menú durante el proceso de arranque** se encuentra lo que estoy recomendando al compañero.

Saludos.

---

### Post by pacsum on 2007-10-21
[http://ubuntuforums.org/showthread.php?t=584205&highlight=gutsy+splash](http://ubuntuforums.org/showthread.php?t=584205&highlight=gutsy+splash)

---

### Post by hernan blau on 2007-10-21
Leeré los lugares que me señalan. Gracias. HB

---

### Post by hernan blau on 2007-10-24
Siguiendo sus consejos y, como no entiendo mucho inglés, cambiés por "nosplash" y ahora arranca rápidamente y muestra la carga. Seguí estas instrucciones: [http://www.ubuntu-es.org/index.php?q=node/66758](http://www.ubuntu-es.org/index.php?q=node/66758)
Suerte y gracias. Cordialmente, HB

---

