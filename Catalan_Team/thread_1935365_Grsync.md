---
title: "Grsync"
date: 2012-03-04
forum: Catalan Team
---

### Post by rosa d'abril on 2012-03-04
Em vaig instal·lar aquest programa per tal de sincronitzar tot el que vaig guardant durant la setmana al Pendrive amb els corresponents arxius al disc dur. El programa em va bé però no sé com dir-li que no em sincronitzi algunes de les carpetes del llapis.
Amb el Windows feia servir el SyncBack que sí em pemetia definir filtres.

---

### Post by wgarcia on 2012-03-04
La millor eina que (almenys jo) conec per sincronitzar fitxers entre sistemes de fitxers diferents és "unison" (fins i tot remotament, jo el faig servir per tenir sincronitzats l'ordinador de sobretaula de la feina i el portàtil, o tot i que no l'he provat entre plataformes diferents, per exemple entre Linux i Windows). Jo el faig servir des de la línia de comandes, però hi ha una interfície gràfica que és força intuïtiva i et permet escollir quines carpetes vols sincronitzar i moltes altres coses avançades més. 

Entra "unison" al Centre de Programari i t'oferirà dues versions, pots instal·lar qualsevol d'elles (sols és important això si estàs sincronitzant remotament entre dos sistemes, ja que han de tenir instal·lades exactament la mateixa versió, però no és el teu cas). 

Després inicies l'aplicació entrant "unison" de la manera habitual i et deixarà definir quines carpetes vols sincronitzar i em sembla que també les excepcions.

---

### Post by rosa d'abril on 2012-03-04
Gràcies, ho provaré.
Ets com una fada madrina.

---

### Post by wgarcia on 2012-03-04
A la nit em transformo en una granota...

---

### Post by rosa d'abril on 2012-03-05
Ahir em vaig instal·lar l'Unison i ja el vaig fer servir. Té un entorn gràfic per a "dummies" que el fa molt accessible. Em va anar perfecte i ja vaig desinstal·la el Grsync.
Una pregunta més: algun suggeriment sobre com aprendre les ordres necessàries per a fer anar l'Ubuntu des del terminal? (Per a *dummies*, si us plau)

---

### Post by jaumell on 2012-03-05
Bon dia,

Tot i que ja he vist que el tema consta com a solucionat, voldria comentar-te que jo vaig tenir força problemes amb Unison i precisament el vaig substituir per Grsync.

Faig servir Grsync exactament pel mateix que tu i cap problema, però no puc ajudar-te en el tema de l'exclusió. L'únic que se m'acut és que creis una nova sessió que inclogui només els directoris que vulguis sincronitzar, enlloc de tot el usb.

En el meu cas, Unison em donava força problemes al sincronitzar. No puc ser més explícit perque el vaig canviar abans de la última LTS i no en recordo detalls, però et recomanaria que facis còpia de seguretat dels arxius abans de provar-lo, no sigui que et desapareguin...

---

### Post by wgarcia on 2012-03-05
Jo en canvi fa anys que faig servir l'unison i cap problema. A mi em fa molt bon servei quan hi ha conflictes, és a dir fitxers que han canviat de forma diferent entre les carpetes que sincronitzes, perquè és molt curós en no perdre cap canvi que hagis pogut fer en forma diferent entre els fitxers.

Ara bé, no és una eina de còpia de seguretat sinó de sincronització. És a dir si esborres un fitxer a la carpeta A, i sincronitzes amb la carpeta B, òbviament te l'esborrarà a B, perquè has demanat la sincronització. I el mateix a l'inrevés (si esborres a B, esborrarà a A). 

Per fer còpies de seguretat s'han de fer servir altres eines i una altra metodologia (incremental, etc.).

---

### Post by rosa d'abril on 2012-03-05
Pel que puc dir de la meva experiència l'Unison em sembla molt més complet que el Grsync, per això no vaig dubtar a substituir-lo. Si tinc algun problema inesperat i greu ja ho faré saber al fòrum.

---

