---
title: "Com editar l'arrencada i triar el SO per defecte?"
date: 2009-05-01
forum: Catalan Team
---

### Post by carevolta on 2009-05-01
Hola, hui per curiositat i perquè és un aparell bastant antic, he instal·lat Xubuntu 9.04 a un ordinador. Tanmateix, l'usuari vol continuar utilitzat l'Ubuntu. Cap problema, m'he dit, després edite /boot/grub/menu.lst i per defecte faig que entre a Ubuntu. A més, aquests detall té la seua importància per no confondre't amb tantes entrades gairebé idèntiques (al llistat totes s'anomenen Ubuntu..., no Xubuntu). 
Doncs bé, en algun pas, m'he equivocat o bé he creat unes particions pròpies d'un aprenent massa atrevit, però el cas, és que no ho aconseguisc. 
L'arrancada continua igual. He provat també amb l'StartUp-Manager i ni s'immuta. Us adjunte algunes línies del /boot/grub/menu.lst. He canviat els títols d'algunes entrades a Xubuntu i allò del "Other operative systems" he provat a traduir-ho al català, res més.
Alguna instrucció o suggeriment? Una abraçada des de València!

---

### Post by kimet on 2009-05-01
Has d'editar el menu.lst amb un editor de text plà, (nano, gedit, emacs....) i com a root. 

Per canviar l'entrada per defecte, s'ha de canviar el número d'alla hon hi diu "default..    0" per el numero de la linia que vols que arrenqui per defecte, tenint en compte que la primera linia es "0". En el teu cas sería "2".

Salut.

---

### Post by carevolta on 2009-05-01
Gràcies, Kimet. Vols dir que la línia 2 correspon a l'entrada que adjunte, l'Ubuntu 9.04 que apareix després de ### END DEBIAN AUTOMAGIC KERNELS LIST? Jo entenia que les 2 primeres entrades corresponen a Xubuntu (ho he modificat jo per aclarir-me), les següents al kernel anterior d'Ubuntu i les últimes a Windows XP i el kernel actual d'Ubuntu.
A banda d'això, continue sense saber perquè no fa cas quan modifique o agregue comentaris (per exemple: "altres sistemes operatius") ni perquè tampoc em respon l'StartUp-Manager. Supose que per poca perícia. Vaja no és res urgent, és un detall que faria més senzilla l'arrancada, però ho seguiré provant.

---

### Post by kimet on 2009-05-01
Tens raó no m'havia donat compte de que hi tenies mes kernels.
De totes maneres, quant et surt el grub al arrencar, comptes les línies començant desde cero i ja està.
Em sorprén que enganxis les sortides en ODT, segur que fas servir un editor de text plà? Openoffice no serveix.

Salut.

---

### Post by carevolta on 2009-05-01
Si ho he provat tal com em dius, encara que així correspon a la línia 6, i tot segueix igual. Vaja, hui se m'acumulen les errades. Si, clar, utilitze gedit, però no els havia guardat en .txt i m'era més fàcil en aquell moment pujar un .odt. Gràcies de nou!

---

### Post by kimet on 2009-05-01
No sé que pot ser. Si després de editar el GRUB , el que hi ha al xubuntu, amb ```
$ sudo /gedit/boot/grub/menu.lst
```
No ho sé.

Salut.

---

### Post by papapep on 2009-05-01
Uns comentaris, carevolta:

1) Fixa't al menu.lst, que totes les entrades apunten al mateix disc-mateixa partició, o sigui que és evident que sempre et sortirà el mateix.

2) Per provar Gnome o KDE o el que sigui, no cal reinstal·lar tot el sistema operatiu de nou.

3) Per triar l'entorn d'escriptori predeterminat es fa al Gdm (o Kdm o Xdm), allà on et demana l'usuari i contrasenya, fes clic a opcions i digues-li amb quin entorn vols arrencar.

4) Per adjuntar text no cal crear un odt, que ens obliga a obrir l'OpenOffice (gran programa, però no és l'ideal per a aquestes tasques). Amb un simple .txt (si consideres que és massa llarg per enganxar-lo directament al fòrum) ja fem el fet ;)

---

### Post by socderafel on 2009-05-01
prova amb el startup-manager. és un programa que et fà l'edició del grub.lst de forma gràfica.

---

### Post by carevolta on 2009-05-01
Anem a pams: 
1. Socderafel, ja he provat amb el startup-manager, ho deia als primers missatges, però no em respon
2. Papapep, aleshores entenc que no puc triar el SO que arranque per defecte?
3. Ei, ja ho sé, que amb afegir xubuntu o kubuntu-desktop els podíem provar, però el propòsit no era aquest, sinó aprofitar un espai lliure per instal·lar Xubuntu. Potser no ha estat una bona decisió.
4. Ja ho sé per a la pròxima, pujaré els adjunts amb .txt

Doncs, res, continuarem aprenent, que d'això es tracta.

---

### Post by papapep on 2009-05-01
> Anem a pams:
2. Papapep, aleshores entenc que no puc triar el SO que arranque per defecte?

Tal i com ho tens ara, no. Has de configurar correctament les entrades del menu.lst.

Suposem que tens el SO que vols configurar a la 4a partició del 1r disc, aleshores hauries de posar:

```
root		(hd0,3)
```

> 3. Ei, ja ho sé, que amb afegir xubuntu o kubuntu-desktop els podíem provar, però el propòsit no era aquest, sinó aprofitar un espai lliure per instal·lar Xubuntu. Potser no ha estat una bona decisió.

Home, si és un ordinador "de proves", potser ho faria així. Però tenir diverses instal·lacions per a diversos entorns d'escriptori, tot i ser perfectament possible, és matar mosques a canonades :)

---

### Post by oriolsbd on 2009-05-01
Hola, quin "menu.lst" estàs modificant? El que tens a Ubuntu o el que tens a Xubuntu? Si estàs modificant el menu.lst de Ubuntu, prova de fer les modificacions al de Xubuntu (que crec que és on ho hauries de fer). En canvi, si estaves fent les modificacions al menu.lst de Xubuntu, prova de modificar-ho a Ubuntu.

Pensa que a tots dos entorns hi tens un fitxer /boot/grub/menu.lst, però el Grub només fa cas a un d'ells per saber les opcions de menú que t'ha de presentar. Quan has instal·lat Xubuntu, suposo que deus haver instal·lat també el Grub, de manera que per això suposo que et deu estar apuntant al menu.lst de Xubuntu. Però si no has reinstal·lat el Grub, et deu apuntar al menu.lst d'Ubuntu.

Espero no haver-me liat massa amb l'explicació, però crec que hauria de funcionar. :-)

Salut!

---

### Post by carevolta on 2009-05-01
Ep, ja ho he arreglat. L'entrada que corresponia a "default" era, en el meu cas la 5. Pel que entenc i és important: no només cal començar a contar des de 0, i no des d'1, sinó que aquella línia inútil de "Other operating systems" també compta. Ara, Xubuntu apareix a sobre del tot, però quan inicie l'ordinador està ressaltat Ubuntu i hi entra al 10 segons. I només fa cas editant des de Xubuntu, l'entorn que "mana", per expressar-ho d'alguna manera.
Bo, és la meua solució, però no sé si donar per tancat el fil. Gràcies de nou!

---

