---
title: "Pantalla &quot;flickering&quot; - ATI Drivers"
date: 2008-05-02
forum: Argentina Team
---

### Post by fepe55 on 2008-05-02
Estoy con los Drivers propietarios de ATI y cuando intento utilizar un juego, por ejemplo el XMoto o el ManiaDrive, la pantalla *flickerea* (supongo que una traducción sería "parpadea").
Además, no puedo ver videos de YouTube en full-screen, pero esta vez porque anda lento, pocos FPS.

La placa es una ATI Radeon 9600XT (256MB).

Sé que el soporte de las placas ATI para Ubuntu no es el mejor, pero mejoró muchísimo en el último tiempo, así que espero sus sugerencias. Díganme qué otros datos necesitan.

¡Gracias!

---

### Post by sajnox on 2008-05-02
Yo tengo una radeon de ese modelo, si queres usar el driver de Ati bajalo con Envy [0], sino tenes el driver libre que tiene sus vueltas pero anda mejor con Hardy (con Hardy el driver propietario me arrastraba la maquina)

Probalos y fijate como andan con tu maquina, con Envy lo podes instalar y desinstalar a gusto sin problemas

[0] [www.albertomilone.com](www.albertomilone.com)

---

### Post by fepe55 on 2008-05-03
Lo instalé mediante Envy y nada, siguen sin funcionar.

Probé con los open-source que vienen por defecto, luego con los propietarios y ahora probé instalándolo mediante Envy y sigue tirando el mismo error.

Y probé los juegos en full-screen y no lo hace, es sólo cuando están <em>windowed</em>, ¿eso puede indicar algo más?

Mi xorg.conf está casi como por defecto, pero quizás sirva:

```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"es"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection

Section "Module"
	Load		"glx"
	Load		"dbe"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

```

---

### Post by sajnox on 2008-05-03
Perdon, me olvide de lo mas importante en esos casos. Si usas compiz deshabilitalo, compiz y arriba juegos es una mala idea.

Para deshabilitarlo podes elegir metacity como windows manager desde el compiz-icon (si no lo tenes lo recomiendo) Sino alt +f2 y escribis metacity --replace

Para jugar a mi me anduvo mejor el driver propietario, pero como te dije, con Hardy a mi me andaba pa' tra' 

Conta que pasa con tu maquina

---

### Post by fepe55 on 2008-05-03
Estupendo.

Instalé el fusion-icon, puse Metacity como Windows Manager y ahora todo anda.

¡**Muchas gracias** Sajnox!

---

