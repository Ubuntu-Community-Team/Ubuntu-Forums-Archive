---
title: "disc dur extern i ext3"
date: 2007-06-14
forum: Catalan Team
---

### Post by bikerbaixcamp on 2007-06-14
Bones!

Avui m'he comprat una caixa de disc dur extern Conceptronic USB 2.0  CHD3UL i li he posat el disc dur que vaig posar fa un parell d'anys al meu ordinador d'abans. Aquest disc dur té 120gb. Doncs bé, primer ho he provat (tenia una partició NFTS amb Windows i una altra amb arxius fat32). Doncs bé, he vist que podia accedir-hi i tot. M'he disposat a formatejar, ja que vull utilitzar aquest disc dur extern per desar arxius (importants i no tan importants) com a còpia de seguretat de les meves coses. 
He formatejat amb l'editor de particions Gnome. Particions primàries totes, crec que ho he fet bé, no?. El primer inconvenient es que no podia formatejar amb nfts (alguna solució?, tampoc m'importa massa, però si es pot millor). I bé, he seguit més o menys com desitjava, he fet:
- 31gb amb fat32
- 61gb amb ext3
- 15gb amb ext3
- 8gb amb fat32

Doncs bé, les particions s'han fet correctament, i tot s'ha detectat perfectament. He provat d'escriure en les dues particions de fat32 i perfecte. Ara bé, amb l'ext3 he tingut problemes. Primer de tot m'ha sortit una carpeta anomenada "last+found" la qual em deia que no podia ni obrir ni esborrar perquè no tenia permisos. I l'altra cosa es que NO em deixa enganxar res a les particions ext3, no hi puc escriure. Com es soluciona això? i que coi és la carpeta aquesta de lost-found que m'ocupa espai i tampoc la puc borrar?

Moltes gràcies. ;)

---

### Post by patrickfromspain on 2007-06-14
sudo chmod 777 punt-de-montatge

---

### Post by papapep on 2007-06-14
> i que coi és la carpeta aquesta de lost-found que m'ocupa espai i tampoc la puc borrar?

 /lost+found

Aquí dins Linux guarda els fitxers que recupera després d’una caiguda del sistema per fallada o quan una partició s’ha desmuntat abans de tancar el sistema. Així es facilita la feina de recuperació de fitxers que, d’altra manera, s’haurien perdut.

Evidentment, com que formen part de l'estructura, diguem-ne, de seguretat de dades del sistema de fitxers, no  s'ha d'esborrar.

---

### Post by bikerbaixcamp on 2007-06-14
Ara haig de marxar, ho provaré el vespre..

Si faig això: "sudo chmod 777 punt-de-montatge" ho hauré de fer cada cop que posi el disc, o només una vega i prou? I per cert, el punt de muntatge és /sda /sdb (ara no recordo si és aquest concretament, però ja m'enteneu.. etc...?

Papapep, és a dir, que el lost+found puc fer que sigui una carpeta oculta i llestos, no? ;)

salut!

---

### Post by patrickfromspain on 2007-06-14
lost+found no pot ser una carpeta oculta, ja que pasaria a ser .lost+found, que no es el mateix.

El punt de montatge seria... /media/particio que sigui.

salut!

---

### Post by papapep on 2007-06-14
Biker, lost+found ni tocar-lo, això és el que volia dir l'explicació ;)

---

### Post by bikerbaixcamp on 2007-06-14
Això del lost+found ha quedat molt clar, gràcies. 

Demà al matí que avui no tinc temps provaré aquesta comanda del sudo. Per cert, això cal fer-ho sempre, o només amb un cop ja anirà sempre així ni que ho connecti de nou? I si s'ha fer cada cop hi ha alguna opció de boto dret + el que sigui o sempre cap a la consola?

Merci.

---

### Post by papapep on 2007-06-14
> Per cert, això cal fer-ho sempre, o només amb un cop ja anirà sempre així ni que ho connecti de nou?

Si et refereixes a:

> sudo chmod 777 punt-de-montatge

els permisos dels fitxers i directoris son estàtics, o sigui, que un cop canviats han de quedar com els deixes.
En conclusió, que si no hi ha cap altra cosa que et fa la punyeta fent-ho un cop ja t'hauria de funcionar sempre més bé.

---

### Post by bikerbaixcamp on 2007-06-15
Sembla que la cosa vagi bé, gràcies.

---

### Post by AlexMuntada on 2007-06-16
> **bikerbaixcamp said:**
> ... NO em deixa enganxar res a les particions ext3, no hi puc escriure. Com es soluciona això?

Les particions ext3 utilitzen un sistema de permisos de tipus UNIX (propietari, grup i altres) i després de crear la partició, només l'usuari root té permisos per escriure-hi.

Personalment, enlloc de fer un «sudo chmod 777 punt-de-muntatge» et recomano que facis una altra cosa:

```
sudo mkdir punt-de-muntatge/nomusuari
sudo chown nomusuari:grupusuari punt-de-muntatge/nomusuari
```

Així ja tens un directori sobre el qual tens permisos d'escriptura i lectura però protegint l'arrel del disc.  A més, si vols pots crear diferents directoris per a d'altres usuaris i cadascú tindrà permisos pel seu.  Els permisos 777 indiquen que tothom pot escriure i modificar l'arrel del disc i això pot provocar greus problemes de seguretat.

---

### Post by bikerbaixcamp on 2007-06-16
> **AlexMuntada said:**
> Les particions ext3 utilitzen un sistema de permisos de tipus UNIX (propietari, grup i altres) i després de crear la partició, només l'usuari root té permisos per escriure-hi.

Personalment, enlloc de fer un «sudo chmod 777 punt-de-muntatge» et recomano que facis una altra cosa:

```
sudo mkdir punt-de-muntatge/nomusuari
sudo chown nomusuari:grupusuari punt-de-muntatge/nomusuari
```

Així ja tens un directori sobre el qual tens permisos d'escriptura i lectura però protegint l'arrel del disc.  A més, si vols pots crear diferents directoris per a d'altres usuaris i cadascú tindrà permisos pel seu.  Els permisos 777 indiquen que tothom pot escriure i modificar l'arrel del disc i això pot provocar greus problemes de seguretat.

Gràcies per la recomenació; però crec que no ho necessito, o potser sI?
M'explico, aquest disc és extern, i sempre està desconectat de l'ordinador menys quan vull fer còpies de seguretat dels meus arxius. I tampoc no ho tocarà cap més persona. Així que no li veig cap problema, no? O potser no he entès el que em vols dir?

;)

---

### Post by AlexMuntada on 2007-06-16
En aquest context no és especialment greu, però és un mal costum tenir permisos massa laxos a menys que sigui del tot imprescindible.  De fet, fixeu-vos que els arxius que creeu dins del disc no tenen permisos d'escriptura per a tothom, el problema només el teniu a l'arrel de la partició.

Resumint, molt de compte amb els «chmod 777».  Res més.

---

### Post by bikerbaixcamp on 2007-06-16
> **AlexMuntada said:**
> En aquest context no és especialment greu, però és un mal costum tenir permisos massa laxos a menys que sigui del tot imprescindible.  De fet, fixeu-vos que els arxius que creeu dins del disc no tenen permisos d'escriptura per a tothom, el problema només el teniu a l'arrel de la partició.

Resumint, molt de compte amb els «chmod 777».  Res més.

;)

---

