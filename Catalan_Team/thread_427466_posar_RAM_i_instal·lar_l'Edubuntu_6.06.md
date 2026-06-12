---
title: "posar RAM i instal·lar l'Edubuntu 6.06"
date: 2007-04-29
forum: Catalan Team
---

### Post by bikerbaixcamp on 2007-04-29
Bones, 
ara m'he desfet d'un ordinador i bé, hi ha alguna peça que es pot aprofitar, com per exemple una RAM de 256. 
Resulta que ma tieta té un ordinador un pentium III amb 64mb de RAM.. llavors el que tenia pensat és posar aquests 256 de més.. i llavors posar l'Edubuntu per ma cosina petita... 
La cosa seria, com posar la RAM, llavors si el Windows o la placa base la detectaria.. i al cap d'un temps ja instal·laria l'Edubuntu 6.06.

Algú pot resoldre els meus dubtes.? I les vostres suggerències...

Gràcies i poseu programari lliure als amics, familiars, coneguts!!!!

---

### Post by papapep on 2007-04-29
Be, el que preguntes és simple però, al mateix tems, relliscós. M'explicaré: el fet de que la memòria et funcioni al pc de la teva tieta depèn bàsicament de que siguin del mateix tipus, i que estigui, la de 256, dins els rang de freqüències que permet la placa mare. En principi, posant-la i engegant el pc veuràs si te la reconeix o no. També és possible que no puguin conviure la memòria antiga i la nova. Jo provaria a treure l'actual, posar la nova al seu lloc i engegar el pc. Si funciona, posar les dues a veure si saben conviure.
Normalment els xips de memòria porten una enganxina on posa el tipus i la freqüència de treball de la mateixa. Si ho compares amb les especificacions de la placa mare podàs veure, a priori, si són compatibles, o no. Si ens dius les dues coses, li podem fer un cop d'ull.

I la RAM la detecta la bios, essent indiferent, normalment, el sistema operatiu que hi ha a l'ordinador.

Salutacions.

---

### Post by bikerbaixcamp on 2007-04-29
La freqüència és allò dels 133Mhz ? Per informació addicional dir que el meu ordinador vell i el de la tieta tenen els mateixos anys.

Tardaré en comprovar-ho, però gràcies per la recomanació.

Per cert, si faig això, i pel que fos la RAM no me la reconeix, i llavors torno a posar la de 64mb no hi hauria cap problema, no? S'hauria de tornar a configurar o què?

;-)

---

### Post by CarlesOriol on 2007-04-29
Personalment crec que es massa poca màquina per fer-hi res.

---

### Post by papapep on 2007-05-02
Doncs, Carles, tot depèn de la memòria que hi posi. 256 megues és justet. Però mira que tinc jo com a servidor web, per jugar els nanos i unes quantes tonteries més:

root@helm:~# dmesg|grep Intel
[17179571.316000] CPU0: **Intel Pentium III** (Coppermine) stepping 0a

Ara, el fet que permet que rutlli decentment és aquí:

root@helm:~# free
             total       used       free     shared    buffers     cached
Mem:       **1815936**    1107996     707940          0     409596     509084
-/+ buffers/cache:     189316    1626620
Swap:       779144          0     779144

Salutacions.

---

### Post by papapep on 2007-05-02
> La freqüència és allò dels 133Mhz ?
Si, això és una freqüència. I si està escrita als xips de memòria, és la freqüència de treball de la mateixa, la qual ha d'estar dins del rang de freqüències admeses per la placa mare.

> 
 Per informació addicional dir que el meu ordinador vell i el de la tieta tenen els mateixos anys.

Ho sento, però actualment pots comprar ordinadors d'última generació, o màquines que fa dos o tres anys que ja existeixen. M'explico, oi? Apart, en mesos les tecnologies canvien.

> 
Per cert, si faig això, i pel que fos la RAM no me la reconeix, i llavors torno a posar la de 64mb no hi hauria cap problema, no? 

No, no ha d'haver-hi cap problema. Sobretot, quan manipulis els xips de RAM intenta no tocar els contactes amb les mans, la electricitat estàtica els mata molt ràpid. Si toques la fibra de vidre ho evitaràs.

> 
S'hauria de tornar a configurar o què?

Excepte en equips de marca com IBM, Dell i similars, que si detecten canvis et demanen confirmació o anar a la Bios, no he vist que controlin quanta memòria tenen instal·lada. La majoria dels clònics quan s'engeguen detecten automàticament quanta en tenen i punt.
Vaja, que com a molt et demanarà confirmació per actualitzar la informació de la RAM.

---

### Post by CarlesOriol on 2007-05-03
Disculpa papapep vaig llegir massa ràpid. 

Vaig veure ordinador + vell + 133 mhz = container

---

### Post by PellRoja on 2007-05-03
Em sembla que les regletes de Ram tenen unes pestanyes o dentetes que s'els i diu. Són una mena de forat que hi ha al mitg. Pots comprovar que al extreure la de 64mb sigui igual a la de 256mb per que tenen la dent o pestanya al mateix lloc.

Per si a cas, miret be les entrades de RAM amb una llenterna  i veuras que hi ha la denteta, mira de colocar be la regleta, i no forcis si veus que no entra.

:P

---

