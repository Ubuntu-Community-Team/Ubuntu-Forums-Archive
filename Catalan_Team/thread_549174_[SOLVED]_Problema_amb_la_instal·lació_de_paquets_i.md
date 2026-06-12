---
title: "[SOLVED] Problema amb la instal·lació de paquets i sources.list"
date: 2007-09-12
forum: Catalan Team
---

### Post by Satboy on 2007-09-12
Hola a tothom,
 Un dia vaig instal.lar un programa per descomprimir arxius, però finalment no em va convèncer, i el vaig desinstal·lar.Des d'aleshores em surt un missatge allà on t'avisa de les noves actualitzacions que diu el següent:

 [B]"No es pot inicialitzar la informació del paquet

S'ha produït un problema irresoluble mentre s'inicialitzava la informació del paquet.

Informeu de l'error, referent al paquet update-manager, i adjunteu el següent missatge d'error:

'E:Línia 44 malformada en la llista de fonts /etc/apt/sources.list (analitzant dist), E:No s'ha pogut llegir la llista de les fonts.'"
[/B]

 També m'ha sortit el següent missatge:

 [B]"E: Línia 44 malformada en la llista de fonts /etc/apt/sources.list (analitzant dist)
E: No s'ha pogut llegir la llista de fonts.
Aneu al diàleg de repositoris per a corregir el problema.
E: _cache->open() failed, please report."[/B]

 Com ho puc sol.lucionar? Què és això del "diàleg de repositoris"? Tingueu en compte que sóc un usuari novell.

 Per cert, ja se sap en quina data sortirà el proper Ubuntu 7.10?

 Siau, i moltes gràcies!!

 David

---

### Post by pespin on 2007-09-12
Tal com diu l'error, tens un error de sintaxis o alguna cosa per l'estil al arxiu */etc/apt/sources.list*, que es on és guarden les URLs dels repositoris, que venen a ser els servidors d'on et baixes els paquets per instal·lar programes.

L'error potser bé donat de quan vas instal·lar el programa vas afegir un nou repositori.

La solució és revisar l'arxiu. Si no trobes l'error enganxa'n el contingut aquí. :)

---

### Post by papapep on 2007-09-12
Tal i com t'ha dit en Pespin, i el missatge ja t'explica, tens alguna línia malament al fitxer on li dius on ha d'anar ha buscar els paquets quan demanes instal·lar o actuatlizar-ne algun.

Al fitxer /etc/apt/sources.list, busca la línia 44 i fica-li un # al principi de tot. Això servirà per que el gestor de paquets no la consideri.

Després fes a un terminal:

```
sudo aptitude update
```

A veure si actualitza la base de paquets sense generar cap error.

Respecte la Gutsy Gibbon, dos punts d'informació:

[https://wiki.ubuntu.com/CatalanTeam/GrescaGutsy](https://wiki.ubuntu.com/CatalanTeam/GrescaGutsy)
[https://wiki.ubuntu.com/JosepS%c3%a0nchez/documentaci%c3%b3/Versions_Ubuntu](https://wiki.ubuntu.com/JosepS%c3%a0nchez/documentaci%c3%b3/Versions_Ubuntu)

---

### Post by Satboy on 2007-09-12
Hola companys,
 Moltísimes gracies a tots dos, ja he resolt el problema.Jo hi vaig voler "colar" una adreça per baixar-me el **NeroLinux**, però l'**Ubuntu** m'ha dit que res de res, un cop l'he esborrada, ja m'ha funciona a la perfecció.

 Moltes gràcies, de nou!

 Siau!;)

---

