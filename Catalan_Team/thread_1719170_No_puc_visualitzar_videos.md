---
title: "No puc visualitzar videos"
date: 2011-04-01
forum: Catalan Team
---

### Post by dariusill on 2011-04-01
Hola que tal?

Cada cop tinc més problemes.

Ara resulta que al intentar fer gran un video del youtube em salta una pantalla que diu el que surt a la imatge que he adjuntat.


Cada cop tinc més problemes, repeteixo. Sento bombardejar.

Dàrius

---

### Post by kimet on 2011-04-01
Tens intal.lat el pluggin de flash?
Tens acceleració gràfica?
Fes:
```
glxinfo | grep direct
```( has de tenir instal-lat mesa-utils)

Salut.

---

### Post by dariusill on 2011-04-01
kimet,

Si, tinc instalat mesa-util i el Conector Flash Adobe.

Aquest es el resultat del codi que m'has dit per a que posi a la terminal...

Acer-TravelMate-5335:~$ glxinfo | grep direct
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0"


Continua el problema...

---

### Post by kimet on 2011-04-01
No tens acceleració gràfica.
Primer identifica la targeta gràfica i instal.la els drivers si cal, despres hauràs de configurar l'arxiu /etc/X11/xorg.conf adequadament.

Salut

---

### Post by dariusill on 2011-04-01
Dec haver instal·lat algun programa que m'ha revolucionat la targeta gràfica, perquè no fa gaire tot funcionava bé.  
A veure...per a mirar quina targeta gràfica tinc va per aqui...oi ?

**~$ lspci | grep -i vga**

* 00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)*

Quins són els drivers? tinc instal·lat Nvidia. no és això ?!

Gràcies

---

