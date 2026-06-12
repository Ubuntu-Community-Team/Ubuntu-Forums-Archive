---
title: "Programació bash"
date: 2010-05-13
forum: Catalan Team
---

### Post by lorencillo on 2010-05-13
Hola a tothom...

estic fent un petit script per treure informació d'uns logs i haig de calcular el temps que hi ha desde del començament d'un procés fins que acaba, en format HH:MM:SS.

Com que el inici per exemple es a les 20:40 del 12/05/2010 i l'acabament es a les 10:40 del 13/5/2010, no sé que passa que m'en surten coses rarisímes!!

1er transformo les hores a segons en format UNIX
2on les resto 
y al final transfromo aquests segons al format HH:MM:SS

No sé que estic fent malament, però aquesta resta em tona per exemple (no m'en recordo exactament) 89961 segons. Aquesta quantitat de segons són més de 24 hores!!!! i el procès no triga tant

No sé si ho estic fent bé o si n'hi ha una manera més lógica de tractar dates/hores en bash.

Algú té una orientació?

Gracies.

---

### Post by wgarcia on 2010-05-14
#!/bin/bash

TEMPS_INICI=`date +%s`

######
# les teves comandes
du
#

TEMPS_FINAL=`date +%s`

DURACIO=`expr $TEMPS_FINAL - $TEMPS_INICI`

echo "Ha acatat el " `date` " Duració: " `date -d 00:00:$DURACIO +%H:%M:%S`

---

### Post by epileg on 2010-05-16
Bones,

Una manera senzilla de fer-ho és executant l'script amb l'ordre «time»:

> $ /usr/bin/time -f "%E" script.sh


I si no, pots fer això a dins l'script:

> inici=`date +%s`

# les teves ordres

final=`date +%s`

dif=`expr $final - $inici`

dies=`date -d '1970-01-01 '$dif' seconds' +"%j"`

dies=`expr $dies - 1`

date -d '1970-01-01 '$dif' seconds' +"$dies %H:%M:%S"

Això mostra els dies (fins a un any), hores, minuts i segons entre les dues dates.

Evidentment la data «inici» ha de ser sempre anterior a «final» i amb menys d'un any de diferència, ja que no es té en compte l'any i donaria resultats incorrectes.

Salut.

---

