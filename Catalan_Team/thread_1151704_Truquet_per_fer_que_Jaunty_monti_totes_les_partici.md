---
title: "Truquet per fer que Jaunty monti totes les particions al inici"
date: 2009-05-07
forum: Catalan Team
---

### Post by sianeu on 2009-05-07
Ubuntu Jaunty tampoc no munta d'arrancada les particions que no formen part del seu sistema de fitxers, tant si son ntfs fat32 o ext3. Les deixa a Llocs>medis extraibles, i es monten al moment que es clica en elles.

He trobat per internet una manera molt simple de fer que es muntin TOTES, (i aquest es l'únic desavantatge que li he torbat, que han de ser totes sí o sí) al iniciar el sistema.

Per aconseguir-ho només cal fer un lleuger canvi en les polítiques de maneig de volums interns per part del servei HAL. Fem:

sudo gedit /etc/hal/fdi/policy/preferences.fdi

Busquem una liniea que diu: 
 <merge key="storage.automount_enabled_hint" type="bool">false</merge>. Canviem el >false< per >true<, guardem i sortim. Ara, al pròxim inici, carregarà totes les particions i les deixarà muntades i amb una icona a l'escriptori.
 
Salut

---

### Post by kukat on 2009-05-07
Gràcies!!!!!!!!!
Era una de les coses que tenia pendents!!!
Salut!

---

### Post by iSoc on 2009-05-17
Moltes Gràcies. Em serà molt útil.
Un Salut i força Barçaa...

---

### Post by PatrickVogeli on 2009-05-17
editar l'fstab ja no es porta? ;)

---

### Post by CarlesOriol on 2009-05-18
Això automonta el amb el gnome-volume-manager. Però per als altres escriptoris cal modificar el fstab.

De fet és millor fer-ho sols al fstab com diu en Patrick.

---

### Post by albert-I on 2009-08-10
Suposo que hi ha un alentiment de l'engegada?

---

