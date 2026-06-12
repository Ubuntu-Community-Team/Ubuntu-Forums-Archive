---
title: "[SOLVED] Hardy + compiz= no más combinación de teclas."
date: 2008-05-19
forum: Argentina Team
---

### Post by valucha on 2008-05-19
[COLOR="DarkOrchid"]Hola, ahora si vengo por un problema más serio que estético... De un momento para el otro, la verdad no pude notar cuando (aunque tengo mis premoniciones) fue que perdí la capacidad de hacer ciertas combinaciones de teclas.. pero ya resulta incómodo.
Lo que no puedo hacer:
-ctrl c, ctrl v
-ctrl h (en nautilus para las carpetas ocultas)
-ctrl t (en firefox para abrir una pestaña)
-una combinación que yo determine en compiz para mostrar el escritorio (que tambien se me agrego en "combinaciones de teclas" en ubuntu), al principio si podía, pero de un momento para el otro dejé de poder. La combinacion es ctrl y la tecla que ellos llaman "masculine" pero que es la que está a la izquierda del 1.

Lo que si puedo hacer:
alt+f4
alt+tab
super + tab (para el ring switcher)
ctrl+alt+backspace.

LO que no puedo hacer básicamente son las que tienen el ctrl solo... No sé cuál es la razón, toqué todolo relativo en el panel de compiz y no se arregla. Lo mismo con la configuracion de las teclas de ubuntu y con la configuración del teclado...

Estoy re perdida, en internet encontré esto [http://www.ubuntu-es.org/index.php?q=node/89649](http://www.ubuntu-es.org/index.php?q=node/89649), pero nadie prece responderle... después no hay nada, ni en inglés ni en castellano.
Evidentemente metí la pata ocn algo...


Espero que me puedan ayudar, y desde ya mil gracias :)[/COLOR]

---

### Post by sajnox on 2008-05-19
Estas segura que es compiz? Lo deshabilitaste para ver si el problema persiste?

---

### Post by valucha on 2008-05-19
[COLOR="DarkOrchid"]Me olvidé de decir, que si deshabilito compiz, la combinación de teclas funciona normalmente.[/COLOR]

---

### Post by MeduZa on 2008-05-19
> **valucha said:**
> [COLOR="DarkOrchid"]Me olvidé de decir, que si deshabilito compiz, la combinación de teclas funciona normalmente.[/COLOR]

valucha solo se me ocurre que tengas pisada la tecla control con otra cosa en el menu que pongo en el adjunto, de ultima, vas a ~/.config/compiz/compizconfig y move eso a otro lado a ver que pasa.

---

### Post by Mister X on 2008-05-19
posiblemente algun plugin debe estar capturando esas hot-keys, podrias probar ir deshabilitando de a uno los plugins (con compiz activado) y probar las combinaciones que no te andan

---

### Post by Mauro22 on 2008-05-19
O por descarte:

Desactiva todos los plugins pero no desactives compiz.


Activas un plugin y probas las teclas, asi hasta que encontras el que falla.

---

### Post by sajnox on 2008-05-19
Plan B = restablece los valores por defecto.

---

### Post by valucha on 2008-05-19
[COLOR="DarkOrchid"]BUeno, finalmente lo agregué restableciendo los valores por defecto... Cosa rara ya que había "borrado" (ocn el botoncito de restablecer de cada efecto) todas mis preferencias anteriormente... Pero bueno, tal vez sea algún plugin habilitado/dehsabiitado por error...
NO pude encontrar cuál era, lo marco como solved pero cuando lo encuentre lo posteo para el próximo que se mande la metida de pata ^^


Gracias por su pronta ayuda...[/COLOR]

---

