---
title: "Canviar l'idioma a KBruch i KGeography"
date: 2010-02-22
forum: Catalan Team
---

### Post by mrc2407 on 2010-02-22
Hola de nou.

He instal·lat els programes KBruch i KGeography a Ubuntu 9.10 i em surten en anglès, tot i que la seva pàgina al Launchpad diu que està traduït al català (al primer hi falten 27 cadenes, el segon està al 100%).

Els dos programes tenen una opció a Help -> Switch Application Language que en toria hauria de permetre canviar l'idioma, però només puc seleccionar American English en els dos programes. Algú sap com puc canviar l'idioma?

Gràcies!

---

### Post by oriolsbd on 2010-02-22
Hola,

Segurament són els primers programes de KDE que t'has instal·lat a Ubuntu. Els programes de KDE tenen les seves traduccions en paquets específics, que no s'instal·len si no hi tens cap programa de KDE instal·lat.

Per a instal·lar-te aquests paquets, pots anar a "Sistema>Administració>Suport d'idioma". En principi, t'hauria de dir que no tens complet el suport d'idioma en català (perquè ara sí detecta que necessites els paquets d'idioma català per a KDE). Acceptes, i t'ho instal·larà sol.

Si no t'ho instal·la sol, ves al Synaptic i instal·la't directament els paquets en qüestió, que són:
language-pack-kde-ca
language-pack-kde-ca-base

Salut!

---

### Post by mrc2407 on 2010-02-22
@oriolsbd:

Moltíssimes gràcies! Ja funciona :)

---

### Post by orestesmas on 2010-02-23
> **mrc2407 said:**
> Hola de nou.

He instal·lat els programes KBruch i KGeography a Ubuntu 9.10 i em surten en anglès, tot i que la seva pàgina al Launchpad diu que està traduït al català (al primer hi falten 27 cadenes, el segon està al 100%).


De cara al futur no et refïis de la informació que dóna el Launchpad sobre el percentatge de traducció de les aplicacions KDE.

Nosaltres traduïm el KDE directament al seu lloc original (tècnicament es coneix com *upstream*), i allí ho tenim tot traduït. Si després els d'Ubuntu tenen problemes i errors en importar aquestes traduccions és molt lamentable, però no es pot atribuir al projecte KDE. De fet, i em dol dir-ho, Ubuntu és una de les pitjors distribucions que pots escollir si vols gaudir d'un KDE ben "afinat". També és cert que la situació ha anat millorant darrerament, però encara falta per arribar al nivell d'integració del Gnome (en Ubuntu, clar :-).

Tornant a les traduccions que esmentaves, la pàgina que cerques correspon al mòdul **kdeedu** i la pots consultar [aquí]("http://l10n.kde.org/stats/gui/stable-kde4/team/ca/").

---

### Post by mrc2407 on 2010-02-23
Gràcies per la informació, orestesmas :)

---

