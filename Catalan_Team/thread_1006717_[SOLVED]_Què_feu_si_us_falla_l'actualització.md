---
title: "[SOLVED] Què feu si us falla l'actualització?"
date: 2008-12-09
forum: Catalan Team
---

### Post by Tomàs M. on 2008-12-09
Hola,
abans d'ahir vaig intentar actualitzar a 8.10 (8.04 de 32 bits amb Gnome), però a banda d'algun altre error que no recordo i dos o tres missatges preguntant si reemplaçar algun fitxer de configuració modificat (en aquests casos no tinc mai gaire clar què fer, i algun cop quan he dit "mostra les diferències entre fitxers", després no he sabut com escollir l'opció desitjada; normalment acabo posant la versió més nova i ja configuraré més endavant...), vaig acabar obtenint aquests dos: ```
S'ha produït un error en carregar o desar informació de la configuració per a frontend. Alguns paràmetres de la configuració no funcionaran correctament.
``` i ```
No s'han pogut instal·lar les actualitzacions.
S'interromprà l'actualització. Pot ser que el sistema hagi quedat en un estat inutilitzable. S'executarà una recuperació (dpkg --configure -a) immediatament.
```
Tot i que vaig poder arrencar amb aparent normalitat, com que no ho acabava de veure clar, vaig decidir tirar enrera recuperant un backup de la partició del sistema del dia anterior fet amb [ubackup]("http://ubuntuforums.org/showthread.php?t=613462&page=2") (abans QuickStart) que ja m'ha salvat la vida unes quantes vegades.
Bé, tot plegat va ser una mica desastrós, perquè em vaig quedar sense poder iniciar sessió, ja que petava amb un [missatge conforme la sessió havia durat menys de 10 segons]("http://ubuntuforums.org/showthread.php?t=904081") i això:
```
/etc/gdm/Xsession: Beginning session setup...
Setting IM troug im-switch for locale=ca_ES.
Start IM through /etc/X11/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
**Message: Another GPG agent already running
```
Suposo que com a conseqüència d'algun fitxer de 8.10 que el *restore* no havia esborrat.
Al final i després del malson fent-me recordar temps passats de la meva època fosca, n'he sortit reinstal·lant amb un CD de 8.04 i a partir d'aquí sí que he pogut recuperar el backup sense problemes (bé, de moment cap altre que no s'hagi solucionat reconfigurant l'openssh i l'exim4)
Les preguntes concretes són:
-què hauria d'haver fet, exactament?
-tinc més possibilitats d'èxit actualitzant des de cd (per cert, amb la desktop-i386 de la 8.10 no m'arrenca ni amb mode segur, per tant si mai volgués fer instal·lació des de 0, igualment necessitaria l'alternate, no?
-ara m'arrenca amb un kernel antic. Si volgués arrencar amb un de més nou (de moment no ho penso tocar, doncs ja he xafat prou coses i resulta que amb el 2.6.24-19 no tinc el [bug del micròfon]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/212378") i ara em funciona) :lolflag: ; ho podria fer editant el menu.lst mantenint el codi actual de root=UUID=?

Gràcies per llegir tot el totxo...

---

### Post by papapep on 2008-12-10
> Tot i que vaig poder arrencar amb aparent normalitat, com que no ho acabava de veure clar,

Però si, inicialment, funcionava correctament, per què no et vas esperar a verificar que tot anava i ja està?? sempre tenies la carta de recuperar la còpia de seguretat....

> Les preguntes concretes són:
-què hauria d'haver fet, exactament?

Esperar-te.

> -tinc més possibilitats d'èxit actualitzant des de cd (per cert, amb la desktop-i386 de la 8.10 no m'arrenca ni amb mode segur, per tant si mai volgués fer instal·lació des de 0, igualment necessitaria l'alternate, no?

Si preguntes, que no ho acabo d'entendre, si tens més probabilitat d'èxit actualitzant des de CD que des de xarxa, doncs no. 

> -ara m'arrenca amb un kernel antic. Si volgués arrencar amb un de més nou (de moment no ho penso tocar, doncs ja he xafat prou coses i resulta que amb el 2.6.24-19 no tinc el bug del micròfon i ara em funciona) ; ho podria fer editant el menu.lst mantenint el codi actual de root=UUID=?

Instal·lar un nucli nou no t'esborra un d'antic, amb el qual no té massa sentit no instal·lar-lo per "por a xafar res". Si no va, edites, com tu bé dius, el menu.lst i punt. I sí, afegint una(es) línia(es) amb el nou nucli i respectant la UUID del disc dur d'arranc, t'hauria de funcionar per afegir-ho posteriorment.

---

### Post by Tomàs M. on 2008-12-10
> **papapep said:**
> Si preguntes, que no ho acabo d'entendre,..
Sí, perdó; es veu que a aquella hora ja tenia la neurona cansada i em vaig deixar un parèntesi.
Moltes gràcies pels teus sempre savis consells, papapep. Els tindré en compte al proper intent.

---

