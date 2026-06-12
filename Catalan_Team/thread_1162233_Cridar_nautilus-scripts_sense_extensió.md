---
title: "Cridar nautilus-scripts sense extensió"
date: 2009-05-17
forum: Catalan Team
---

### Post by friviere01 on 2009-05-17
Hola geeks!

Voldria fer una crida a nautilus-scripts per compilar amv gcc que en clicar un fitxer fes:

gcc fitxer.c -o fitxer

però no aconsegueixo treure la extensió al final (sense cap script, directament al diàleg!)

ja que fent

gcc %d/%f -o %d/%f%%c

dóna per resultat un arxiu així:

fitxer.c%c

Algú sap com fer-ho?

Refs: [http://g-scripts.sourceforge.net/index.php](http://g-scripts.sourceforge.net/index.php)

Per cert, per fer-ho cridant a un script, funciona amb aquest:

#!/bin/sh
#compila.sh
gcc $1 -o ${1%.c}

---

