---
title: "Problemes amb GStreamer, crec."
date: 2011-03-23
forum: Catalan Team
---

### Post by Anskari on 2011-03-23
Hola a tothom,

Sóc nou per aquí i he estat buscant informació relativa al problema que tinc, però el que he trobat no em resolt res.

Tinc instal·lada la versió 10.10 - el Maverick Meerkat - i des del primer dia, quan reprodueixo vídeos o música, tant per el firefox o per el Rythmbox o el Moovida ho fa entretallat i a cops, gens fluïd o a una velocitat elevada. Imposible veure vídeos o escoltar música.

He provat a instal·lar i desinstal·lar els códecs peró res de res.

Algú em pot ajudar.

Gràcies a tothom.

Anskari.

---

### Post by wgarcia on 2011-03-24
El primer que convé fer és veure quina targeta gràfica hi ha instal·lada, cosa que es pot fer obrint una terminal (Aplicacions -> Terminal) i entrant

lspci | grep -i vga

i prement intro. La primera instrucció llista tots els dispositius "pci" i la segona selecciona les línies que diguin "vga" que són las de la gràfica, "-i" ignora majúscules i minúscules.

---

### Post by Anskari on 2011-03-24
La gràfica que tinc instal·lada es ATI Technologies Inc RV350 AS [Radeon 9550] amb el controlador compatible de linux.
Però crec que és més tema de la tarjeta de sò que de la gràfica, ja que no puc escoltar música tampoc...

01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]
02:0c.0 Multimedia audio controller: Creative Labs [SB Live! Value] EMU10k1X

---

### Post by wgarcia on 2011-03-25
Penso que el problema del so i de la gràfica són dos problemes separats, el millor és que obris un altre fil per al problema del so. 

En aquest fil es discuteix la instal·lació de mòduls adequats per a les targetes ATI:

[http://ubuntuforums.org/showthread.php?t=1573921&highlight=Radeon+9550](http://ubuntuforums.org/showthread.php?t=1573921&highlight=Radeon+9550)

En particular sembla que el kukat que volta per aquests fòrums té el mateix model que tu i potser pot donar una mà.

---

