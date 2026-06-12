---
title: "tancar l'ordinador correctament sense monitor"
date: 2009-01-24
forum: Catalan Team
---

### Post by indiosincracia on 2009-01-24
Salut, avui no para de marxar la llum, tinc un regulador de tensió amb bateria i cinc ordinadors connectats, els monitors no hi estan, perquè en lloc d'aguantar 7 minuts, amb els monitors només aguanta pocs segons.
hi ha alguna combinació de tecles que permeti tancar l'ordinador correctament, entenent que el monitor està apagat?

kubuntu hardy (el servidor)
la placa base es ASUS P5KPL-VM

i als altres xubuntu gutsy i kubuntu intrepid

el que faig cegament és F12 (que és l'emulador de terminal yakuake) i escric sudo poweroff i el codi, pero hi han cops que no funciona per que no veig el que faig.

Vinga merci, no oblideu de posar-vos pedres a les butxaques avanç de sortir, no quedarà res de peu aquí.

---

### Post by papapep on 2009-01-24
No sé quin SAI tens, però amb el dimoni upsd pots fer que un dels ordinadors monitoritzi, via port sèrie, el SAI i que, en cas de fallada del fluït elèctric, envii un avís a tots els altres i tots plegats es tanquin de manera "armoniosa".
Si el que tens és marca APC, amb l'[apcupsd]("http://packages.ubuntu.com/intrepid/apcupsd") tens el tema solucionat (per port sèrie, USB o ethernet, depenent del model de SAI), sinó, pots provar el que t'he comentat abans, [upsd]("http://packages.ubuntu.com/intrepid/upsd"), o algun que et proporcioni el mateix fabricant, que últimament s'han posat gairebé tots les piles :-)

---

### Post by papapep on 2009-01-24
Per cert, també t'hi pots connectar per ssh i anar-los tancant, com a mínim veuràs el que escrius.
També hi ha un projecte que permet tenir un sol teclat i ratolí per a diversos ordinadors, de nom [synergy]("http://packages.ubuntu.com/intrepid/synergy").

Serà per opcions, no??? :-D

---

