---
title: "Memoria Cau i swap"
date: 2010-12-08
forum: Catalan Team
---

### Post by dmartinez116 on 2010-12-08
Tinc ubuntu 10.10 64 bits i 4GB de memòria RAM.

Quan tinc moltes aplicacions a la vegada (sobretot màquines virtuals), la memòria ocupada (mirant-ho al monitor de sistema) no arriba al 50%, però quan la memòria cau arriba al 100% l'equip es fa molt lent, no em deixa fer res... fins que passa un temps i es recupera sol. 

El tema és que jo quan vaig instal·lar ubuntu vaig definir una partició per a swap, però quan mire el monitor de sistema em diu que hi ha 0% ocupada... per molt liat que estiga l'equip, mai s'utilitza... a que és degut? com ho puc solucionar?

Gràcies.

---

### Post by wgarcia on 2010-12-09
Potser és que no necessiti el swap, i la lentitud provingui d'un altre factor com ara l'ús del CPU. Pots mirar com està configurat l'ús del swap mirant el paràmetre de "swapiness":

cat /proc/sys/vm/swappiness

El valor normal és 60.

---

### Post by dmartinez116 on 2010-12-09
Si, mirant per foros vaig vore el paràmetre que comentes i jo també el tinc a 60 (el valor per defecte). Quan al processador... a la barra superior de gnome tinc definits els quadres de monitor de sistema (cpu, memòria, xarxa i espai d'intercanvi) i els processadors estan ociosos, la memòria com he descrit abans, la xarxa parada i el espai d'intercanvi a 0.

Hem resulta extrany...

---

### Post by wgarcia on 2010-12-09
Tingues en compte que linux fa servir memòria cau. Això el que vol dir és que la memòria queda reservada, tot i que es tanqui un programa, a aquest programa per si es torna a obrir. És per aquesta raó que els programes obren molt més ràpid un cop que ja s'han obert i tancat, per exemple el firefox o qualsevol altre navegador tarda més d'obrir la primera vegada que qualsevol altra arrencada subsegüent. Ara bé, si aquesta memòria cau es necessita per algun altre programa, s'allibera i s'utilitza. Per això pots veure que la memòria RAM està a 100% però en realitat és tot memòria cau. 

El que no s'entén del que planteges és per què s'enlenteix el sistema. Una altra comanda molt útil és "free -m", que t'ensenya com està sent utilitzada la memòria RAM i el swap. Per exemple al meu sistema (8 gigues) això és el que veig amb "free -m":

[SIZE=2]

```
             total       used       free     shared    buffers     cached
Mem:          7937       7501        435          0       1941        542
-/+ buffers/cache:       5017       2919
Swap:        16946         38      16908
```


[/SIZE]

Crec llegir aquí que hi ha 7501 de RAM utilitzat, però 5017 és memòria a cau per si es tornen a obrir programes que l'han utilitzat. Que algú em corregeixi si ho llegeixo malament...[FONT="Courier New"][/FONT]```

```

---

### Post by dmartinez116 on 2010-12-09
Ok, entec el que dius, i el meu free -m torna:
```
ubuntu@fubuntu:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3963       3930         33          0        162        771
-/+ buffers/cache:       2996        967
Swap:         9700          3       9697
ubuntu@fubuntu:~$ 
```
Així i tot no entenc perquè es queda com congelat el meu equip. Sol passar-me quan tinc en marxa una màquina virtual amb W7 que faig servir per al LightRoom 3.3 que té assignada 1GB de RAM. A més i simultàneament solc tindre oberts el thunderbird, el firefox i el metv. De sobte el metv es queda congelat (de vegades sols s'escolta) i les finestres del thunderbird i firefox es queden gris oscur (funciona el ratolí, però no puc fer res) si m'espere una estona (1-2 minuts) tot torna a la normalitat...

---

### Post by kimet on 2010-12-09
> ```
             total       used       free     shared    buffers     cached
Mem:          7937       7501        435          0       1941        542
-/+ buffers/cache:       5017       2919
Swap:        16946         38      16908
```




Crec llegir aquí que hi ha 7501 de RAM utilitzat, però 5017 és memòria a cau per si es tornen a obrir programes que l'han utilitzat. Que algú em corregeixi si ho llegeixo malament...[FONT="Courier New"][/FONT]```

```

No, els 5017 es memória utilitzada ja descontant buffers i cache i 2919 es el que tens a disposició.

---

### Post by kimet on 2010-12-09
> **dmartinez116 said:**
> Ok, entec el que dius, i el meu free -m torna:
```
ubuntu@fubuntu:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3963       3930         33          0        162        771
-/+ buffers/cache:       2996        967
Swap:         9700          3       9697
ubuntu@fubuntu:~$ 
```
Així i tot no entenc perquè es queda com congelat el meu equip. Sol passar-me quan tinc en marxa una màquina virtual amb W7 que faig servir per al LightRoom 3.3 que té assignada 1GB de RAM. A més i simultàneament solc tindre oberts el thunderbird, el firefox i el metv. De sobte el metv es queda congelat (de vegades sols s'escolta) i les finestres del thunderbird i firefox es queden gris oscur (funciona el ratolí, però no puc fer res) si m'espere una estona (1-2 minuts) tot torna a la normalitat...

Has de tenir en compte que w7 consumeix una gran quantitat de memória i si amb els programes que tens oberts a més, superes la teva memòria disponible i es fà ús de la swap aquesta no és igual de ràpida que la RAM. Per tant es normal que es faci mes lent el sistema.
Per altre banda amb la memòria RAM de que disposeu em sembla molt exagerat l'espai destinat a SWAP.

Salut.

---

### Post by dmartinez116 on 2010-12-09
Ok Kimet, entenc el teu raonament, però si el W7 te assignat 1GB, per poc que siga, i per molt que consumixca... es deuria penjar ell sol, no? a l'ubuntu encara li queden quasi 3GB per al metv, per al firefox i el thunderbird... no entenc perquè es congela l'ubuntu...

---

### Post by kimet on 2010-12-09
> **dmartinez116 said:**
> Ok Kimet, entenc el teu raonament, però si el W7 te assignat 1GB, per poc que siga, i per molt que consumixca... es deuria penjar ell sol, no? a l'ubuntu encara li queden quasi 3GB per al metv, per al firefox i el thunderbird... no entenc perquè es congela l'ubuntu...

No es tan senzill, la màquina virtual no consumeix només el espai que l'hi has assignat al sistema virtualitzat.

Pots povar a modificar els valors a /proc/sys/vm/swappiness com et diu l'wgarcia.
Em sembla:
```
sudo sysctl -w vm.swappiness=80 
```
Em sembla que elvalor 80 hauria de retrasar la entra en que es posa a funcionar la swap, no ho recordo exactament, (podria ser a revés).
O desctivant la swap completament:
```
sudo swapoff -a
```

---

### Post by wgarcia on 2010-12-09
Una altra possibilitat és que la màquina virtual pengi el sistema gràfic. Perquè segons comentes no hi ha un consum excessiu de CPU quan el sistema es penja. Un altre símptoma d'això és que el so se segueix reproduint tot i que el sistema es penja. 

Una prova que es pot fer és provar de córrer la màquina virtual amb els "efectes especials" gràfics desactivats (Aparença -> efectes gràfics) i veure si el problema desapareix.

---

### Post by dmartinez116 on 2010-12-09
Primer es congela la imatge, però acaba per parar-se tot (inclòs el so).

El W7 està configurat amb les acceleracions gràfiques, aero, etc... desactivats, pareix un xp.

He provat a fer que la màquina virtual tinguera 2GB i també funciona... però no utilitza RES de memòria d'intercanvi. Encara que tinga el metv encés... ara faré proves arrancant dos màquines virtuals amb 2GB cadascuna... a vore si així veig algo clar...

---

### Post by marteljorge on 2010-12-09
> **dmartinez116 said:**
> Primer es congela la imatge, però acaba per parar-se tot (inclòs el so).

El W7 està configurat amb les acceleracions gràfiques, aero, etc... desactivats, pareix un xp.

He provat a fer que la màquina virtual tinguera 2GB i també funciona... però no utilitza RES de memòria d'intercanvi. Encara que tinga el metv encés... ara faré proves arrancant dos màquines virtuals amb 2GB cadascuna... a vore si així veig algo clar...
Jo vaig tenir problemes similars per una causa diferent. Els vaig solucionar afegint una línia al crontab de root (amb crontab -e ho pots editar):
```
*/5 * * * * echo 3 > /proc/sys/vm/drop_caches
```
I si fas el que dius es passarà una bona estona el sistema "pillat" si les màquines ho consumeixen. Com em va passar amb el portàtil un dia que fent swapoff -a no em vaig fixar que tenia la memòria plena...

---

### Post by dmartinez116 on 2010-12-10
gràcies jorge, però hem podries explicar que fa eixe comandament que me recomanes ficar al crontab?

Es que pense que tu fas les màquines virtuals amb vmware o xen, no? i jo estic fent servir VirtualBox.

---

