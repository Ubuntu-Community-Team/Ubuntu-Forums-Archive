---
title: "[SOLVED] openoffice : problemes després d'actualitzar"
date: 2008-12-02
forum: Catalan Team
---

### Post by jac2 on 2008-12-02
L'openoffice 3 en català m'anava de conya amb l'ubuntu 8.10 fins que des de la darrera setmana de novembre, després d'una actualització de l'ubuntu, no se'm permet obrir cap de les aplicacions openoffice.

Després de desinstal·lar-lo, quan l'intento instal·lar de nou amb "afegeix-elimina aplicacions", em surt:

"Aquesta aplicació té un conflicte amb un altre programa insta&#320;lat, que heu d'eliminar si voleu insta&#320;lar «openoffice.org-writer».
Utilitzeu el gestor de paquets Synaptic per solucionar aquest conflicte."

He aconseguit instal·lar-lo en anglès, però no en català. Si instal·lo el paquet d'idioma "openoffice.org-|10n-ca" o bé el "language-support-translations-ca" hem desinstal·la tot allò relacionat amb l'openoffice.

Com solucionar aquest conflicte paqueto-idiomàtic?
Gràcies

---

### Post by CarlesOriol on 2008-12-06
Fa uns dies que el paquet openoffice 3 que s'insta&#320;la via ppa està desactivat degut als problemes que han tingut. (probablement del que parles)

---

### Post by SiscoGarcia on 2008-12-08
> **CarlesOriol said:**
> Fa uns dies que el paquet openoffice 3 que s'insta&#320;la via ppa està desactivat degut als problemes que han tingut. (probablement del que parles)

Sembla que ja està resolt al launchpad, pel que acabo de veure-hi:

> **SiscoGarcia said:**
> Sembla que després d'un període de proves en què els repositoris del launchpad van deixar de funcionar, la cosa està solventada i ja és operatiu l'[enllaç al launchpad]("https://launchpad.net/~openoffice-pkgs/+archive"), no només per intrepid que és on hi ha hagut el problema, sinó que es pot fer servir el mateix enllaç per hardy. Llàstima que m'he actualitzat a intrepid ;)

---

### Post by jac2 on 2008-12-09
Moltes gràcies, companys.
Tal i com dieu, el problema ja l'han resolt.
En el meu cas, he fet el que ja havia provat fa dies i no funcionava... però ara sí:
Des de Synaptic:
-posar (cerca ràpida): openoffice
-marcar i eliminar tots els paquets openoffice (inclòs el  "openoffice.org-|10n-ca"). Aplicar els canvis.
-Marcar per instal·lar els paquets: "openoffice-writer, openoffice-calc, openoffice-impress i openoffice draw". A més del "openoffice.org-|10n-ca". Aplicar els canvis.

I ja està, ja torno a tenir l'Openoffice 3 amb l'intrepid i en català.

---

