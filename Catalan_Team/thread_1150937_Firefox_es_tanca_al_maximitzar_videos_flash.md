---
title: "Firefox es tanca al maximitzar videos flash"
date: 2009-05-06
forum: Catalan Team
---

### Post by Picarona on 2009-05-06
Hola!

Aquí estic, barallant-me encara amb algunes coses d'Ubuntu...

D'ençà que vaig actualitzar al 9.04, tinc problemes al visualitzar videos de llocs com You Tube. Concretament al clickejar a la icona per veure el video en pantalla complerta.
El Firefox es tanca, inmediatament.

He reinstalat l'Adobe Flash Player vàries vegades, però res.

Algun suggeriment? (He buscat al fòrum, però no he trobat res).

Gràcies!!!

---

### Post by oriolsbd on 2009-05-06
Hola,

Prova d'executar el firefox des d'un terminal, a veure si quan es tanca et deixa algun missatge. Per a fer-ho, obre un terminal i executa:
```
firefox
```

Salut!

---

### Post by Picarona on 2009-05-06
Hola Oriol, i gràcies per respondre tan ràpid.
Copio tot el que surt al terminal per si té importància.

A l'iniciar apareix:

> (firefox:3479): Gtk-WARNING **: Error parsing gtk-icon-sizes string:
	'panel-menu=24,24
panel=20,20
gtk-button=18,18
gtk-large-toolbar=24,24'

I això al tancar-se:

> Xlib:  extension "GLX" missing on display ":0.0".
Segmentation fault

Tant de bó em puguis donar un cop de mà, gràcies!!!

---

### Post by mcako on 2009-05-07
Pots ser que sigui un problema dels drivers de la targeta gràfica.
Jo quan vaig actualitzar a la 9.04 vaig tenir alguns problemes amb els drivers, simplement no m'acceptava els drivers de Nvidia i vaig haver d'instal·lar una versió diferent dels drivers perquè em tornés a funcionar.
Per si de cas pots provar d'executar:
```
$ glxinfo | grep -i render
```

Si el resultat és algo així segurament tinguis problemes de drivers:
```
Error: couldn't find RGB GLX visual
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
```

---

### Post by Picarona on 2009-05-07
**Mcako**, l'has encertada.
Em surt això:

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
Xlib:  extension "GLX" missing on display ":0.0".


Miraré a veure si trobo informació sobre això que em comentes dels drivers. Espero sortir-me'n.

Moltes gràcies!!!

---

### Post by mcako on 2009-05-08
Jo ho vaig solucionar anant a Sistema > Controladors de Maquinari i m'apareixien 2 versions del driver d'Nvidia: la versió (137) i la (68 ) o algo així. Lo únic que vaig fer va ser activar la 68 en comptes de la 137 i ja se'm va arreglar tot. No sé si el teu cas serà el mateix, però pots provar-ho! toquetejar sense tenir-ne ni idea de vegades funciona..

---

### Post by Picarona on 2009-05-08
A Controladors de maquinari em surt que "Aquest sistema no utilitza controladors de propietat".
Quina cosa més estranya... seguiré investigant però gràcies per la pista, mcako!

Edito:
Solucionat fent el següent:
-Entrar a Sistema/Administració/Gestor de paquets Synaptic
-Buscar "nvidia"
-Marcar per eliminar tot el que fa referència a la versió 180
-Marcar per a instalar tot el que fa referència a la versió 96

Reiniciar i ja està!

El que encara no puc fer és activar els efectes d'escriptori. M'imagino que deu ser encara degut als controladors. Seguiré informant...

---

### Post by torracastanyes on 2009-05-08
Si el controlador 96 no et permet activar els efectes, prova d'instalar el 173. Si no és al Synaptic, ho pots provar a través de l'envy:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Sembla que molta gent hem tingut problemes amb el 180, però pel que he vist, el 173 està funcionant bé a tothom.

---

### Post by Picarona on 2009-05-11
Gràcies, Torracastanyes. Ho provaré i informaré puntualment per si li serveix a algú més.

---

