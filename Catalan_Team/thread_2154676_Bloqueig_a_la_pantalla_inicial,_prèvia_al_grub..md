---
title: "Bloqueig a la pantalla inicial, prèvia al grub."
date: 2013-06-15
forum: Catalan Team
---

### Post by jinglada on 2013-06-15
Bona tarda ubunters!

Tinc un Packard Bell Easynote MT85-M-005SP, Intel Core 2 Duo P8400 2.26 GHz, Ram 4 Gb DDR2, ATI HD3650 512 MB, Hard Drive 320 GB, amb el Precise Pangolin, 12.04 LTS.

Fa dues o tres setmanes que, de tant en tant, a l'engegar es produïa el que ara explicaré i que ara ja passa 9 de cada 10 arrancades.

L'ordinador es queda bloquejat a la pantalla inicial on t'indica accedir a la BIOS amb F2, arrancar des de CD amb F3 i BOOT amb F8. El bloqueig és total i només respon la tecla d'arrancada/parada. He provat d'arrancar amb el CD i es queda bloquejat igualment.

Vaig telefonar a la botiga d'informàtica i em van dir que els hi portés l'ordinador que segurament era que la pila s'havia de canviar. Avui hi he anat i m'han dit que la pila està bé i que ha de ser cosa del sistema operatiu UBUNTU i que ells no hi entenen.

Us agraeixo a la bestreta el vostre ajut.

---

### Post by wgarcia on 2013-06-16
Si això passa abans que es carregui el grub òbviament no pot tenir res a veure amb l'Ubuntu, perquè encara no s'ha començat ni a executar. És trist que hi hagi gent a les botigues que no tingui ni idea i que estigui venent ordinadors i assessorant a la gent. Jo també he sospitat de la pila. 

Un altre símptoma que diu que difícilment pot tenir a veure amb l'Ubuntu és que ha començat a empitjorar progressivament, ja em diràs com pot passar això si el culpable és l'Ubuntu.

Una cosa semblant li passa a un ordinador Hewlett Packard d'una filla meva, i ells el que ens van dir és que és un problema de càrrega d'electricitat estàtica de la placa mare. Mai no l'hem pogut arreglar. En el seu cas s'ha de desendollar, treure la pila, i mantenir la tecla d'engegar premuda per una estona, i això descarrega l'electricitat estàtica. Després de fer això comença a arrencar correctament per un temps fins que li comença a passar un altre cop i s'ha de tornar a repetir aquest procés de descàrrega.

Per demostrar-los que l'Ubuntu no té res a veure el que pots fer és fer còpia de tot, reinstal·lar Windows o fer una instal·lació de recuperació del Windows (això farà que el Windows sobreescrigui el grub, però en principi no esborrarà la partició on està instal·lat l'Ubuntu, perquè el Windows està tan mal programat que no veu la partició de Linux), provar si ara arrenca el Windows sense fer això que descrius. Si continua passant doncs tornes a la botiga, si s'arregla em deixaria ben sorprès. Si finalment t'ho arreglen, es pot recuperar l'Ubuntu amb un CD o USB autònom, i seguint les instruccions que es donen aquí:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Si hi hagués algun problema amb la recuperació de l'Ubuntu  i tens la còpia de seguretat sempre hi ha l'opció de reinstal·lar i recuperar les dades de la còpia de seguretat.

---

### Post by jinglada on 2013-06-16
Gràcies, wgarcia. 

Només desendollant ja s'arrenca normalment. Ara entenc com al botiguer no se li va bloquejar cap de les dues vegades que el va engegar perquè ho va fer sense endollar-lo. El que va desorientar al botiguer va ser que en el grub encara hi havia les línies d'arrancada i recuperació de W2 i quan les va clicar, no li van funcionar perquè el W2 ja el vaig desinstal·lar l'octubre passat seguint l'enllaç que tu em vas facilitar en aquest [fil]("http://ubuntuforums.org/showthread.php?t=2076920"), després de fracassar varis cops en la reinstal·lació i ara no tinc ganes de tornar a complicar-me la vida. El que si que faré és enviar-los un missatge explicant el que em dius per si els pot servir en el futur.

Una altra cosa que he solucionat és el tema del fitxer /etc/default/grub que [no existeix en el meu ordinador]("http://ubuntuforums.org/showthread.php?t=2064387") i és que sembla ser que la meva instal·lació (no sé per què) funciona segons he llegit al final d'aquest [fil]("http://ubuntuforums.org/showthread.php?t=1779149") amb /boot/grub/menu.lst, que ja he editat i he eliminat les entrades de W2.

---

### Post by wgarcia on 2013-06-16
Això que dius que la teva instal·lació fa servir /boot/grub/menu.lst vol dir que encara fa servir el Grub versió 1, i no la versió 2 com es fa servir ara. Jo et recomenaria actualitzar a la versió 2 (que és la que fa servir /etc/default/grub) perquè la versió 1 ja no està suportada en cap distribució. Aquí hi ha instruccions sobre com actualitzar-se a la versió 2:

[https://help.ubuntu.com/community/Grub2/Upgrading](https://help.ubuntu.com/community/Grub2/Upgrading)

---

### Post by jinglada on 2013-06-16
Òndia, ho veig una mica complicat. Em pots dir si és això el que he de fer?
1) sudo apt-get update
2) sudo apt-get install grub-pc
3) sudo upgrade-from-grub-legacy

---

### Post by wgarcia on 2013-06-17
A més d'això la pàgina explica que pots provar primer la versió Grub 2 (des de la versió anterior) i un altre punt important és que has de saber on està instal·lat el Grub (normalment /dev/sda però potser en algun altre lloc). Si tens dubtes,  com que és un tema delicat perquè pot deixar-te sense capacitat d'arrencar el sistema, potser el pots deixar com està i quan tinguis ocasió de tenir a prop algun que et pugui donar una mà si alguna cosa va malament, l'actualitzes.

---

### Post by jinglada on 2013-06-17
> **wgarcia said:**
> A més d'això la pàgina explica que pots provar primer la versió Grub 2 (des de la versió anterior) i un altre punt important és que has de saber on està instal·lat el Grub (normalment /dev/sda però potser en algun altre lloc). Si tens dubtes,  com que és un tema delicat perquè pot deixar-te sense capacitat d'arrencar el sistema, potser el pots deixar com està i quan tinguis ocasió de tenir a prop algun que et pugui donar una mà si alguna cosa va malament, l'actualitzes.

Gràcies wgarcia!

---

### Post by sianeu on 2013-06-22
A mi també em va passar fa pocs mesos. Al principi de tant en tant, després mes sovint, al final cada dia. Al principi es solventaba desconnectant la font d'alimentació (el meu es sobretaula), prement el botó d'arrancada i tornant a connectar i engegar. Després fins i tot això fallava sovint.

Pensava que hauria de canviar la placa base. Però vaig pensar que potser era el software de la bios que, per alguna raó s'havia corromput una mica. Per sort hi havia una actualització de la bios disponible i va resultar fàcil. No he tingut mes problemes.

La informàtica, a vegades, té coses ben estranyes. En fi, si us serveix......

Salut

---

### Post by jinglada on 2013-06-23
> **sianeu said:**
> A mi també em va passar fa pocs mesos. Al principi de tant en tant, després mes sovint, al final cada dia. Al principi es solventaba desconnectant la font d'alimentació (el meu es sobretaula), prement el botó d'arrancada i tornant a connectar i engegar. Després fins i tot això fallava sovint.

Pensava que hauria de canviar la placa base. Però vaig pensar que potser era el software de la bios que, per alguna raó s'havia corromput una mica. Per sort hi havia una actualització de la bios disponible i va resultar fàcil. No he tingut mes problemes.

La informàtica, a vegades, té coses ben estranyes. En fi, si us serveix......

Salut

Gràcies sianeu. Ho tindré en compte. De moment engegant sense connectar l'adaptador no dóna el problema. Ara que hi penso, de vegades també es parava durant l'engegada amb el missatge que s'havia superat la temperatura i ara tampoc ho fa. Creuaré els dits ... ;)

Salut, igualment.

---

### Post by jinglada on 2013-07-17
No trobo la manera de posar el "[Solved]"; a veure si funciona posar [Solucionat] a mà despres de "Re:"?

Doncs no funciona :-(

---

### Post by wgarcia on 2013-07-18
Has d'editar el primer missatge teu, i clicar "Go advanced", aquí veuràs una opció per posar "Prefix" i una d'elles és "Solved".

---

### Post by jinglada on 2013-07-18
> **wgarcia said:**
> Has d'editar el primer missatge teu, i clicar "Go advanced", aquí veuràs una opció per posar "Prefix" i una d'elles és "Solved".

Gràcies, un cop més :), wgarcia, però és que a les "[normes d'or]("http://ubuntuforums.org/showthread.php?t=599965")" que tu mateix enllaces, hi diu això:

> 
12.- Acabeu amb una nota sobre la solució

Com a conseqüència directa dels punts anteriors, és important acabar el fil explicant, si no s'ha fet abans, com s'ha arribat a la solució del problema. De pas, aprofiteu per marcar el fil com a resolt [SOLVED].

Això ho podreu fer un cop us identifiqueu amb el vostre usuari i contrassenya i anant al damunt del fil, fent clic a "Thread tools" i marcant l'opció "Mark this thread as solved". Tingueu present que això només ho podrà fer qui ha creat el fil o un dels moderadors del fòrum.

I a "Thread tools" no hi apareix  l'opció "Mark this thread as solved".

---

### Post by wgarcia on 2013-07-18
Gràcies, això està desactualitzat, però no puc editar aquest missatge perquè no tinc permisos per fer-ho...

---

### Post by jinglada on 2013-07-18
> **wgarcia said:**
> Gràcies, això està desactualitzat, però no puc editar aquest missatge perquè no tinc permisos per fer-ho...

I l'autor papapep no ho podria actualitzar? 

El que no entenc és aquest [http://ubuntuforums.org/showthread.php?t=2152985](http://ubuntuforums.org/showthread.php?t=2152985) que ha posat [Solucionat] en lloc de [SOLVED]. Com ho deu haver fet?

Edito: Ja ho he vist; ho poses en el títol en el mateix procediment que m'has dit de posar el [SOLVED]

---

