---
title: "No puc descarregar updates"
date: 2009-05-07
forum: Catalan Team
---

### Post by Jayhawker on 2009-05-07
M'ha aparegut un senyal de direcció prohibida i si el clicko em diu que he instal·lat paquets que no han trobat dependències. La qüestió és que quan intento obrir el gestor de paquets per mirar de solucionar la cosa em surt un cartellet que diu: 

[COLOR="DarkRed"][B]E: El tipus <debsrc> no és conegut en la línia 57 de la llista de fonts /etc/apt/sources.list
E: The list of sources could not be read.
Anar al diàleg de repository (repository dialog) per corregir el problema.
E:_cache- open() failed.[/B][/COLOR]

Quan tanco aquest cartellet se'm tanca el Gestor, de tal manera que no puc mirar de solucionar res i no puc descarregar updates ni programes. 

Sisplau, hi hauria alguna manera de solucionar això? No sé el que són repositoris per començar i per tant no puc solucionar el problema. 

Moltes mercès

---

### Post by Daerun on 2009-05-07
Doncs el propi missatge crec que et diu que el fitxer /etc/apt/sources.list té algun problema. De primer podries anar al menú Sistema > Administració > Fonts de programari y mirar la pestaña "programari de tercers" a veure si hi veus res d'estrany; és possible que hi afegissis un repositori nou de manera incorrecta i per això et surt l'error.
Si no, ja seria cosa de mirar-se el propi fitxer sources.list, i aqui ja caldria que algú més entès hi digués la seva.

---

### Post by torracastanyes on 2009-05-07
Una altra cosa. Si has instalat paquets, d'on els has tret?

---

### Post by papapep on 2009-05-07
> Sisplau, hi hauria alguna manera de solucionar això? No sé el que són repositoris per començar i per tant no puc solucionar el problema.

Tot tingués una solució tan simple (el teu desconeixement, vull dir). A llegir toquen:

[https://wiki.ubuntu.com/CatalanTeam/Recursos/PMFUbuntuCat#Gesti%C3%B3%20de%20paquets%20(programes](https://wiki.ubuntu.com/CatalanTeam/Recursos/PMFUbuntuCat#Gesti%C3%B3%20de%20paquets%20(programes))

---

### Post by Jayhawker on 2009-05-08
> **torracastanyes said:**
> Una altra cosa. Si has instalat paquets, d'on els has tret?

Si, em va passar quan vaig descarregar algun paquet, ara no me'n recordo bé però em sembla que tenia alguna cosa a veure amb drivers d'imatge i so. Ja que no sóc cap expert en Linux, procuro sempre descarregar-los des del gestor de paquets.:)

---

### Post by Jayhawker on 2009-05-08
> **Daerun said:**
> Doncs el propi missatge crec que et diu que el fitxer /etc/apt/sources.list té algun problema. De primer podries anar al menú Sistema > Administració > Fonts de programari y mirar la pestaña "programari de tercers" a veure si hi veus res d'estrany; és possible que hi afegissis un repositori nou de manera incorrecta i per això et surt l'error.
Si no, ja seria cosa de mirar-se el propi fitxer sources.list, i aqui ja caldria que algú més entès hi digués la seva.

Moltes mercès pel teu suggeriment. Si hi hagués cap problema, què hi hauria de constar? Només veig que tinc repetit dos cops, com a instal·lat, [COLOR="DarkRed"]**[http://packages.medibuntu.org/hardy](http://packages.medibuntu.org/hardy) free non-free**[/COLOR], però no hi ha cap senyal d'error visible o que jo pugui percebre com a tal. 

Com desinstal·lo el que perjudica? COm entro a la source.list?

Consultant directament la carpeta etc, veig dos fitxes amb un senyal d'error (el senyal de transit de direcció prohibida). Es diuen secring.gpg i trustdb.gpg. VOl dir alguna cosa. Com e spot intervenir-hi per solucionar-ho?

Merci de nou

---

### Post by Jayhawker on 2009-05-08
> **papapep said:**
> Tot tingués una solució tan simple (el teu desconeixement, vull dir). A llegir toquen:

[https://wiki.ubuntu.com/CatalanTeam/Recursos/PMFUbuntuCat#Gesti%C3%B3%20de%20paquets%20(programes](https://wiki.ubuntu.com/CatalanTeam/Recursos/PMFUbuntuCat#Gesti%C3%B3%20de%20paquets%20(programes))

Mercès pel link.

---

### Post by papapep on 2009-05-08
> Com desinstal·lo el que perjudica? COm entro a la source.list?

Fes a un terminal:

```
cat /etc/apt/sources.list
```

i enganxa aquí el que surti.

---

### Post by Jayhawker on 2009-05-08
> **papapep said:**
> Fes a un terminal:

```
cat /etc/apt/sources.list
```

i enganxa aquí el que surti.

mercès pel teu interès. Dispensa però en dir "enganxar", a on i amb quin objectiu, sisplau?

---

### Post by quitus on 2009-05-08
ves a aplicacions/accessoris/terminal s'obrira una finestra en la que podràs escriure i has de escriure el que t'ha dit en papapep, et recomano que copiïs i enganxis l'ordre, ja que els espais son importants. Després  "intro" i a veure que passa.

salut

---

### Post by papapep on 2009-05-08
> Dispensa però en dir "enganxar", a on

Enganxar, aquí, al fòrum. Per que poguem veure el contingut del teu sources.list i intentar trobar el problema de sintaxi que no acabes de resoldre.


> i amb quin objectiu, sisplau

Bàsicament, ajudar-te :)

---

