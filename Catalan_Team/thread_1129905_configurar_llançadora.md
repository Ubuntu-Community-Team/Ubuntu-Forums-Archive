---
title: "configurar llançadora?"
date: 2009-04-19
forum: Catalan Team
---

### Post by Miquel Ubuntero on 2009-04-19
Bones.
Tinc un pc amb Ubuntu 7.10 configurat amb una resolució de pantalla 800x600.
Alguns jocs requereixen 1024x768. Voldria saber si és pot crear una llançadora a un joc determinat configurant la resolució de pantalla que li cal.
Moltes gracies.

---

### Post by tanreb20 on 2009-04-19
Que jo sàpiga no es pot fer...

El que deus poder fer és un script que primer et canvii la resolució i després llençar el joc.

No sé com es deu fer aixo de canviar la resolució... Suposu que amb el xrandr!

---

### Post by Miquel Ubuntero on 2009-04-19
SOLVED!
He creat un fitxer nou amb les següents ordres:

xrandr -s 1024x768
wesnoth
xrandr -s 800x600

El resultat bo. Canvia la reso&#320;lució, carrega el joc i en acabar deixa la reso&#320;lució inicial.
Moltes gracies per la orientació. :D

---

