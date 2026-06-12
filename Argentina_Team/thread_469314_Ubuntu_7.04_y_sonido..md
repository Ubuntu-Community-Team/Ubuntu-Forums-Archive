---
title: "Ubuntu 7.04 y sonido."
date: 2007-06-09
forum: Argentina Team
---

### Post by ricardomanu on 2007-06-09
Hola, me a surgido otro problema con UBUNTU 7.04 Feisty, esta vez es con el sonido, la placa de sonido es una CREATIVE SOUND BLASTER, Modelo CT4750, en Ubuntu lo detecta como Ensoniq (ES 1371). El problema es que el sonido se corta al estar escuchando con el XMMS, es decir que quedo sin sonido en Ubuntu, tengo que reiniciar para que vuelva el sonido. He actualizado los driver de ALSA a la version 1.0.14, pero sigue el problema, he cambiado en el XMMS, los PLUGINS de salida, y el sonido vuelve pero el sistema no. En ALSAMIXER, los valores estan bien.
Cual puede ser la causa.

Gracias.

---

### Post by Gideon26 on 2007-06-10
Hola probaste copilar los controladores de alsa? no te falto bajar los lib-plugins y los tools? yo en tu caso probaria purgando y colocando los drivers de alsa (todas las actulizaciones de alsa lib-plugins, etc) y los volveria a copilar.

Saludos

---

### Post by ricardomanu on 2007-06-10
Como se hace para purgar, los lib-plugins y los tools no lo he tenido en cuenta, lo bajare, me podrias decir cuales son los pasos.

Gracias por responder.

---

