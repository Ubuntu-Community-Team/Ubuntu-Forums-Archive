---
title: "Recuperar configuracio anterior"
date: 2010-02-08
forum: Catalan Team
---

### Post by pserra on 2010-02-08
Hola companys,
al acer ONE que anava de maravella amb el 9.10 Remix, l'altre dia  em va sortir el  gestor d'actualitzacions i em demanava d'actualitzar entre altres coses el Kernel per un****.19  (estava al ****17), vaig acceptar.**PUTADA!!**
He perdut la rapidessa, configuracio  pantalla...i quan  engego em surt un error respecte els grafics.... 
El kernel l'he borrat per el synaptic,però hi ha alguna manrera de recuperar la configuració anterior??

---

### Post by sordoman on 2010-02-08
Ostres tu!!!

Acabo de tornar de refer la mateixa desfeta al pc del sogre ;)

El que m'ha tocat fer (no vol dir que sigui el correcte pero finalment ha funcionat)

-Primer reinstalar del drivers de la targeta de video

-reiniciar y arrencar com a root amb mode "recuperació", un cop "loguejat" ```
aptitude install -f
``` el retorn del cual m'ha donat molts errors, sobretot del firefox-3.5

-com a consell de l'ordre anterior ```
dpkg --configure -a
```
ho ha deixat tot ok, excepte el firefox.

-Per últim m'ha tocat desinstalar el firefox amb "purge" y també el "xulrunner" el ke ha desinstalat desde "ubuntu-desktop" fins no se cuantes coses mes, i finalment torna-ho a instalar.(quant instales el firefox ja instala el xulrunner, només quedaria reinstalar el ubuntu-desktop)

Despres tot fantàstic fluid y ràpid

espero que et serveixi

Sort

P.D: a veure si algu sap algun altre mètode més facil, curt i elegant (aprenent en pràctiques) ;)

---

### Post by pserra on 2010-02-08
> **sordoman said:**
> Ostres tu!!!

Acabo de tornar de refer la mateixa desfeta al pc del sogre ;)

El que m'ha tocat fer (no vol dir que sigui el correcte pero finalment ha funcionat)

-Primer reinstalar del drivers de la targeta de video

-reiniciar y arrencar com a root amb mode "recuperació", un cop "loguejat" ```
aptitude install -f
``` el retorn del cual m'ha donat molts errors, sobretot del firefox-3.5

-com a consell de l'ordre anterior ```
dpkg --configure -a
```
ho ha deixat tot ok, excepte el firefox.

-Per últim m'ha tocat desinstalar el firefox amb "purge" y també el "xulrunner" el ke ha desinstalat desde "ubuntu-desktop" fins no se cuantes coses mes, i finalment torna-ho a instalar.(quant instales el firefox ja instala el xulrunner, només quedaria reinstalar el ubuntu-desktop)

Despres tot fantàstic fluid y ràpid

espero que et serveixi

Sort

P.D: a veure si algu sap algun altre mètode més facil, curt i elegant (aprenent en pràctiques) ;)

Al final l'he pogut solventar....
he trobat aquest enllaç
[http://otroblogmas.com/configurar-la-tarjeta-grafica-intel-gma500-en-ubuntu-9-10-despues-de-las-actualizaciones-del-kernel/](http://otroblogmas.com/configurar-la-tarjeta-grafica-intel-gma500-en-ubuntu-9-10-despues-de-las-actualizaciones-del-kernel/)


i després de la espera de uns minuts s'ha arreglat tot 'solet'
el que encara em queda pendent es el brillo de la pantalla que per defecte em surt al màxim i les tecles (fn +/-) no fan rés...

Ara la pregunta que m'agradaria que els experts m'aconsellessin...un 'novato' com sap si l'actualització de un kernel li pot suposar problemes?? o el més recomenable es quan surti una versio nova de ubuntu canviar-lo llavors??

Merci

---

### Post by pserra on 2010-02-10
Rectifico,
el post anterior em va solventar la configuració  de pantalla,
pero el sistema anava lent...millor aquest enllaç:
[http://www.ubuntu.org.uy/main/?q=node/2063](http://www.ubuntu.org.uy/main/?q=node/2063)
seguint els passos m'ha instalat el kernel actual.....-19
i va el ubuntu MOOLT RÀPIT!!!
Sort

---

