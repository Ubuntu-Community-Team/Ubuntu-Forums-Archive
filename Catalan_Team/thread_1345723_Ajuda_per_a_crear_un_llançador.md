---
title: "Ajuda per a crear un llançador"
date: 2009-12-04
forum: Catalan Team
---

### Post by valdric on 2009-12-04
Hola a tots.

Estic fent servir Ubuntu 9.10 i encara soc una mica totxo en aquest mon del Linux. Anem al gra:

Jo per fer una copia de la meva base de dades MSQL obro una terminal i faig lo següent:

mysqldump --opt --user=***** --password=***** carme > "/home/carme/Dropbox/Base de Dades/Copia a dia `date`.sql"

***** = ;)

En una terminal hem va tot bé. El problema es que quan ho intento fer desde un llançador i cridar aquesta ordre només fent doble click sobre el corresponent icono la cosa no rutlla.

Ho he probat amb el tipus de llançador Aplicació i amb Aplicació en terminal i res.

També he probat de posar-hi al davant: "gnome-terminal -e" sense les cometes però tampoc. Ja no se que fer-hi més....

Algú hem pot ajudar?

---

### Post by abuch on 2009-12-04
Hola,

l'ordre de bolcat de la base de dades la poses directament al llançador o bé en un fitxer? Si és el primer cas et suggereixo que creïs un fitxer de text pla amb aquesta ordre, li donis permís d'execució, i llavors creïs el llançador del fitxer. Si el crees del tipus aplicació en un terminal la finestra que s'obrirà es tancarà un cop acabada la feina.

Fins una altra.

Aleix

> **valdric said:**
> Hola a tots.

Estic fent servir Ubuntu 9.10 i encara soc una mica totxo en aquest mon del Linux. Anem al gra:

Jo per fer una copia de la meva base de dades MSQL obro una terminal i faig lo següent:

mysqldump --opt --user=***** --password=***** carme > "/home/carme/Dropbox/Base de Dades/Copia a dia `date`.sql"

***** = ;)

En una terminal hem va tot bé. El problema es que quan ho intento fer desde un llançador i cridar aquesta ordre només fent doble click sobre el corresponent icono la cosa no rutlla.

Ho he probat amb el tipus de llançador Aplicació i amb Aplicació en terminal i res.

També he probat de posar-hi al davant: "gnome-terminal -e" sense les cometes però tampoc. Ja no se que fer-hi més....

Algú hem pot ajudar?

---

### Post by papapep on 2009-12-04
La manera més simple és crear un script on "allotjar" a teva ordre:

```

#!/bin/bash
mysqldump --opt --user=***** --password=***** carme > "/home/carme/Dropbox/Base de Dades/Copia a dia `date`.sql"

```

i tot això dins un fitxer de nom, per exemple, copiaSeguretatMysql.sh

Dónes permisos d'execució al fitxer:

```
chmod +x copiaSeguretatMysql.sh
```

i l'executes:

```
./copiaSeguretatMysql.sh
```

També et recomano, per evitar maldecaps, no emprar espais als noms de fitxers. Ho pots fer, en teoria, però pot ser que un dia et tornis boig (o haig de dir boja?? :D) buscant per què una ordre no fa el que esperes ;)

---

### Post by valdric on 2009-12-07
Primer de tot moltes gràcies per les vostres respostes. Anem a contertar:

**abuch:** Ho sento però no tinc el nivell de coneixements necessaris per entendre la teva resposta. Jo el que vull fer és crear un arxiu que contingui una còpia de la meva base de dades. Aquest arxiu el poso a la carpeta Dropbox i aquest mateix programa en fa una còpia al núvol. 

**papapep** Et confirmo que la teva resposta m'ha anat perfectament:-D. He seguit les teves indicacions al peu de la lletra i oli en un llum. 

Tot i així, de cara a apendre'n una micona, hem podries dir perquè no funciona lo que jo intentava fer? Es a dir, perquè no funciona aquesta ordre directament en un enllaç i sí que funciona en un script?

---

