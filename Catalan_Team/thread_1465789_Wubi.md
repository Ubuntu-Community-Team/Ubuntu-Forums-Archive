---
title: "Wubi"
date: 2010-04-29
forum: Catalan Team
---

### Post by lord_mordred on 2010-04-29
Hola, he probat diverses vegades el Wubi, i algunes de les vegades al desinstalar m'ha quedat l'entrada de Ubuntu en el gestor de carrega. Ja en tinc 2, mes la entrada que m'acaba de crear el Lucid. La questio es que les altres dues son erronies, per que esta desinstalat, pero continuen sortint...
Com les puc eliminar?

---

### Post by pelai21 on 2010-05-01
Hola, Wubi no és la millor opció per instal·lar l'ubuntu. Ni tan sols per provar-lo. El millor és fer una partició del disc dur, perquè si no hi poden haver interferències i tampoc pots veure correctament el rendiment que té ubuntu. 

Dit això, intentaré ajudar-te. Pot ser que no s'hagin desinstal·lat bé les versions antigues o que tinguis kernels antics instal·lats? Prova d'escriure això en una terminal, i a veure què et diu.

> dpkg --get-selections | grep linux-image

---

### Post by lord_mordred on 2010-05-01
linux-image-2.6.32-21-generic            install
linux-image-generic                install

Ja se que no es la millor manera, pero nomes tinc mig portatil y acostumen a venir sense cd de windows :confused:

Vejam si estalvio, em compro un sobretaula i m'hi fico mes a fons... si es que aprenc a fer anar aixo de Linux, que cada vegada em perdo mes

---

### Post by SiscoGarcia on 2010-05-01
> **lord_mordred said:**
> Com les puc eliminar?

Primer assegura-te'n de quines són les versions que tens instal·lades amb

```
sudo aptitude search linux-image-|grep ^i
```

després fes

```
sudo aptitude purge linux-image-versió_del_paquet
```

on «versió_del_paquet» serà 2.6.32-xx-generic o el que correspongui.

Compte: Verifica bé quina versió tries per desinstal·lar, no hi ha tornada enrere :(

---

### Post by lord_mordred on 2010-05-02
Ja, pero es que d'instalades nomes surt el Lucid... 
La cosa es que en anteriors ocasions que he usat el Wubi, al desinstalar m'ha deixat l'entrada al master boot recorder del windows, i ara em surten 3 versions de ubuntu a l'hora de triar S.O., i de fet nomes tinc el Lucid y windows

---

### Post by wgarcia on 2010-05-02
No t'estaràs referint a tres nuclis del Lucid diferents, amb números de versió diferent? Això és normal al grub.

---

### Post by lord_mordred on 2010-05-02
No, una de la entrades es de quan vaig baixar l'anterior versio estable per probar... l'altre del Koala, i la 3ª, que es la unica que hauria de ser, es del Lucid.
La questio, torno a dir, es que vaig executar el desinstalador del Wubi amb les 2 primeres, i normalment anaba tot be, pero 2 de les vegades va deixar l'entrada al selector d'arranc... i ara em surten aquelles dues entrades, que no remeten a res, la del windows y la de Lucid.
Les altres dues versions no hi son, nomes queda l'empremta al menu d'arranc
quen pico el que meu dit a la consola surt
linux-image-2.6.32-21-generic            install
linux-image-generic                install
Que imagino es el Lucid, ni rastre de les altres, ni queda cap carpeta a windows ni res, la desintalacioa va ser correcta, nomes que ara al arrencar em surt 1 windows y 3 ubuntus (el Lucid, y dos "fantasmes"

Haig de empaparme el Grub per veure si alla hi ha res a fer, o es questió d'escriure una consulta als nois de Redmond per que em diguin, aixó et passa per ser un noi dolent :lolflag:?

Es que no tinc ni idea si el master boot record del windows es pot reparar desde Grub, desde la consola o nomes desde windows...

A mi l'unic que se m'acudia era tirar de Ccleaner a veure si trobaba alguna entrada penjada al registre de windows, y en feia neteja, pero es veu que el master boot esta fora de l'abast del ccleaner

---

### Post by wgarcia on 2010-05-02
Però el windows el pots arrencar?

---

### Post by lord_mordred on 2010-05-04
Si tots dos arrencan be. tant el Lucid, com el Windowa, pero es un merder tenir 3 entrades d'Uubntu al gestor d'arranc quan nomes n'hi ha una versio en marxa.... 
Si per error miró d'entrar amb una de les erronies toca reiniciar a la brava jajajaaa
El que vull es saber com netejar el gestor d'arranc de les entrades invalides...

Via Ubuntu, via Windows, via BIOS? No en tinc ni idea

---

### Post by papapep on 2010-05-04
Si fas a un terminal:

```
sudo aptitude search linux-image |grep ^i

```

què et surt?

Abans has dit:

> Ja, pero es que d'instalades nomes surt el Lucid... 

però què et surt al terminal en fer això?

Enganxa aquí el resultat, si us plau.

---

### Post by pelai21 on 2010-05-06
Hola, he trobat una pàgina que potser et pugui ajudar:
[http://techtastico.com/post/como-limpiar-el-sector-de-arranque-del-disco-duro/](http://techtastico.com/post/como-limpiar-el-sector-de-arranque-del-disco-duro/)
De totes maneres, el Master Boot Record, si no m'equivoco, no és un programa d'Ubuntu, de manera que si no te'n surts probablement ho hauries de consultar a una altra banda. És el que et comentava de Wubi i de les interferències...

---

### Post by lord_mordred on 2010-05-10
anem a pams, el que surt quan entro a consola el que diu en papapep es:
i   linux-image-2.6.32-21-generic   - Linux kernel image for version 2.6.32 on x
i   linux-image-2.6.32-22-generic   - Linux kernel image for version 2.6.32 on x
i   linux-image-generic             - Generic Linux kernel image    

I sobre el que diu en Pelai, també es el que penso jo. Si el Wubi "corre" sota windows, el mes segur es que les dades per arrencar Ubuntu no siguin sota cap Gestor de carrega de Linux, si no que son al MBR de Windows. 
La pagina aquesta que dius, explica molt be com arreglar-ho Pelai, pero em fa mes por que una pedregada esborrar tot el MBR, i confiar que windows solet l'arregli hahahahaa.
Basicament, per que ni tinc unitat de cd, ni disc d'arranc ni res, i si despres Windows no es capaç de trobarse a si mateix ja l'hem liat... 
D'altra banda, em jugo un pessol que el que no trobaria seria el Lucid,... Repararia el MBR creant nomes l'entrada de Windows suposso. I llavors, seria possible "desinstalar" el Lucid, o windows simplement ignoraria els 12 gigas de la instalacio?

---

### Post by SiscoGarcia on 2010-05-12
Com pots veure tens dos nuclis diferents, tots dos de Lucid. Si vols desintal·lar-ne un (el més vell, suposo) el que has de fer és:

```
sudo aptitude purge linux-image-2.6.32-21-generic
```

... que és el que fa una setmana et vaig comentar i diria que vas ignorar :evil:

---

### Post by lord_mordred on 2010-05-26
Ara tince el nucli 2.6.32-21 purgat....
I continuo tenint 3 entradas d'ubuntu al master boot...
Abans, quan seleccionaba la unica entrada valida del ubuntu em pasaba a la tipica pantalla per escollir si entras en mode segur etc.... o amb quin nucli entres... ara nomes tinc el 2.6.32-22, ja que he purgat l'altre.... Pero a la primera, la d'on esculls entre windows o linux, em continua donant 2 "imatges fantasmes" de l'ubuntu fruit de 2 desinstalacions fallides del Wubi...
Aixi donç tornem al mateix... com elimino aquestes dues entrades?
Pelai, em penso que el teu consell es valid, pero ja et dic, sense cap mitja de fer un back-up, i sense unitat de cd operativa per reinstalar windowa, no m'atreveixo a esborrar el MBR i jeure a esperar a que windows el repari solet.... i menys amb un altre SO al disc...
Si alguna cosa pot sortir malament...sortira malament... i si el manefles de Seatle hi estan embolicats p'el mig.... la fallada es segura :P
I com que no tinc cap intencio de quedarme amb un pc mort, i sense manera d'arrencarlo i a mes perdent el contingut del disc, prefereixo no potinejar via windows.
No hi ha cap "eina" que simplement et permeti eliminar entrades del Wubi?

---

### Post by wgarcia on 2010-05-26
Per veure com està configurat el teu sistema, pots córrer el programeta que et pots baixar de:

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

i adjuntar el resultat (RESULT.txt) que obtens fent:

sudo bash ~/boot_info_script*.sh 

des de la línia de comandes.

---

