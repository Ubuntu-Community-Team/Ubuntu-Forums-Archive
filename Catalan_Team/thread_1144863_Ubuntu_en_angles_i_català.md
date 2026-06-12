---
title: "Ubuntu en angles i català"
date: 2009-05-01
forum: Catalan Team
---

### Post by planera on 2009-05-01
Hola!
Ahir em vaig reinstal.lar l'Ubuntu i ho vaig fer des d'un cd antic que tenia, que no se per quin motiu no està complet en català.
Les altres vegades ho havia resolt des de suport d'idioma, i així ho vaig fer. Però també vaig desactivar l'angles.
Però segueix sortint.me mig en català i mig en anglès (fins i tot la data em surt en angles).
M'ha semblat que mentre "s'apliquen els canvis d'idioma" (que realment no s'apliquen) surt algun tipus d'error, pero va molt ràpid i quan acaba em tanca la  finestra, així que nomès tinc aproximadament un segon per a llegir-ho. 
Com ho podria resoldre?
Gracies!

---

### Post by RainCT on 2009-05-02
Prova en una terminal:

```
sudo aptitude install language-pack-ca language-support-ca
```

I comprova també la sortida de:

```
locale
```

---

### Post by planera on 2009-05-03
Gràcies per contestar. Ara acabo de provar el que m'havies dit, pero em surt:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = "ca_ES.UTF-8LANGUAGE=ca_ES.UTF-8LC_TYPE=ca_ES.UTF-8LC_MESSAGES=ca_ES.UTF-8LANG=ca_ES.UTF-8",
    LANG = "ca_AD.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

I no tinc ni idea que vol dir, ni com solucionar-ho... Alguna suggerencia?

---

### Post by RainCT on 2009-05-04
I la sortida de l'ordre «locale»?

---

### Post by planera on 2009-05-04
Acabo de provar i em surt:

LANG=C
LC_CTYPE=C
LC_NUMERIC=C
LC_TIME=C
LC_COLLATE=C
etc, etc

Pero com no es el que em sortia ahir, he tornat a desinstal.lar el catala des del suport d'idioma i ho he tornat a instal.lar tal i com em vas dir. 
He reiniciat i m'he tornat a posar trista al veure que a la pantalla per a escollir usuar seguia en angles. He anat a les opcions i em deixava canviar l'idioma (que ahir no podia). Ho he canviat, i ara va perfecte.
Em surt:

LANG=ca_ES.UTF-8@valencia
LC_CTYPE="ca_ES.UTF-8@valencia"
LC_NUMERIC="ca_ES.UTF-8@valencia"
LC_TIME="ca_ES.UTF-8@valencia"
LC_COLLATE="ca_ES.UTF-8@valencia"
LC_MONETARY="ca_ES.UTF-8@valencia"
LC_MESSAGES="ca_ES.UTF-8@valencia"
LC_PAPER="ca_ES.UTF-8@valencia"
LC_NAME="ca_ES.UTF-8@valencia"
LC_ADDRESS="ca_ES.UTF-8@valencia"
LC_TELEPHONE="ca_ES.UTF-8@valencia"
LC_MEASUREMENT="ca_ES.UTF-8@valencia"
LC_IDENTIFICATION="ca_ES.UTF-8@valencia"
LC_ALL=

Es suposa que ara ja ho tinc be no?

Ara nom`es em queda arreglar els accents (que com pots comprovar de moment encara no funcionen..)

Gracies!!
Per cert, com es fa per a donar el tema per acabat o solucionat? Es que no ho trobo..

---

### Post by SiscoGarcia on 2009-05-04
> **planera said:**
> 
Es suposa que ara ja ho tinc be no?

Ara nom`es em queda arreglar els accents (que com pots comprovar de moment encara no funcionen..)

Gracies!!
Per cert, com es fa per a donar el tema per acabat o solucionat? Es que no ho trobo..

Els locale ja els tens bé, diria que ara has de dir a suport d'idioma que "habiliti el suport per a introduir caràcters complexos". Prova-ho si no ho has fet i ja diràs.

Finalment, em temo molt que de moment no és possible marcar el fil com a resolt. Han tret aquesta opció :(

---

### Post by planera on 2009-05-04
La opció d'habilitar els caràcters complexos, ja el tenia activat d'un primer moment, però no anaven els accents. Ara, desactivant-ho, ja funcionen :confused:
La primera vegada que em vaig instal.lar l'Ubuntu, el dels accents ho vaig solucionar afegint a environment això: 

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games"

LC_ALL=ca_ES.UTF-8
LANGUAGE=ca_ES.UTF-8
LC_TYPE=ca_ES.UTF-8
LC_MESSAGES=ca_ES.UTF-8
LANG=ca_ES.UTF-8

però ara no m'ha funcionat, l'únic que he conseguit fent-ho és que em torni a quedar tot en anglès.. Al eliminar les linies afegides, ja ha tornat a la normalitat.
Però encara em queda la finestra d'entrada en anglès. Li puc canviar l'idioma, però al reiniciar torna a sortir en anglès.
Ho deixo així i no em complico més o té alguna solució fàcil? Perque no he aconseguit trobar-la..

Moltes gràcies una vegada més!

---

### Post by SiscoGarcia on 2009-05-04
> **planera said:**
> Però encara em queda la finestra d'entrada en anglès. Li puc canviar l'idioma, però al reiniciar torna a sortir en anglès.
Ho deixo així i no em complico més o té alguna solució fàcil? Perque no he aconseguit trobar-la..

A risc de dir una obvietat, has provat de canviar l'idioma a l'inici de la sessió i predeterminar-lo?

---

### Post by RainCT on 2009-05-04
- Sí, la sortida de «locale» està bé.

 - El suport per a caràcters complexos no cal, és per a llengues com el japonès.

 - A Sistema -> Administració -> Suport d'idioma, tens triat el Català a «Per a l'inici i l'entrada de tothom, utiliza:»?

 - A Sistema -> Preferències -> Teclat, pestanya «Disposicions», tens «Espanya - Variant catalana amb L amb punt volat» (o bé «Espanya» a seques) se&#320;lecionat?

---

### Post by planera on 2009-05-05
RainCT, l'idioma per defecte tinc el "catalan; valencian (Espanya)", i com a idiomes suportats nomès tinc marcat el català, però tot i això em deixa seleccionar l'angles a idioma per defecte.
El del teclat no ho tenia seleccionat, però ara ja hi està.

SiscoGarcia, vaig canviar l'idioma de la finestra d'entrada, i em va preguntar si volia mantenir-lo sempre, li vaig dir que si, però sembla que ignora el que li vaig dir.

Així que, segueixo amb la finestra d'entrada en anglès, però com tot el demés ho tinc ja en català, crec que ho deixaré així.

Gràcies!!

---

