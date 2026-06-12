---
title: "[RESOLT] Canviar llenguatge sense reiniciar - Kmediafactory"
date: 2007-05-22
forum: Catalan Team
---

### Post by manelolesa on 2007-05-22
](*,)

Companys, el Kmediafactory no funciona si el sistema no esta configurat amb angles US.

La  variable  LANG, te que estar establerta amb un valor igual a  "en_US.UTF-8".

En Català aquesta variable es "ca_ES.UTF-8".

Si canvio d’idioma  des de Sistema -  Administració - Suport de Idioma, tinc que reiniciar el Sistema per que s'apliquin els canvis.

Sabeu si existeix alguna manera de canviar temporalment el LANG, sense tenir que reiniciar o llançar el programari amb paràmetres o script.

Salut i gracies


Manel
):P

---

### Post by orestesmas on 2007-05-22
Uses Gnome o KDE?

En KDE (configurat en català) el programa que esmentes em funciona bé, tot i que en anglès perquè ningú no l'ha traduït encara.

A banda d'això, en cap cas m'he trobat mai amb que cal reiniciar el sistema perquè s'apliquin els canvis d'idioma. Com a molt, cal reiniciar les aplicacions engegades en aquell moment.

---

### Post by manelolesa on 2007-05-23
El problema el tinc tant en Gnome com amb KDE, ja ho vaig provar.
 
Al intentar crear o modificar Menús em surt un error del imagemagik i en un foro parlaven que el LANG tenia que estar en Angles. Ho vaig provar i va funcionar correctament.
 
[I]ImageMagick yields an error:
Non-conforming drawing primitive definition `rectangle'
 
Setting LANG to English fixes the problem.
 
I think you should change the LANG variable. But simply unsetting it does not work. My default is "de_DE.UTF-8".
If I unset the variable, the strings are not rendered correctly anymore. I have to set LANG to "en_US.UTF-8" to make ImageMagick work and render the strings properly[/I]
 
 
L' idioma si que el puc canviar sense reiniciar el sistema, però la variable $LANG, no canvia fins que no reinicio.
 
Salut
 
Manel

---

### Post by manelolesa on 2007-05-23
SOLUCIONAT.

Despres de instal.lar mes eines per el tema de tractament de DVD ( Devede, QDVDAUTHOR i algun mes ) el kmediafactory funciona correctament, penso que podria ser la versió de la llibreria del Imagemagik.

Salut i gracies

---

### Post by orestesmas on 2007-05-23
Això no és del tot cert. Pots canviar la variale d'entorn "LANG" sense reiniciar si ho fas en el context d'un terminal. Obre un terminal i tecleja:

export LANG=en_US.UTF8
kmediafactory

o encara més senzill: tot a la mateixa línia sense l'export:

LANG=en_US.UTF-8 kmediafactory

El programa kmediafactory s'executa amb el LANG al valor que li acabes de posar. en el primer cas això només té efecte per aquella sessió de terminal, i en el segon cas únicament per l'ordre kmediafactory.

Això ho pots posar en un script d'inici o fins i tot als paràmetres de l'aplicació quan l'executis des d'un menú.

---

