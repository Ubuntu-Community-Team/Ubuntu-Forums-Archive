---
title: "ubuntu no reconeix auriculars"
date: 2009-07-10
forum: Catalan Team
---

### Post by anikuni_69 on 2009-07-10
Tinc HP Pavilion Dv6, i al principi d'instal·lar ubuntu no sonava res.
Després vaig actualitzar els drivers d'ALSA i vaig afegir la linia següent a l'arxiu /etc/modprobe.d/alsa-base.conf

*options snd-hda-intel model=hp-m4*

Des d'aleshores tot sona de meravella i el micròfon grava perfectament. L'únic problema és que el controlador de volum no detecta que hi ha una sortida d'auriculars a l'ordinador. He mirat les propietats del controlador de volum i no hi ha ni Headphones, ni jack, ni res que s'hi assembli (he provat tot el que hi ha). També he anat a Sistema/Preferències/So i tampoc no hi he sabut trobar res.
He mirat pel google però les poques solucions que he trobat no m'han servit.

Alguna idea?

Per cert, quan endollo uns auriculars no passa absolutament res, tot segueix sonant pels altaveus.

Gràcies!

---

### Post by pauelmaco on 2009-07-15
Aquí en parlen, també un HP pavilion dv6 amb el mateix problema.

[http://ubuntuforums.org/showthread.php?t=1200498](http://ubuntuforums.org/showthread.php?t=1200498)

---

