---
title: "[SOLVED] Escriure accents amb l'AMSN"
date: 2007-08-19
forum: Catalan Team
---

### Post by nickpage on 2007-08-19
Hola companys,

tinc la versió 7.04 d'ubuntu, i he instalat la versió de l'aMSN 0.97.
Funciona molt be però tinc l'inconvenient que no puc escriure accents ni els caràcters ç i ñ.

Hi ha algú amb el mateix problema que ho hagi solucionat.

Gràcies

---

### Post by papapep on 2007-08-19
Sembla ser que és un problema ja detectat i que està pendent de resolució en properes versions.

---

### Post by nickpage on 2007-08-19
Gràcies per la resposta....

esperarem a veure que passa en les noves versions.
De fet he perdut molt de temps aquest cap de setmana buscant la solució...

---

### Post by patrickfromspain on 2007-08-19
es molt facil. Has de modificar l'arxiu langlist de l'amsn. Per veure on es, en una terminal:

sudo updatedb
locate langlist

Aquesta ultima ordre et dira on es, sera de l'estil de: /carpetes/share/amsn/langlist

gksudo gedit /......./share/amsn/langlist

i alla, busques:

<lang>
                <langcode>ca</langcode>
                <name>Catalan-Valencian (Català-Valencià)</name>
                <version>1.123</version>
                <encoding>iso8859-1</encoding>
        </lang>

i cambies l'iso8859-1 de l'encoding per utf-8

Guardes i reinicies l'amsn i ja hauria d'estar.

salut!

---

### Post by nickpage on 2007-08-20
Gràcies,

aquesta tarda ho provaré quan torni de la feina. Ja diré si m'ha anat be o no.

Salut

---

### Post by nickpage on 2007-08-20
Hola patrickfromspain,

doncs he provat com dius i continuo sense poder posar accents...:(

Seguiré investigant, si ho trobo ja us informaré

Salut i gràcies

---

### Post by patrickfromspain on 2007-08-21
proba aixo:

sudo locale-gen --purge

---

### Post by nickpage on 2007-08-21
Doncs ho he provat i tampoc funciona.

Gràcies per l'interès. ;)

---

### Post by pabloiran on 2007-08-24
Passa't per ací i mira si et funciona el que comenten:

[http://forum.somgnu.cat/viewtopic.php?f=5&t=532&p=2882&hilit=amsn#p2858](http://forum.somgnu.cat/viewtopic.php?f=5&t=532&p=2882&hilit=amsn#p2858)

---

### Post by pespin on 2007-08-24
Doncs sí, a mi em funciona, i sí, també tenia la 'versió' valenciana activada.

Per a que funcionin els accents i 'ñ' abans haig de fer un 

```
export LANG=ca_ES.UTF-8
```

i córrer l'amsn des de la terminal.

**Algú pot explicar com es fa per a possar-ho de manera global i automàtica?**

---

### Post by nickpage on 2007-08-26
Efectivament, si llanço l'amsn pel terminal els accents funcionen perfectament... m'agradaría saber si hi ha alguna manera de fer-ho amb una llançadora

Salut i gràcies

---

### Post by patrickfromspain on 2007-08-27
Perque no probeu a anar a Sistema -> Administracio -> Suport d'idioma i hi poseu Catalan (Spain)? 

Si voleu fer la llançadora.. feu una llançadora nova i poseu-hi de comanda export LANG=ca.ES.UTF-8 && amsn o el que sigui. O a /usr/local/bin/amsn-cat hi poseu: 

#!/bin/bash

export LANG=ca_ES.UTF-8
amsn

i feu una llançadora a amsn-cat

salut!

---

### Post by pespin on 2007-08-27
Hmm a mi m'intereseria més saber quina ordre o quin arxiu haig d'editar per a deixar el ca_ES.UTF-8 i treure'm el ca_ES.UTF-8@Valencia

---

### Post by lluisanunez on 2007-08-27
I no pots insta&#320;lar Language-suport-ca, assignar-lo per defecte  i desinsta&#320;lar el valencià?

---

### Post by pespin on 2007-08-27
En aquest ordinador tinc el KDE, i no veig a cap lloc que posi Valencià, només posa Català a la configuració d'idiomes. 

i el paquet "language-support-ca" ja el tinc instal·lat :)

Per això preguntava on parava l'arxiu de configuració, perquè suposo k només serà canviar la variable $LANG

---

### Post by patrickfromspain on 2007-08-27
/etc/default/locale

/etc/environment

igual has de reinicia per a que els canvis facin efecte, o al menys entra i sortir de la sessió.

salut!

---

### Post by nickpage on 2007-08-27
Hola,

als arxius que comenta patrickfromspain tinc el següent:

LANG="ca_ES.UTF-8@valencia"

en canvi al suport d'idioma tinc posat Català(Espanya).

Per tenir el català que no sigui valencià com ho puc canviar.

Gràcies

---

### Post by patrickfromspain on 2007-08-27
canviant ca_ES.UTF-8@valencia per ca_ES.UTF-8

---

### Post by nickpage on 2007-08-28
Solucionat!!!!!!!

Efectivament, he editat els arxius 
/etc/default/locale
/etc/environment

i he substituït ca_ES.UTF-8@valencia per ca_ES.UTF-8

he re iniciat el PC i el amsn funciona correctament :popcorn:

la pregunta que em queda es per què tenia posat valencià???:confused:

Gràcies a tots per la vostra ajuda.

---

### Post by CarlesOriol on 2007-08-29
En Toni Hermoso ha corretgit aquest error de les variants del ca_XX a les X. Crec que a la propera versió ho tindrem arregladet.

---

