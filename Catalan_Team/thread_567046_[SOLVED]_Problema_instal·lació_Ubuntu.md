---
title: "[SOLVED] Problema instal·lació Ubuntu"
date: 2007-10-04
forum: Catalan Team
---

### Post by Guillem_PV on 2007-10-04
Hola, volia preguntar una cosa.
M'hi he decidit a instal·lar-me Linux i més en concret Ubuntu. M'he descarregat el CD-Live (de la versió 7.04) i he provat d'instal·lar-lo però no em deixa. Quan carrega els arxius (s'omple la barra taronja) canvia la pantalla i es veu el cursor, el qual es mou durant dos segons i després queda tot totalment congelat. El mateix passa amb el mode gràfic de prova.
Pot ser problema de la targeta gràfica (tinc una nVidia GeForce 6600)?
Com que el meu ordinador és de 64 bits he provat amb el CD corresponent, penjant-se al mateix punt.
He provat també amb l'Alternate i nanai. Ja no sé què fer...
Tampoc és culpa d'un error al CD, perquè els he provats; ni del lector, perquè he provat amb un altre.
Teniu alguna idea? Gràcies.

---

### Post by papapep on 2007-10-04
Podries provar amb la versió alternate i passar-li la opció "noapic" a l'arrencada. A molta gent li soluciona el problema.

---

### Post by Guillem_PV on 2007-10-04
Gràcies ja ho tinc solucionat!!!
Moltes gràcies una altra vegada! \\:D/

---

### Post by eselma on 2007-10-05
Les targes nvidia amb el xip [COLOR="Red"]6600LE[/COLOR] donen problemes en GNU/Linux (jo en tinc una). Són reconegudes com a nvidia i els Live-CD els hi adjudiquen un controlador lliure "nv", però que no funciona bé en aquest model concret. Això ho he pogut comprovar en diverses distribucions, no solament en ubuntu. 

En canvi, un cop instal·lat pots canviar el controlador "nv" per "vesa" al fitxer */etc/X11/xorg.conf* (fes una còpia de seguretat del fitxer primer) i la pantalla ja es veu correctament, però sense l'acceleració gràfica en 3D. Llavors pots instal·lar el controlador privatiu de nVidia (*nvidia-glx* i els mòduls del kernel) amb el *Synaptic* o  l'*Adept* si uses [COLOR="DarkSlateBlue"][COLOR="Blue"]Kubuntu[/COLOR][/COLOR] i, un cop reengegades les X t'anirà correctament amb acceleració 3D (necessària per usar *Compiz-Beryl* i similars).

---

