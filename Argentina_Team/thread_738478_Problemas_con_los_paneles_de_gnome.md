---
title: "Problemas con los paneles de gnome"
date: 2008-03-28
forum: Argentina Team
---

### Post by julgon on 2008-03-28
Hola, 
Tengo Ubuntu 7.10 y utilizo gnome y hace unos días comencé a tener problemas con los paneles (barras) del escritorio.  Tenia 2 y desaparecieron.

En realidad arrancan y luego, sin dejarme hacer nada desaparecen.
Pareciera que titilan, pero en realidad están arrancando y desapareciendo.  Pues si miras las procesos con ps -e aparecen una docena de procesos de gnome-panel.

He probado de todo!  Me asesoré con otros usuarios que conozco en el trabajo, con un poco más de experiencia que yo, que me hicieron borrar los archivos de configuracion .gconf, .gconfd .gnome .gnome2 .gnome2_private .metacity  .nautilus

También ejecute, como pude, el gnome-appearance-properties  y le saque todo efecto  al escritorio; también he matado todos los procesos para que arranque nuevamente... pero nada funciona!! las malditas barras no aparecen.

Si alguien tuvo un problema parecido y puede darme una mano...

Gracias y Saludos

---

### Post by xpelaox on 2008-03-28
proba esto, a mi me pasaba antes.


sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.orig

sudo nvidia-xconfig -composite

sudo nvidia-xconfig -allow-glx-with-composite

sudo nvidia-xconfig -render-accel

sudo nvidia-xconfig -add-argb-glx-visuals

Tras esto, reinicia el servidor gráfico con Ctrl+Alt+Borrar. Si el servidor gráfico no arranca y arranca Linux en modo texto, escribe estas órdenes para volver a la situación anterior:

sudo mv /etc/X11/xorg.conf.orig /etc/X11/xorg.conf

startx





Conta como te fue!

---

### Post by euzkoarima on 2008-03-28
Yo tuve un caso parecido cuando tenia compiz activado (no se si es tu caso). En el mio parece que conflictuaba el compiz con el selector de area de trabajo (en el panel de abajo). Si no lo usaba, no me desaparecía nada, pero sino, era una lotería. Al final lo saqué del panel y se estabilizó.

---

### Post by xpelaox on 2008-03-28
a mi me hacia lio el emerald con el compiz o algo asi:S

---

### Post by julgon on 2008-04-01
Nada, xpelaox.  Sigue todo igual. aparecen por unos segundos y cunado pinchas algun menu desaparece y vuelve a arrancar para luego desaparecer definitivamente.

¿Me pueden decir como se si tengo activado el compiz, así trato de desactivarlo.

Gracias igualmente por la soga que me tiraron.  Sigo con kde pero consume muchos recursos.

---

### Post by euzkoarima on 2008-04-03
(en gnome) Vas a Sistema->Preferencias->Apariencia, ahí a la solapa "efectos visuales" y elegí "ninguno". Te desactiva el compiz (no lo desinstala, pero lo desactiva).

Saludos

---

