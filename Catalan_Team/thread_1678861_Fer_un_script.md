---
title: "Fer un script"
date: 2011-01-31
forum: Catalan Team
---

### Post by edvac on 2011-01-31
Hola,

 Tinc un problema a l'hora de realitzar un script, aquest script ha de servir per a trobar diversos arxius i esborrar-los.

 find nom_arxiu

 Això em dóna una sèrie d'arxius que s'han de esborrar, el meu problema és el següent. Com els puc esborrar?

 Crec que podria ser:

 rm find nom_arxiu

 Però no sabria com fer-ho ...

 També voldria que la informació d'aquest arxiu anés a parar a un. txt per revisar-la ... però això no és imprescindible.

 Gràcies per la seva ajuda per endavant.

 Salutacions,

 EDVAC

---

### Post by kukat on 2011-01-31
find . -name *.mp3 | xargs rm -f

he trobat açò: 
[http://www.guatewireless.org/os/linux/linux-buscar-y-borrar-archivos-del-sistema-de-archivos/](http://www.guatewireless.org/os/linux/linux-buscar-y-borrar-archivos-del-sistema-de-archivos/)

Supose que també pots acabar-ho amb:

find . -name *.mp3 | xargs rm -f >> informe.txt

Per a dirigir-ho a un fitxer de text.

Però no puc provar-ho en aquestos moments. 


;)

---

### Post by ggoscarl on 2011-01-31
Hola,

per a generar l'informe falta la "v" de verbose mode:

find . -name *.mp3 | xargs rm -vf >> informe.txt

llavors genera línies d'aquest tipus:

s’ha eliminat «./proves/prova2.txt»

---

### Post by kimet on 2011-01-31
Pots assignar una variable al fitxer en qüestió, si son mes d'un pots fer servir caracter de substitució ('*','?') 

f=fitxer* 
find $f 
cat $f >> copia.txt
rm $f


Salut

PD. Si poses l'script ho veurem millor.

---

### Post by edvac on 2011-02-03
Gracias a tots, ja ho he solucionat.

---

### Post by ggoscarl on 2011-02-03
i no ens poses la solució? ;-)

---

