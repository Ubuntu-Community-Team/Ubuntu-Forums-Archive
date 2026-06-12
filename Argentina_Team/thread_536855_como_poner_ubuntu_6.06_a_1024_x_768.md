---
title: "como poner ubuntu 6.06 a 1024 x 768"
date: 2007-08-28
forum: Argentina Team
---

### Post by aceki on 2007-08-28
Gente buen dia, como puedo cambiar el el xorg.conf para que me habilite el 1024 x 768 en gnome,

---

### Post by rojojuan on 2007-08-28
En el xorg tenés puesta la sincronización de horizontal y vertical que corresponde a tu monitor?

---

### Post by faktorqm on 2007-08-29
Hola, por lo general, los problemas de resolucion se deben a que esta mal configurado en el xorg.conf la frecuencia de refresco horizontal y vertical del monitor. Entonces, para que no se te vaya de rango, no te deja poner ciertas resoluciones, pero en realidad lo que pasa es que hay que correr el tope digamos.
Busca en google las frecuencias de refresco horizontal y vertical de tu monitor, y despues edita el archivo: "sudo gedit /etc/X11/xorg.conf" (sin comillas)
hay una parte que es la que te pego a continuacion que es la que tenes que cambiar:

```
Section "Monitor"
	Identifier	"Monitor genérico"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Tarjeta de vídeo genérica"
	Monitor		"Monitor genérico"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

Bueno, en la sección monitor ahi le pones los valores, y en la seccion screen te fijas de tener bien las resoluciones, sino, "sudo dpkg-reconfigure -phigh xserver-xorg" (sin comillas) y reconfiguras. (recorda revisar que no te pise la configuracion del monitor).
Bueno espero que te haya servido. salu2!!

---

### Post by clasificado on 2007-08-29
Me pregunto como hará Windows para autodetectar las frecuencias cuando el driver es monitor plug and play, porque anda joya

Clasificado

---

