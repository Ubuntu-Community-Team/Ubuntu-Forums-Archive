---
title: "garmin -- etrex vista hcx     GPS"
date: 2010-02-08
forum: Catalan Team
---

### Post by Miquel Ubuntero on 2010-02-08
Bones.
El meu germà, al qual li vaig instal·lar Ubuntu, hem pregunta que tal un GPS garmin amb Ubuntu. 
Suposo que vol saber si, en connectar-lo a Ubuntu, es detecta correctament i és pot actualitzar el mapes.
A veure si algú, per un casual, té un d'aquest dos models:
garmin -- etrex vista hcx     GPS   
garmin -- etrex legend h

Sembla que són d'un tipus de tamany reduït per anar a fer montanyisme.

O bé, si algú pot recomanar-nos un altre model que vagi bé amb Ubuntu, dons estaria bé.

Gracies per endavant.
Salutacions cordials,
Miquel.

---

### Post by SiscoGarcia on 2010-02-09
Ei Miquel, a [http://tinyurl.com/y8ens3c](http://tinyurl.com/y8ens3c) hi ha alguna cosa ;)

---

### Post by Miquel Ubuntero on 2010-02-09
Gracies Sisco.
M'ha agrada't molt el teu enllaç.
No ho havia vist mai això del google, està prou bé. No, és broma.
Però hem quedaria més tranquil si algú proper m'ha ves dit que li anava bé.
En qualsevol cas, gracies.
Salut!

---

### Post by somhi on 2010-02-09
Per aquest model en concret ni idea, però si que s'hi pot connectar altres models, com els rellotges Garmin Forerunner (paquet garmin-forerunner-tools)


Pots provar si funciona amb gpsbabel:
./gpsbabel -t -i garmin -f /dev/ttyUSB0 -o gpsdrive -F tracks.gps
./gpsbabel -t -i garmin -f /dev/ttyUSB0 -o kml,points=0,line_color=ff0000ff -F waypoints.kml

---

### Post by SiscoGarcia on 2010-02-10
> **Miquel Ubuntero said:**
> M'ha agrada't molt el teu enllaç.
No ho havia vist mai això del google, està prou bé.

No és meu, me'l va ensenyar en una situació semblant el papapep ;)

> **Miquel Ubuntero said:**
> Però hem quedaria més tranquil si algú proper m'ha ves dit que li anava bé.

Sento no poder ajudar-te més, però no faig servir cap GPS, de moment ja t'han donat alguna idea.

---

### Post by Miquel Ubuntero on 2010-02-12
Moltes gracies a tots dos.
Salut!

---

