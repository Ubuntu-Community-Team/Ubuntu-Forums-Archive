---
title: "Problemes amb la targeta grafica"
date: 2008-12-29
forum: Catalan Team
---

### Post by auska1714 on 2008-12-29
Bones, 

aviam si em podeu ajudar, m'he instal·lat un joc. Però quan provo de jugar-hi em surt una finestra que em diu:

Unsupported video card!

There are three possible causes for this error:
1. Your video card is too old
2. You haven't installed the latest available drivers
3. You haven't installed the latest DirectX version

Com puc saber quina de les tres possiblitats es la q em passa? I com puc arreglar-ho.

Merci,

Salut!

---

### Post by torracastanyes on 2008-12-29
Primer caldría saber quina tarja tens. Saps la marca i el model?
Es molt vella?

---

### Post by jerec on 2008-12-30
has de posar mes informació.

Model de tarja:
lspci | grep VGA

Amb que vols fer anar el joc wine, cedega.... 
Has mirat a les bases de dades de cedega si el joc funciona?¿
[http://www.cedega.com/gamesdb/]("http://www.cedega.com/gamesdb/")
o a les de wine?
[http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse Applications&sOrderBy=appName&bAscending=true]("http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse Applications&sOrderBy=appName&bAscending=true")

---

### Post by auska1714 on 2008-12-30
La targeta no se quina és :(, pot ser aquesta:
nVidia Corporation NV43 [GeForce 6600 LE]

I no necessita cam emulador, el joc funciona directament perquè es multiplataforma.

merci,

Salut!

---

### Post by torracastanyes on 2008-12-30
Amb aquesta tarja no hauríes de tenir problemes.

Ves a Sistema=>Administració=>Controladors de maquinari i mira si tens instalat el controlador privatiu, i si no ho està, instala'l

---

### Post by auska1714 on 2008-12-30
Ja està he instal·lat el que m'has dit i perfecte.

Merci ;)

Salut!

---

### Post by SiscoGarcia on 2008-12-30
> **auska1714 said:**
> Ja està he instal·lat el que m'has dit i perfecte.

Doncs què tal si marques el fil com a resolt?

Ja saps "Thread Tools" i després "Mark This Thread As Solved" ;)

---

### Post by auska1714 on 2008-12-30
Em sap greu ja ho farè, tot i que el problema persisteix ja que el meu germà volia el joc al seu ordinador també i quan li he instal·lat tinc el mateix problema. I en mirar d'instl·lar els controladors de propietat em diu que no s'usa per tant la solució d'abanç no serveix.

La seva targeta gràfica és la :  Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

que puc fer-hi? 

Merci,

Salut!

P.D.: Siscu et prometu que ara si quan funcioni el marcaré com a resolt xD

---

### Post by torracastanyes on 2008-12-30
De gràfiques Intel no en tinc cap, però diuen que funcionen amb els controladors lliures. Mira d'activar la acceleració gràfica.

Igual aquest fil t'ajuda:

[http://ubuntuforums.org/showthread.php?t=916695&highlight=intel](http://ubuntuforums.org/showthread.php?t=916695&highlight=intel)

---

### Post by jaume69 on 2008-12-30
Mirant per Google he vist això.

[http://linuxsix.blogspot.com/2008/12/intel-corporation-mobile-gm965gl960.html]("http://linuxsix.blogspot.com/2008/12/intel-corporation-mobile-gm965gl960.html")

Sort!..,si ho proves.

---

### Post by torracastanyes on 2008-12-31
Abans de tocar res del sistema, crec que hauríes de mirar com és d'exigent aquest joc. Mira els requeriments del sistema, a veure si diu res de la versió mínima de l'OpenGL o la velocitat del renderitzat.

Per veure la versió de l'Open GL, ves a la cònsola i escriu "glxinfo".
Comprova primer, a dalt de tot,  que digui "Direct Rendering=Yes" i busca la línia "OpenGL version string: X.X.X" que serà la versió que tens.

Per mesurar la velocitat del renderitzat, escriu "glxgears". Veuràs uns engranatges girant i a la cònsola t'apareixerà una medició cada 5 segons.

En principi, amb OpenGL 2.0 (o superior) i més de 2000 FPS, funcionen la majoría de jocs, però n'hi ha que xuclen molt més.

---

### Post by auska1714 on 2008-12-31
Bones,

aviam nem per pams. 

_Les característiques son: _

Mínimo
Procesador
Intel Pentium 3 800 Mhz o AMD Duron 900 Mhz o superior
Memoria
256 Megabytes de RAM o superior
Video
ATI Radeon 7500 o nVIDIA Geforce 2 y superiores
 
Recomendado
Procesador
Intel Pentium 4 2.4Ghz o AMD Athlon XP 2400
Memoria
512 Megabytes de RAM
Video
ATI Radeon 9600 o nVIDIA Geforce FX5700
[U]
Quan escric *glxinfo* em surt:[/U]
Direct Rendering=Yes
OpenGL version string: 1.4 Mesa 7.2
[U]
I quan escric *glxgears* em posa:[/U]

1466 frames in 5.0 seconds = 293.088 FPS
1612 frames in 5.0 seconds = 322.282 FPS
1581 frames in 5.0 seconds = 316.068 FPS
1593 frames in 5.0 seconds = 318.583 FPS
1596 frames in 5.0 seconds = 319.047 FPS
1580 frames in 5.0 seconds = 315.883 FPS
1587 frames in 5.0 seconds = 317.343 FPS
1578 frames in 5.0 seconds = 315.520 FPS
1565 frames in 5.0 seconds = 312.915 FPS
1569 frames in 5.0 seconds = 313.725 FPS
1587 frames in 5.0 seconds = 317.241 FPS

Salut!

---

### Post by torracastanyes on 2008-12-31
Mmmmm... Veig aquesta tarja una mica justeta. No sé si entra dintre dels requeriments, però la majoría de jocs no els mous amb menys de 500 FPS.
 
Compara aquest resultat amb l'altre ordinador, amb la nvidia 6600 hauríes d'anar al voltant dels 3000 FPS.

---

