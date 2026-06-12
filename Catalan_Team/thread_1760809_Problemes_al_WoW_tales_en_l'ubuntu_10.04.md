---
title: "Problemes al WoW tales en l'ubuntu 10.04"
date: 2011-05-17
forum: Catalan Team
---

### Post by Skrack on 2011-05-17
Estimats ubuntaires,
aquesta setmana, ara fa poc, va caure a les meves mans una còpia del World of Warcraft Tales, que usa la versió del Wrath of the Lich King del WoW. Jo, il·lús de la vida, vaig creure que tot solet i amb l'ajuda d'algunes guies de solució de problemes d'aquestes que hi ha per internet vaig rebre'l amb els braços oberts.

La còpia aquesta, ja preparada per a jugar en windows, la vaig modificar segons el que deien certes guies perquè s'iniciés amb el wine i l'OpenGL. Doncs va resultar que quan creia que ja el tenia a punt per a jugar, l'executo (de diverses maneres diferents) i veig que em surt un error amb lletres descomunals (ja que no sé per què em canviava la configuració de la pantalla a 800x600) que em diu:

ERROR # 132 (0x85100084) Fatal Exception
Program:  c:\Program Files\World of Warcraft\wow .exe
Exception: 0xC0000005 (ACCESS_VIOLATION) at 0073:376CB490

a més d'una altra finestra amb tant de text que si el fiqués aquí colapsaria el fòrum.

Per tant us demanaria si us plau, que em donguéssiu un cop de mà tant sigui per ajudar-me a mi i a els altres que llegeixin aquest post. I us agrairia que no trigueu massa, ja que tots els meus companys ja han començat i m'estic quedant enrere.

Moltes gràcies
Atentament 
Skrack

---

### Post by wgarcia on 2011-05-17
En aquest fòrum en anglès:

[http://ubuntuforums.org/showthread.php?t=822943](http://ubuntuforums.org/showthread.php?t=822943)

diuen que és un problema de targeta gràfica i proveeixen alguns suggeriments i altres enllaços.

---

### Post by Skrack on 2011-05-17
Gràcies wgarcia, segons he pogut entendre del fil que m'has passat, i com molt bé has dit , sembla un problema de la tarjeta gràfica. 

Per intentar-ho arreglar, he seguit alguns links que hi havia al fil i he buscat pel google i he arrivat a la conclusió que no tinc els drivers de la tarja gràfica instalats. no he aconseguit trobar com posar-los. La tarjeta que sembla ser que tinc és la seguent:

82945G/GZ Integrated Graphics Controller

Si tu o algun altre ubuntaire expert em pogués ajudar a trobar els drivers que nessecito i em digués com posar-los em faria un gran favor, i a més probablement se'm solucionés el problema. 

Cal que digui que he anat a Sistema->Administració->Controladors de maquinari  i no m'ha sortit res.

Moltes gràcies
Atentament

Skrack

---

### Post by wgarcia on 2011-05-17
En principi la targeta gràfica que tens és d'Intel i no necessita controladors propietaris per fer tots els efectes, Intel proveeix tots els seus controladors en forma oberta i estan integrats al nucli de linux. 

Ara bé, no sé si té suficient capacitat gràfica per córrer wine i el joc que vols fer servir. 

Has vist aquesta pàgina:

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

---

### Post by Skrack on 2011-05-18
Aquesta web que dius ja l'havia vista, i me n'he llegit un bon tros. Però (almenys pel que he vist) no em serveix, ja que el meu WoW tales es copiat d'un windows d'un company meu, i aguí no me'n parla.

A més, tot llegint el fil que m'havies passat, veig veure que el problema se li havia solucionat tornant-lo a instal·lar. I ara no sé què fer. Ho borro tot, i l'instal·lo un altre cop? (com volguent dir el copio un altre cop); segueixo intentant arreglar aquest?... 
Vaig ben perdut.... 

Agrairia algun consell de cap a on tirar.

Moltes gràcies, 

Skrack

---

### Post by thepiratefish on 2011-05-19
I wish I could read this in English because I get a feeling that its the same problem I'm having haha

---

