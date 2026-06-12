---
title: "Problemes amb ratolí i entorn gràfic. Era:Solucionar un petit (però molt molest) bug."
date: 2010-05-06
forum: Catalan Team
---

### Post by Black_02 on 2010-05-06
Hola,
Tinc un petit problema amb l'ubuntu, i és que hi ha un bug que em fa desaparèixer entre altres coses, les descripcions que surten al passar el ratolí per sobre de les icones del sistema i dels enllaços. 

Em refereixo a això:

[IMG]http://s3.subirimagenes.com:81/imagen/4465195captura01.png[/IMG]

Però també em passa quan vull marcar varies icones amb el requadre que fa el ratolí (em desapareix sense soltar el botó):

[IMG]http://s2.subirimagenes.com/imagen/4465232captura02.png[/IMG]

I quan inicio el Google Picassa, no para de fer captures de pantalla automàtiques cada 3 segons més o menys.

Crec que tots aquests bugs són causa del mateix mal, crec que estan relacionats amb la captura de pantalla. És com si hi hagués una interferència que actua de manera sistemàtica cada pocs segons, hi he d'afegir que com a danys col·laterals, l'estalvi de pantalla no s'activa degut a que quan actua el bug el compte enrere per a que s'activi es deu posar a 0. 

He provat de treure el teclat per si les mosques, però el problema és una altra cosa.

Nota: El problema el tenia amb l'ubuntu 9.10 i ara amb 10.04 (fent una instal·lació des de 0 en els dos casos).

---

### Post by wgarcia on 2010-05-06
Has provat de crear un altre usuari i veure si també li passa el mateix? És convenient fer-ho per descartar que no sigui un problema de configuració del teu usuari principal.

---

### Post by Black_02 on 2010-05-06
Hola wgracia,

Ho acabo de provar i el problema hi continua sent. De fet fent una instal·lació des de 0, el problema hi és igualment, per tant no pot tenir res a veure amb la configuració, és més, amb la versió anterior (9.10) també em passava, però no amb les més antigues (8.10). El curiós del cas és que fa dos dies em va funcionar correctament, però allò va ser una cosa anecdòtica  :???:.

La veritat és que m'agradaria solucionar-ho, ja que resulta bastant molest, tot i que puc treballar igualment. 

Gràcies.

---

### Post by wgarcia on 2010-05-06
Fas servir els efectes gràfics especials (Compiz)? En cas afirmatiu prova de desactivar els efectes especials a veure si desapareix el problema.

---

### Post by Black_02 on 2010-05-06
Sí, però he provat de desactivar-los i res, el problema continua, és més he provat de iniciar l'ubuntu des de el CD (live CD) i el problema igual el tinc.

No se que pot ser.

---

### Post by wgarcia on 2010-05-07
Mira a veure si hi ha algun informe d'error al registre del sistema gràfic X. Per això intenta generar el problema, i immediatament obre una terminal i posa:

tail -10 Xorg.0.log

Si veus algun error enganxa'l aquí a veure si algú pot ajudar.

---

### Post by Black_02 on 2010-05-07
Em diu que no troba l'arxiu o el directori:

"tail: no s’ha pogut obrir «Xorg.0.log» per a llegir: No such file or directory"

---

### Post by wgarcia on 2010-05-07
Perdona, és que m'he equivocat, perquè evidentment l'arxiu aquest no està a la carpeta on s'obre el terminal. Ha de ser:

tail -10 /var/log/Xorg.0.log

---

### Post by Black_02 on 2010-05-07
Ara sí, em diu això:

(II) Logitech USB-PS/2 Optical Mouse: Found scroll wheel(s)
(II) Logitech USB-PS/2 Optical Mouse: Found relative axes
(II) Logitech USB-PS/2 Optical Mouse: Found x and y relative axes
(II) Logitech USB-PS/2 Optical Mouse: Configuring as mouse
(**) Logitech USB-PS/2 Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech USB-PS/2 Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB-PS/2 Optical Mouse" (type: MOUSE)
(II) Logitech USB-PS/2 Optical Mouse: initialized for relative axes.
(II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)

:confused:

---

### Post by wgarcia on 2010-05-08
L'última línia pot ser una mica sospitosa. En tot cas el teu problema sembla relacionat amb un malfucionament entre el ratolí i la targeta gràfica. Pot servir també que posis el que tens a l'arxiu de configuració del sistema gràfic X, que ja no s'utilitza gaire, però a vegades queden coses d'instal·lacions anteriors que poden afectar el funcionament del sistema gràfic. Per això dóna ara la següent instrucció a la línia de comandes:

cat /etc/X11/xorg.conf

i posa aquí el resultat.

---

### Post by Black_02 on 2010-05-08
Em diu que no el troba (igual que abans):

cat: /etc/X11/xorg.conf: No such file or directory

He intentat buscar-lo manualment, però dintre de la carpeta X11 no hi es:

[IMG]http://s2.subirimagenes.com/imagen/4473792cap01.png[/IMG]

He de dir que els drivers gràfics que tinc són el oberts (xserver-xorg-video-ati), ja que em funcionen més bé que el restrictius (fglrx). De totes formes abans al Ubuntu 9.10 tenia el restrictius i el problema igual hi era.

És possible que sigui algun residu de instal·lacions anteriors com tu dius, però és estrany perquè abans d'instal·lar he formatejat el disc dur, com no sigui un residu al la memòria ram no se que pot ser.

Gràcies pel teu interès... i per la teva paciència  
:smile:

---

### Post by papapep on 2010-05-08
I des d'un CD en viu et fa el mateix? o només amb la instal·lació normal?

---

### Post by Black_02 on 2010-05-08
Hola papapep,

Sí, des del cd en viu em passa el mateix, inclús he provat des del live cd de l'ubuntu 8.04 i res, continua igual. No se que carai pot ser :-k.

---

### Post by Black_02 on 2010-05-08
Per cert el meu ratolí és un Logitech MX 400.

[IMG]http://imagesb.ciao.com/ies/images/products/normal/201/product-690201.jpg[/IMG]

---

### Post by wgarcia on 2010-05-09
És normal que no hi hagi l'arxiu xorg.conf si és una  instal·lació nova, perquè ara aquest arxiu no es necessita, a no ser que s'hagi de canviar alguna especificació. Si hi és els sistema gràfic X el fa servir però si no hi és les últimes versions de GNU-Linux no el necessiten. 

Podria ser que necessitessis algun controlador especial per al teu ratolí, però abans de buscar i instal·lar un controlador, i crear un xorg.conf i posar una secció de ratolí en ell, potser el millor és que provis amb algun altre ratolí que algú et presti, per veure si realment és aquest el problema.

---

### Post by Black_02 on 2010-05-16
Ja he trobat el problema, era la targeta de TV (pinnace pctv 310i), tot i que funcionava, no ho feia del tot bé a causa del firmware.

Tenia que instal·lar el firmware nonfree:

sudo apt-get install linux-firmware-nonfree

---

