---
title: "eliminades les particions de windows-reassignar espai guanyat"
date: 2012-10-29
forum: Catalan Team
---

### Post by jinglada on 2012-10-29
Eliminades les particions de windows amb el GParted, em queda un espai "no assignat" de 47,44 GiB al començament i un que ja tenia de 2,49 MiB al final. 

Què m'aconselleu, que les afegeigi a la partició /home o que faci una partició de 20 GiB per anar provant les noves versions de l'Ubuntu o altres distribucions i la resta ho recupero al /home?

La partició "Linux swap" que tinc de 10,2 GiB no és sobredimensionada?

-------------------------------------------------
joan@joan-laptop:~$ sudo fdisk -l
[sudo] password for joan: 

Disk /dev/sda: 320 GB, 320070320640 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda3            6194       38913   262815367    5  Extended
/dev/sda6            6194       11056    39054015   83  Linux
Warning: Partition 6 does not end on cylinder boundary.
/dev/sda7           11057       37582   213062062   83  Linux
Warning: Partition 7 does not end on cylinder boundary.
/dev/sda5           37583       38913    10683225   82  Linux swap
Warning: Partition 5 does not end on cylinder boundary.
Error: /dev/zram0: etiqueta de disco no reconocida
joan@joan-laptop:~$ 
----------------------------------------------

---

### Post by wgarcia on 2012-10-29
Els 2 megues no utilitzats jo els deixaria, a vegada no es poden assignar aquests troços petits. El swap el deixaria únicament el doble de tamany que la memòria que tinguis, si tens 4 gigues de memòria el deixaria en 8 gigues. I l'espai inicial, que no està en la partició lògica, podries deixar-lo com dius per provar distribucions noves. 

Reduir l'espai del swap i incrementar el home hauràs de fer-ho des d'un CD o USB autònom, perquè no pots canviar el tamany de particions que estan muntades. Sols es pot utilitzar espai contigu a la partició, així que primer has de reduir el swap i després incrementar el home amb l'espai no utilitzat.

---

### Post by jinglada on 2012-10-29
> **wgarcia said:**
>  I l'espai inicial, que no està en la partició lògica, podries deixar-lo com dius per provar distribucions noves. 

Gràcies wgarcia! Per provar distribucions noves amb 20 gigues et sembla suficient?

---

### Post by wgarcia on 2012-10-30
Sí, 20 gigues és suficient, inicialment ocupen menys de 10 gigues.

---

### Post by jinglada on 2012-10-30
> **wgarcia said:**
> Sí, 20 gigues és suficient, inicialment ocupen menys de 10 gigues.

Gràcies; poso SOLVED.

---

