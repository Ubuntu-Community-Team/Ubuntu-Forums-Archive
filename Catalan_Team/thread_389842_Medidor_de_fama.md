---
title: "Medidor de fama"
date: 2007-03-21
forum: Catalan Team
---

### Post by chalimac on 2007-03-21
Hola,

He escrit un programa  per aprendre python que mesura la fama de dos persones o conceptes baixant-se dades i imatges de yahoo.
[[IMG]http://img354.imageshack.us/img354/6408/famekalibratorwr9.th.jpg[/IMG]](http://img354.imageshack.us/my.php?image=famekalibratorwr9.jpg)

A veure què us sembla o com creieu que es podria millorar.

El podeu baixar aquí:

[http://www.kde-apps.org/content/show.php/Fame+Kalibrator?content=54990](http://www.kde-apps.org/content/show.php/Fame+Kalibrator?content=54990)

---

### Post by CarlesOriol on 2007-03-21
M'alegra de veure que el meu web (kumbaworld) és més conegut que l'orxata (tant en català com en castellà)....

... tot i que per mi l'orxata és molt important! ;.)

(la meva dona encara riu...)

:lolflag:

---

### Post by CarlesOriol on 2007-03-21
Conyes a banda...

 ... posa un rellotge quan estigui fent la recerca... per saber que està treballant.

---

### Post by RainCT on 2007-03-21
Doncs podries treure uns quants decimals (print "%.3f", per exemple, per a tres decimals).

---

### Post by chalimac on 2007-03-21
El tema dels decimals va ser bastant mal de cap. En python no funciona

print 1/2

ha de ser

print float(1)/2

Tampoc vaig investigar molt com treure posicions decimals perquè el gruix de la feina se'l va endur el codi per interactuar amb l'Api de yahoo. Provaré el consell de RainCT .

Per cert, si algú té curiositat per com he creat la part gràfica el procés ha estat:

1. Generar un .ui amb el QTdesigner.
2. Convertir-lo a pyqt amb "pyuic xxx.ui -o xxx.py"
3. Introduir les senyals i definir les funcions al document xxx.py amb qualsevol editor.

---

