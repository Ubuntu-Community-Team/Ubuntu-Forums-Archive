---
title: "requeriments minims"
date: 2009-08-17
forum: Catalan Team
---

### Post by mariasantos on 2009-08-17
tinc un pentium 4 1500 amb 512 mb de ram
amb ubuntu 9.04 amb servidor grafic gnome

des de q he canviat a linux x obrir una finestra o un programa tarda bastant, uns segons pero per eixample no puc navegar x varies webs a la vegada a una mateixa finestra de firefox pq va molt lent

i obrir mes d'un programa a la vegada es morir-se de paciencia i veure fotos imposible

potser q tinc q canviar de pc o es q he configurat mal el meu sistema?
gracies

---

### Post by Daerun on 2009-08-17
Potser et faria falta més RAM (1 GB)? Avui dia les webs tenen quantitat d'imatges, i flash, i java i coses rares i de seguida carreguen de feina l'ordinador...

---

### Post by CarlesOriol on 2009-08-18
> **Daerun said:**
> Potser et faria falta més RAM (1 GB)? Avui dia les webs tenen quantitat d'imatges, i flash, i java i coses rares i de seguida carreguen de feina l'ordinador...

Home, 512 mb son suficients per moure la màquina sense fer grans acrobacies.

---

### Post by indiosincracia on 2009-08-18
Jo l'overclockingaria un 10% i posaria 2GB de Ram, amb un pentium 4 encara en tens per uns quants mesos ... o anys :)

---

### Post by Miquel Ubuntero on 2009-08-18
Dons fins fa poc tenia en un portàtil amb 512 MB de Ram un Xubuntu instal·lat en un disc dur extern usb i hem funcionava de conya. Internet, vídeos, tot be.
Xubuntu és, per dir-ho d'alguna manera, l'Ubuntu per ordinadors "justets".
Si vols més info:
[http://miquel66.caliu.cat/](http://miquel66.caliu.cat/)
[http://www.xubuntu.org/](http://www.xubuntu.org/)
Salut!

---

### Post by RicardKp on 2009-08-19
> **indiosincracia said:**
> Jo l'overclockingaria un 10% i posaria 2GB de Ram, amb un pentium 4 encara en tens per uns quants mesos ... o anys :)
Hola a tothom,

Hi ha alguna aplicació a l'Ubuntu per overclockingar? i per mesurar la temperatura, no sigui cas que fongui la CPU?

Salut!

---

### Post by pauelmaco on 2009-08-19
> **RicardKp said:**
> Hola a tothom,

Hi ha alguna aplicació a l'Ubuntu per overclockingar? i per mesurar la temperatura, no sigui cas que fongui la CPU?

Salut!

Per a fer overclocking, pots probar això:

[http://www.econowics.com/linux/298/tutorial-overclocking-ubuntu-linux/](http://www.econowics.com/linux/298/tutorial-overclocking-ubuntu-linux/)

I per la temperatura, primer t'has d'assegurar que l'ordinador tingui sensors.

dew

---

### Post by indiosincracia on 2009-08-19
Això es pot fer de moltes maneres... "la física" canviant el jumper, (cal que tinguis el llibre d'instruccions de la placa base on explica quina pestanya s'ha de tocar) o des de la Bios, els Pentium's es deixen overcklocar sense massa problemes, això sí, s'ha de fer poc a poc, apuja un 5% (reengega l'ordinador prem "Supr" o "Dell" o "F2" depén del model), apareix el menú Bios sol ser semblant en tots els ordinadors, Advanced>overclock options>overclock> tecla "+" "-" per pujar o Baixar, F10 Save and Exit.

instal·la "lm-sensors" 

$sudo aptitude install lm-sensors
$sensors
(respon a totes les preguntes que et faci, però com diu en pauelmaco, els sensors dependran del model que tinguis)

rutlla tres o quatre dies, si tot va bé (si no es penja ni sofoca:oops:) posa'l a un 10%, si tot va be posa'l a 15% i si vols a 20 %.
Per experiència pròpia, un servidor col·labora en Boinc Catalunya i els nostres processadors acostumen a estar ben enllustrats! hi han maneres imaginatives de fer baixar la temperatura, treure la tapa de l'ordinador, deixar la placa base sobre una estanteria de ferro o d'alumini per que dissipi, o enfonsant-la en oli o posar-la a la fresca, 

el que més porta de cap és el voltatge, si et trobes l'ordinador penjat rebaixa un 5% l'overclocking, no es aconsellable pujar per sobre del 20% en els Pentium.

en quant als AMD s'acostumen a escalfar molt, tinc entés que en aquesta batalla del poder els AMD van una mica revolucionats ja de sèrie.

---

### Post by pauelmaco on 2009-08-20
> **indiosincracia said:**
> 
en quant als AMD s'acostumen a escalfar molt, tinc entés que en aquesta batalla del poder els AMD van una mica revolucionats ja de sèrie.

Jo en tenia un, i no anava gaire revolucionat, és més, no anava molt ràpid però en canvi si que s'escalfava molt. És més, el pobre ordinador es va morir d'això, el processador es va escalfar massa :cry:. Per això, més val un intel que un AMD.

---

### Post by RicardKp on 2009-08-20
Moltes gràcies a tots, ja me n'he sortit per la bios és facilíssim, a més també em diu les temperatures. l'únic que no he trobat ala bios del meu pentium IV 2800 i que la viquipèdia en parlava és del factor de multiplicació, que sembla ser que overclockeja tota la bios.

Salut
Ricard

---

### Post by SiscoGarcia on 2009-08-23
Si us plau, no perdeu el nord que això és un SO intel·ligent... al menys ho és més que d'altres i, com diu el Carles, no ens cal cap meravella tecnològica d'última fornada per funcionar més que correctament.

Tinc a les mans un CD original d'ubuntu 9.04 amb gnome, i a l'apartat "System requirements" hi diu textualment: "To use Ubuntu you should have a PC with at least 256 MB of RAM. To install Ubuntu, you should have at least 4 GB of disk space. [...]"; així que em temo mariasantos que el problema no és d'espai de disc, potser tens el disc dur físicament petat o no l'has instal·lat bé.

Per què no proves de fer còrrer el CD autònom a veure què tal va? Si et funciona bé, llavors pots reinstal·lar-te l'ubuntu un altre cop.

Per cert, per què no et passes pel fil de benvinguda i ens expliques alguna cosa sobre tu?

Ja diràs.

---

