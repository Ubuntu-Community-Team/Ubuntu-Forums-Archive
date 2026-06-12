---
title: "La barra d'eines del Firefox no funciona"
date: 2009-03-23
forum: Catalan Team
---

### Post by Quepotser on 2009-03-23
Hola a tothom.
Avui, després d'engegar el Firefox, m'he trobat amb la sorpresa de que la barra d'eines havia deixat de funcionar. Tan sols apareix activada la icona de tornar a l'inici a la barra de navegació i en quant a la barra de les adreces d'interés m'ha aparegut totalment buida:[ATTACH]107406[/ATTACH]

He provat de reinstal·lar-lo però fa exactament el mateix. Com que si reinicio el Firefox puc utilitzar els menus de la barra superior (una vegada), he anat a la consola d'errors i em diu això:

[ATTACH]107409[/ATTACH]

Espero haver-me explicat prou bé. Si algú te alguna idea de què pot ser li agrairia molt que m'en fes cinq cèntims. Gràcies per endevant.

---

### Post by oriolsbd on 2009-03-23
Quan l'has desinstal·lat, ho has fet completament? Amb els fitxers de configuració i tot? Des de Synaptic seria "Marca per a desinstal·lar completament". Si no ho has fet així, prova de fer-ho.

---

### Post by Tomàs M. on 2009-03-23
També pots provar d'arrencar-lo amb un perfil nou, a veure què passa (firefox -profilemanager)

Sort!

---

### Post by Quepotser on 2009-03-24
Bon dia.

Oriolsbd: Vaig desinstal·lar completament amb en Synaptic i no va canviar res.

Tomas M.: Glups!, i com es fa això?

Gràcies per les vostres respostes.

---

### Post by oriolsbd on 2009-03-24
El que et comenta el Tomàs és executar en terminal el que t'ha escrit:
```
firefox -profilemanager
```

Salut!

---

### Post by Quepotser on 2009-03-24
Bona tarda. Ja he executat el "Firefox -profilemanager" i sembla que no ha canviat res. Però si miro la consola d'errors del Firefox em surt això:
[ATTACH]107496[/ATTACH]

---

### Post by oriolsbd on 2009-03-24
L'ordre que t'hem passat era incorrecta. Ha de tenir alguns caràcters en majúscula:
```
firefox -ProfileManager
```
Prova-ho així, a veure si t'obre l'administrador de perfils i en pots crear un de nou.

---

### Post by Quepotser on 2009-03-25
Bon dia. Efectivament aquesta vegada ha funcionat i he pogut crear el nou perfil, hi ha però, una pregunta: seria possible recuperar les adreces d'interès i l'historial del antic perfil?
De totes maneres moltes gràcies altra vegada i per endevant.

---

### Post by Tomàs M. on 2009-03-31
Perdona'm el retard i el tema de les majúscules (a mi em funciona sense...)
Prova d'instal·lar [FEBE]("https://addons.mozilla.org/ca/firefox/addon/2109") per a recuperar-ho (copiant del perfil antic, clar). També pots mirar de recuperar configuracions, extensions, contrasenyes desades, etc, però el meu consell és que recuperis cada vegada una cosa i comprovis el nou perfil, si recuperes el que t'està provocant el problema al perfil antic, malament... si ho fas pas per pas i se't reprodueix el problema, com a mínim en sabràs el culpable, i podràs recuperar tota la resta a un altre perfil.

Sort!

---

### Post by Quepotser on 2009-04-01
Moltes gràcies Tomas. Diuen que és millor tard que mai, o sia, igualment s'agraeix. Ja he sol·lucionat el tema del perfil i de les configuracions, però de totes maneres m'he baixat el FEBE, i després de probar-lo una miqueta he decidit que em pot anar molt bé.

---

