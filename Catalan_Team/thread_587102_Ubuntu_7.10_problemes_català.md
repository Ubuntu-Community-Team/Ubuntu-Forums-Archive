---
title: "Ubuntu 7.10 problemes català"
date: 2007-10-22
forum: Catalan Team
---

### Post by castellfollitenc on 2007-10-22
Hola companys,

Jo sóc bastant novell dins el món de l'Ubuntu, l'utilitzo des de fa un any, i n'estic molt content! Fa poc vaig  comprar-me un portàtil i ara també li he instal·lat l'ubuntu (7.10), la meva sorpresa és que  tot i seleccionar català com a idioma, la majoria d'aplicacions i menús són en anglès. Llavors quan vaig al synaptic no troba cap pàquet que no siguin els de llengua anglesa. El mateix em passa quan vaig a administració / llengua.

Un altre problema és que no hem deixa instal·lar cap nova aplicació, com per exemple l'Amarok.

Que en penseu? com puc posar tot en català (menus, correctors, etc.)

Moltes gràcies per la vostra ajuda!

---

### Post by Kosimo on 2007-10-22
Benvolgut company.
Benvingut a la comunitat Ubuntu!  Aquí t'hi sentiras com a casa i trobaras ajuda als problemes que puguis tenir i veuras que tenen fàcil sol·lució com aquest en concret.

Ubuntu efectivament s'instal·la mig en català mig en anglés, i això no només passa amb el català sinó amb altres llengües, per problemes d'espai al disc.
Per tenir-lo completament en català, menus, firefox, openoffice, correctors etc has de seguir uns passos molt senzills:

Ves a sistema > Administració > Soport de llengües (o alguna cosa semblant, mira la bandereta blava)

Allà hauras d'instal·lar el suport internacional que t'ho demana immediatament, i després en el menú que veus sel·lecciona com a llengua el català, veuras que ubuntu automàticament descarregarà i instal·larà tots els paquets restants per completar el teu sistema i tenir-lo completament en català.

Si tens problemes fes-nos-ho saber.

Sort, i benvingut.

---

### Post by Kosimo on 2007-10-22
Per cert, m'he oblidat de dir-te que per que els canvis tinguin efecte hauras de reiniciar la màquina.

---

### Post by papapep on 2007-10-22
Vols dir que no n'hi ha prou amb reiniciar el servidor X?? :-)

---

### Post by Kosimo on 2007-10-22
> **papapep said:**
> Vols dir que no n'hi ha prou amb reiniciar el servidor X?? :-)

Siguem pràctics! ;)

---

### Post by jmaspons on 2007-10-23
Si dius que no pots intal·lar programes nous, pot ser que no tinguis activats els repositoris. Des de l'Adept en KDE o des del gestor de repositoris del gnome (em sembla) pots activar els repositoris des d'on et pots descarregar tots els paquets que hi ha. Segurament deus tenir unicament activat el cd com a font de paquets.

Si vols fer-ho més artesanalment pots editar l'arxiu /etc/apt/sources.list i eliminar els # del principi dels repositoris que vulguis activar com per exemple:


deb [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) feisty main restricted multiverse universe
deb-src [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) feisty main restricted multiverse universe

---

### Post by papapep on 2007-10-23
Castellfollitenc, enganxan's aquí, si us plau, el contingut del fitxer /etc/apt/sources.list.

---

### Post by castellfollitenc on 2007-10-23
Hola a tots! Moltes gràcies per la vostra ràpida i eficaç ajuda!

Com molt bé ha dit en jmaspons no tenia cap repositori activat.

Moltes gràcies de nou.

---

### Post by CarlesOriol on 2007-10-23
Recordeu que aquest és un fòrum democràtic, **1 tema = 1 fil** per tal d' evitar multiples discusions creuades i poder cercar millor la informació  anterior.

---

### Post by SiscoGarcia on 2007-10-24
Pel que fa al tema d'inici (que lliga amb un altre fil on deia que s'havia instal·lat l'ubuntu mig en català mig en anglès) he de dir-vos que acabo d'aconseguir instal·lar des de CD en una màquina vells només el Gutsy i només en català.
Havia començat anit i només havia aconseguit que se m'instal·lés mig en català mig en anglès, El que havia fet llavors és consultar el fòrum i fer allò que ja havia pensat (sistema/administració/suport d'idioma i també fer servir l'apt...), però no me'n sortia; el tornava a reinstal·lar i tornava a passar-me el mateix. Havia pensat d'instal·lar Feisty i després actualitzar-me a Gutsy, però em sabia greu anar així, i aquest matí he pensat deredimensionar el disc dur amb el GParted i desfer-lo tot, per tal d'instal·lar-hi després només l'ubuntu Gutsy. Aquest cop me n'he sortit. No sé si pot ser útil a algú, espero que sí.

---

