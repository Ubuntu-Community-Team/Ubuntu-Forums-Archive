---
title: "No puc esborrar un programa del menú inicial"
date: 2010-08-09
forum: Catalan Team
---

### Post by Joan A. on 2010-08-09
Hola a tothom!

He intentat instal·lar **Itunes 9** amb **Wine** i no ha estat possible, per la qual cosa he esborrat la carpeta *.Wine* i he reiniciat la configuració amb *winecfg*. Després he esborrat tots els programes que s'havien instal·lat amb Itunes (Quicktime, etc.) i que estaven a *Aplicacions/Wine/Programes*.

A partir d'aquí ve el meu problema, perquè l'**Apple Software Update** no es pot eliminar. Vaig a *Sistema/Preferències/Menú Inici*, però quan li donc a eliminar, aquest no desapareix. Qualcú sap qualque manera per esborrar-lo? :(

Gràcies!

---

### Post by epileg on 2010-08-09
ves a la carpeta
> ~/.local/share/applications/wine/Programs
i elimina la carpeta de l'aplicació que no vols que t'apareixi al menú del Wine, i que prèviament has eliminat del teu sistema.

Salut,

---

### Post by Joan A. on 2010-08-09
M'ha anat perfecte! No era un problema greu, però me molesten aquestes tonteries.

Moltes gràcies!

---

