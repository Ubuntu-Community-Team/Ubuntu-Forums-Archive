---
title: "[SOLVED] TV-OUT Super video"
date: 2008-05-07
forum: Argentina Team
---

### Post by Tosh78 on 2008-05-07
Hola, tengo una placa de video intel (Mobile Intel(R) 915GM/GMS,910GML Express Chipset Family) y quiero saber como puedo hacer para darle salida de Super video y usar la tele como monitor.
Hay algun programita que permite hacer esto? En Win, cuando instale los drivers me aparecio la opcion, sin embargo en Ubuntu HH no tuve que instalar ningun driver y no veo esa opcion Alguien me puede dar una mano?

---

### Post by MeduZa on 2008-05-07
> **Tosh78 said:**
> Hola, tengo una placa de video intel (Mobile Intel(R) 915GM/GMS,910GML Express Chipset Family) y quiero saber como puedo hacer para darle salida de Super video y usar la tele como monitor.
Hay algun programita que permite hacer esto? En Win, cuando instale los drivers me aparecio la opcion, sin embargo en Ubuntu HH no tuve que instalar ningun driver y no veo esa opcion Alguien me puede dar una mano?

probaste enchufar el tv al super video y ver si te aparece en las opciones de monitor?
yo uso le panel de nvidia pero creo que hardy ahora detecta el tv solito una vez que lo enchufas.

---

### Post by ariel on 2008-05-08
> **Tosh78 said:**
> Hola, tengo una placa de video intel (Mobile Intel(R) 915GM/GMS,910GML Express Chipset Family) y quiero saber como puedo hacer para darle salida de Super video y usar la tele como monitor.
Hay algun programita que permite hacer esto? En Win, cuando instale los drivers me aparecio la opcion, sin embargo en Ubuntu HH no tuve que instalar ningun driver y no veo esa opcion Alguien me puede dar una mano?


es un poco complicado, hay  que editar /etc/X11/xorg.conf  y eso tiene el riesgo de que si algo sale mal, xorg no arranca y tenes que arreglar el problema desde la consola / linea de comandos y un editor de texto (nano, vi). Obviamente, antes de probar nada, hace un backup de xorg.conf. 
Yo en su momento use esto como referencia:

[http://loading-ideas.blogspot.com/2007/05/feisty-updates-tv-out-intel915.html](http://loading-ideas.blogspot.com/2007/05/feisty-updates-tv-out-intel915.html)

---

### Post by Tosh78 on 2008-05-08
Gracias a los dos, voy a probar eso.

---

### Post by spg76 on 2008-05-08
Te cuento mi experiencia, si tengo enchufado el cable a la TV antes de encender la PC me lo detecta automáticamente.
Si lo enchufo después,  lo habilito desde "Sistema > Preferencias > Resolución de Pantalla" (en Hardy). Ahí me pone la opción para elegir la TV, además de otras opciones como clonar pantallas, resolución de pantalla, etc.

---

### Post by Tosh78 on 2008-05-08
Hey, muy buen dato SPG!! Voy a probarlo, mil gracias!

---

### Post by MeduZa on 2008-05-08
> **ariel said:**
> es un poco complicado, hay  que editar /etc/X11/xorg.conf  y eso tiene el riesgo de que si algo sale mal, xorg no arranca y tenes que arreglar el problema desde la consola / linea de comandos y un editor de texto (nano, vi). Obviamente, antes de probar nada, hace un backup de xorg.conf. 
Yo en su momento use esto como referencia:

[http://loading-ideas.blogspot.com/2007/05/feisty-updates-tv-out-intel915.html](http://loading-ideas.blogspot.com/2007/05/feisty-updates-tv-out-intel915.html)

yo estaba hablando de hardy, donde todo lo detecta automatico y trata de no usar el xorg.conf

---

### Post by ariel on 2008-05-09
> **MeduZa said:**
> yo estaba hablando de hardy, donde todo lo detecta automatico y trata de no usar el xorg.conf

Yo tambien. El programita "Screen Resolution" (displayconfig-gtk) de hardy no "detecta" la salida TV-Out analogica. Detecta la conexion de un segundo monitor vga/dvi si la placa es dual head, o en una laptop. Y no anda muy bien, al menos en la laptop de mi laburo.

En mi caso, yo tuve que customizar xorg.conf para habilitar tv-out y hacer que la tele sea una extension del display lcd.

suerte...

---

### Post by Whiffle on 2008-05-09
No se habla espanol...


but you might check out "xrandr"

---

### Post by spg76 on 2008-05-09
> **ariel said:**
> Yo tambien. El programita "Screen Resolution" (displayconfig-gtk) de hardy no "detecta" la salida TV-Out analogica. Detecta la conexion de un segundo monitor vga/dvi si la placa es dual head, o en una laptop. Y no anda muy bien, al menos en la laptop de mi laburo.

En mi caso, yo tuve que customizar xorg.conf para habilitar tv-out y hacer que la tele sea una extension del display lcd.

suerte...

Según tengo entendido, desde "displayconfig-gtk" (que en el menú en español se llama "Pantallas y gráficos") se configuran los monitores y la placa de video, y por eso no te aparece la salida de TV.
Para habilitar la TV, yo utilizo "gnome-display-properties" (que en el menú en español se llama "Resolución de la pantalla").
Lo que no sé es porque no unifican todo esto, para tener un mejor control.

---

### Post by Tosh78 on 2008-05-09
Bueno, pude hacer que algo funcionase. Tengo Hardy pero si enchufaba el cable despues de haber encendido la maquina no me lo detectaba. Lo enchufe antes y ahi lo detecto. Desde Sistema, resolucion, elegi duplicar pantallas y demas. Salio la imagen en la tele, pero no se por que es como que refresca cada dos segundos. Intente cambiarle la tasa de refresco (que esta en 30, mientras que cuando esta solo el monitor esta en 60), pero no me dejo, ni siquiera aparece alguna otra opcion. Si alguien me puede tirar una soga con este tema, lo agradeceria, sino, marco el post como solved y vere que hago. Mil gracias a todos los que me respondieron.

---

### Post by User21 on 2008-05-09
Como tengo mi pc en mi habitación, y un TV junto al monitor, el TV-OUT es inamovible.
 Es necesario que lo enchufes y reinicies, para que aparezca detectado en "Resolución de Pantalla". Luego de eso, no necesitas moverlo mas! :P

---

