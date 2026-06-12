---
title: "On és compiz???"
date: 2007-10-22
forum: Catalan Team
---

### Post by prostata on 2007-10-22
Finalment vaig fer l'actualització a la Gibbon, i algunes de les meves dubtes:

A synaptic veig el compiz, però no veig l'icona del setting manager, ¿on és?
A preferències Sessions a session actual i veig compiz però continuo sense veure el setting manager, com per exemple a Beryl.
Emerald és totalment buit, cap tema, els repos no descarreguen res...

Salutacions

---

### Post by nickpage on 2007-10-22
Hola,

El setting manager de compiz l'has de instal·lar via synaptic, al menys així ho he fet jo i funciona prou be.

L'emerald efectivament no carrega cap tema i en el meu cas no m'apareixen els bordes de la finestra.

---

### Post by prostata on 2007-10-22
> **nickpage said:**
> Hola,

El setting manager de compiz l'has de instal·lar via synaptic, al menys així ho he fet jo i funciona prou be.

L'emerald efectivament no carrega cap tema i en el meu cas no m'apareixen els bordes de la finestra.

de calaix, company, de calaix.
Jo sempre he fet servir Beryl i dec supossar que bàsicament es el mateix, ¿no?,Ara dis-me:

Com faig per arrencar compiz amb el sistema?
Com "activo...." es que no se com dir-lo....a pams, avanç amb beryl tenia configurat que el "cubo", funciones via mouse, i que desplaçant el cursor a un vertix de la pantalla, s'actives, No veig la forma de fer el mateix amb Compiz...donem un cop de má...Gràcies

---

### Post by Ferri on 2007-10-22
Has d'anar al gestor de temes (ara mateix no tinc el meu ordinador al davant i no recordo si el nom exacte és aquest). Hi ha una pestanya que et permet habilitar els efectes visuals; agafa l'opció que et convingui més i ja ho tens activat.

---

### Post by jerec on 2007-10-22
Amb el Beryl tenies l'icona en forma de diamant vermell, amb el compiz-fusion tambe en tens una d'icona, la tens aqui: [http://ubuntuforums.org/attachment.php?attachmentid=42083&d=1188455999]("http://ubuntuforums.org/attachment.php?attachmentid=42083&d=1188455999")
Descarrega el deb i instala-la al teu sistema
Podras activar, desactivar el compiz-fusion i engegar el SettingsManager

Sino, sempre pots posar un script dins de .kde/Autostart/
ex:
#!/bin/bash
compiz --replace

Per el que dius del cub, es exactament el mateix, el que passa es que ho han canviat una mica graficament. Desde SettingsManager al plugin de "Cub d'escriptori" a la pestanya Actions, desplegues General i tens 3 opcions: Desplegar, Diapositiva siguiente i Prev Slide, tries la que vols modificar amb doble clic i jasta.

---

### Post by prostata on 2007-10-22
> **jerec said:**
> Amb el Beryl tenies l'icona en forma de diamant vermell, amb el compiz-fusion tambe en tens una d'icona, la tens aqui: [http://ubuntuforums.org/attachment.php?attachmentid=42083&d=1188455999]("http://ubuntuforums.org/attachment.php?attachmentid=42083&d=1188455999")
Descarrega el deb i instala-la al teu sistema
Podras activar, desactivar el compiz-fusion i engegar el SettingsManager

Bé doncs ja ho he fet, i veig l'icona de compiz fusion. Quan cliko sobre ell no s'activa cap altre icona, però a dalt a la dreta al costat del rellotge, al passar el cursor veig compiz fusion en format text, però cap icona. Una mica esrany, no?

Sino, sempre pots posar un script dins de .kde/Autostart/
ex:
#!/bin/bash
compiz --replace

Per el que dius del cub, es exactament el mateix, el que passa es que ho han canviat una mica graficament. Desde SettingsManager al plugin de "Cub d'escriptori" a la pestanya Actions, desplegues General i tens 3 opcions: Desplegar, Diapositiva siguiente i Prev Slide, tries la que vols modificar amb doble clic i jasta.

Un cop estic a settings puc veure: Reload windows Manager|Select Windows Manager| [per defecte Compiz]|Compiz options ¿?| Select windows decorator| [emerald no és i activa per defecte GTK windows decorator. ¿tot aixó es correcte??     

Dins settings manager Desktop tinc marcat per defecte:  CUB com escriptori/ girar el cub. Dins cub com espcriptori tinc actiu un únic cub. I en actions  desplegar crt+alt+tn abaix. Boton=none. 
Jo només vull saber:
Com arrebacr el cub, com fer-lo girar de la resta ja m'en carregaré més tard.

---

### Post by prostata on 2007-10-22
Ja el tinc sol-lucionat...de moment!!:)

---

### Post by nickpage on 2007-10-22
He instal·lat el paquet deb per veure l'icone, però no es veu, si que hi ha un espai ficat a l'area de notificació però no es veu l'icone.

---

