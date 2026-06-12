---
title: "Problemes amb la visualització del escriptori"
date: 2010-09-09
forum: Catalan Team
---

### Post by sergix on 2010-09-09
Bones,
Ahir vaig estar intentant activar els efectes del escriptori i vaig instal·lar paquets des del synaptic referents a la nvidia i el 3d. El cas és que no me'n vaig ensortir
La qüestió és que avui l'escriptori està com engrandit i nomès veig un quart de la pantalla amb les carpetes molt més grans.El problema també és que a la barra de dalt no veig gaires coses i no puc tancar l'ordinador ni canviar de sessió. Tampoc puc anar a "sistema" ni a "llocs". Per sort l'aplicació del terminal si que la veig i la puc fer servir.
Des d'allí he obert el synaptic i he desinsta·lat tot el que vaig instal·lar ahir.(gracies a Tux que hi ha la "historia del synaptic")Però res.
Es com si hi hagués un desajust de la imatge a la pantalla.
Tinc una nvidia geforce 7600. 

Algú sap que puc fer?
gracies

---

### Post by wgarcia on 2010-09-10
Des de la terminal que tens intenta córrer la següent comanda a veure si t'ho arregla:

sudo dpkg-reconfigure xserver-xorg

Aquesta comanda retorna els paquests de configuració del sistema gràfica als seus paràmetres inicials.

---

### Post by sergix on 2010-09-10
Ho he provat però no ha fet res.(el terminal no ha escrit ni una sola línea)
[HTML]sergi@sergi-desktop:~$ sudo dpkg-reconfigure xserver-xorg
[sudo] password for sergi: 
sergi@sergi-desktop:~$ [/HTML]
Estic mirant lo dels drivers però hem sembla que està tot insta·lat.
Mirant a nvidia-settings he vist que la resolució max. de la pantalla és la meitat de la que realment té. Llavors potser que d'alguna manera la targeta gràfica no és sincronitza bé amb la pantalla.

Pot ser "només" això el problema?
Com puc canviar això?

---

### Post by wgarcia on 2010-09-10
Suposo que hauràs reengegat l'ordinador després de donar l'ordre de "reconfigure", oi? O almenys hauràs sortit de la sessió d'escriptori i tornat a entrar?

---

### Post by sergix on 2010-09-10
si, he reiniciat. Però no ha canviat res.
M'hauria de haver escrit alguna cosa el terminal,no?

 Apart googlejant he llegit de mirar el xorg.conf i el meu hi diu això:

[HTML]Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection
[/HTML]
He vist que a la gent li surt a l'apartat "screen" diverses resolucions de pantalla i, a mi no; pot ser aquest el problema? ho edito jo manualment?

També he entrat amb un "usuari convidat" i passava el mateix.

---

### Post by sergix on 2010-09-10
Això vol dir que tinc ben instal·lats els drivers,no?
[HTML]sergi@sergi-desktop:~$ glxinfo | grep -i render
direct rendering: Yes
OpenGL renderer string: GeForce 7600 GS/PCI/SSE2/3DNOW!
    GL_NVX_conditional_render, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, [/HTML]

---

### Post by sergix on 2010-09-10
Ja ho he arreglat!!

Eliminant les icones de la barra de dalt he arribat a poder clicar a "sistema".
Sistema-> preferencies -> controladors de maquinari

Tenia el controlador privatiu i he posat el de ubuntu, he reiniciat i vualà!

Sembla mentida la de comandes rares que he arribat a posar i que fàcil ha sigut...

---

