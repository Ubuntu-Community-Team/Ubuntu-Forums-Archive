---
title: "Problemas con el puntero del Mouse"
date: 2007-01-17
forum: Argentina Team
---

### Post by godzeus on 2007-01-17
Espero que alguien me pueda dar una mano, es mi primer post.
Estoy teniendo problemas con el puntero del mouse, cuando lo muevo de repente se va para arriba o me abre ventanas solas, o me muestra la ventana de logout.
Hasta ahora lo unico que pude sacar en limpio es que para solucionarlo momentaneamente,tengo que presionar Alt+Tab y marcar una aplicacion en uso, pero esto no sirve siempre.

PD: me olvidaba uso Ubuntu 6.10 Edgy Eft, ya tengo mis stickers!!!!!!!!!!!
Gracias ULUGA

](*,) :-k

---

### Post by beuno on 2007-01-17
> **godzeus said:**
> Espero que alguien me pueda dar una mano, es mi primer post.
Estoy teniendo problemas con el puntero del mouse, cuando lo muevo de repente se va para arriba o me abre ventanas solas, o me muestra la ventana de logout.
Hasta ahora lo unico que pude sacar en limpio es que para solucionarlo momentaneamente,tengo que presionar Alt+Tab y marcar una aplicacion en uso, pero esto no sirve siempre.

PD: me olvidaba uso Ubuntu 6.10 Edgy Eft, ya tengo mis stickers!!!!!!!!!!!
Gracias ULUGA

](*,) :-k

Podes atachear tu "/etc/X11/xorg.conf"?

---

### Post by godzeus on 2007-01-17
Beuno,sos rapido pa´ los mandados vithe, en cuanto llegue a casa(estoy en un ciber, trabajando????:-k naaa) lo subo al post.
gracias por tu respuesta.

---

### Post by godzeus on 2007-01-17
Beuno, te adjunto el archivo que me pediste

---

### Post by lavaramano on 2007-01-18
yo lo unico que vi de distinto con el xorg.conf de la maquina del trabajo (donde tengo la misma placa que vos y y eso) es esto:

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

los que dicen sendcoreevents, por lo que vi. no te haria falta 
y si no tenes tablets pc, tampoco te harian falta los /dev/wacom (yo los tengo y no tuve problemas, pero que se yo)

proba comentando eso (hace un backup por las dudas :mrgreen:) y conta si te sirvio

---

