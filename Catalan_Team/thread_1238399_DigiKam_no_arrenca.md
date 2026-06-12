---
title: "DigiKam no arrenca"
date: 2009-08-12
forum: Catalan Team
---

### Post by prostata on 2009-08-12
Digikam 0.10 el que ve per defecte amb Jaunty no acaba d'arrencar i es penja, tant en mode gràfic com per terminal i per aquí em fa arribar el següent, però no termina d'arrencar:

Warning: No image data to encode Exif.OlympusCs.PreviewImageStart.
Warning: Exif tag Exif.Olympus2.ThumbnailImage not encoded
Warning: Exif tag Exif.OlympusCs.PreviewImageLength not encoded
Warning: Exif tag Exif.OlympusCs.PreviewImageStart not encoded
Warning: Exif tag Exif.OlympusCs.PreviewImageValid not encoded
Warning: Exif tag Exif.OlympusIp.0x1103 not encoded
Warning: Exif tag Exif.OlympusIp.0x1104 not encoded
Warning: No image data to encode Exif.OlympusCs.PreviewImageStart.
Warning: Exif tag Exif.Olympus2.ThumbnailImage not encoded
Warning: Exif tag Exif.OlympusCs.PreviewImageLength not encoded
Warning: Exif tag Exif.OlympusCs.PreviewImageStart not encoded
Warning: Exif tag Exif.OlympusCs.PreviewImageValid not encoded
Warning: Exif tag Exif.OlympusIp.0x1103 not encoded
Warning: Exif tag Exif.OlympusIp.0x1104 not encoded
Warning: No image data to encode Exif.OlympusCs.PreviewImageStart.
Warning: Exif tag Exif.Olympus2.ThumbnailImage not encoded
Warning: Exif tag Exif.OlympusCs.PreviewImageLength not encoded
Warning: Exif tag Exif.OlympusCs.PreviewImageStart not encoded
Warning: Exif tag Exif.OlympusCs.PreviewImageValid not encoded
Warning: Exif tag Exif.OlympusIp.0x1103 not encoded
Warning: Exif tag Exif.OlympusIp.0x1104 not encoded

Val dir que aquest llistat es fa interminable, això es nomes una petita mostra...

He mirat pe google però no hi trobo quelcom interessant que m'ajudi a solucionar el problema.. aquest programa hauria de "funcionar" amb metadades" i/o sense, per això em sorprèn aquesta reacció

Salutacions

---

### Post by prostata on 2009-08-13
finalment he aconseguit arrencar-lo i va bé, però surt en anglès i quan vull canviar l'idioma via help translate seleccionant el que vull o altres per fer proves, a la pàgina que surt i en seleccionar la llengua que vull, no apareix actiu el botonet translate per tant no puc canviar la llengua.

Dins el mateix help hi ha una opció: canviar l'idioma clico i els dos combos de la opció apareixen tots buits...¿per on poc mirar de trobar la solució...?? per Google no trobo res específic...

Salutacions

---

### Post by oriolsbd on 2009-08-13
Pot ser que no tinguis instal·lat el suport d'idioma de KDE? Em sembla que els paquets necessaris eren el "language-pack-kde-ca" i el "language-pack-kde-ca-base".

Salut!

---

### Post by jordilin on 2009-08-13
El digikam té un fitxer de configuració en ~/.kde/share/config/digikamrc. Si no et torna a arrencar o vols tornar als valors per defecte, esborres aquest fitxer i tornes a arrencar el digikam.

---

### Post by prostata on 2009-08-14
Gràcies no havia caigut en "KDE" 

Salutacions

---

