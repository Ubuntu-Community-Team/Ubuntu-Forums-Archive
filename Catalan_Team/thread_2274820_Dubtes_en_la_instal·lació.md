---
title: "Dubtes en la instal·lació"
date: 2015-04-22
forum: Catalan Team
---

### Post by Ddac on 2015-04-22
Hola, ja vaig tenir un ensurt gran fa uns mesos en la instal·lació d'ubuntu en un ordinador d'un familiar i no voldria cometre el mateix error. La qüestió és que m'he comprat un ordinador nou i vull instal·lar ubuntu al costat del windows per necessitat (si pogués instalaria ubuntu i prou). El disc dur d'aquest ordinador conté cinc particions (que venen de fàbrica)  les quals apareixen en la imatge que adjunto. La meva pregunta és: si instal·lo ubuntu al costat de windows amb la opció automàtica, em suprimirà tot aquest seguit de particions, que pel que tinc entès, pertanyen al recovery de l'ordinador (recuperació dels valors inicials)??? Si degut a això hagués de triar la instal·lació manual, tinc entès que només poden haber quatre particions primàries en un disc dur, com puc saber quines de les cinc existents  són primàries o no?

El motiu pel qual exposo això, és perquè  una vegada  instal·lant ubuntu en un altre ordinador, es van formatejar totes les dades que havia un altre disc dur diferent al que instal·lava el SO. Degut a aquesta experiència, preferia preguntar prèviament a algú que tingués coneixement de causa.

Moltes gràcies

---

### Post by wgarcia on 2015-04-23
El teu disc té 5 particions primàries (si hi hagués una partició estesa, amb particions lògiques a dins, es es veuria per exemple

/dev/sda4       Extended
    /dev/sda5     ...
   /dev/sda6      ....

o quelcom semblant. 

Sembla que no està formatejat amb el MBR habitual sinó amb un sistema que es diu GPT que permet més de 4 primàries (i sols particions primàries). En principi segons tinc entès no hi ha problema per instal·lar Ubuntu en un sistema d'aquest tipus, i pots crear tantes particions primàries com vulguis.

Per veure si efectivament és un disc formatejat com GPT, es pot fer servir una utilitat que es diu "gdisk". Has d'obrir un terminal i entrar:

```
sudo gdisk -l /dev/sda
```

Si està fent servir GPT sortira quelcom del tipus:

```

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

```

al principi d'una sortida més llarga. Si és MBR sortiria:

```

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present

```

Si no és GPT no sé exactament què està passant amb les particions del teu disc.

---

### Post by Ddac on 2015-04-24
Moltes gràcies Wgarcia, acabo de veure que el gparted, quan l'inicio, em mostra aquests dos missatges (els quals adjunto en dues imatges i no sé què volen dir) on sembla que es confirma que està formatejat en GPT. Sön importants aquests dos missatges? O puc ignorar-los? I com a últim, si optés per la opció més fàcil (instalar ubuntu al costat de windows de forma automàtica), perillerien tot aquest seguit de particions?? O les respectaria? És on tinc l'altre dubte ja que encara no sé si optaré per la opció de muntar-me jo les particions o que les faci l'instalador automàticament.

Gràcies per endavant

---

### Post by wgarcia on 2015-04-26
Jo primer preparia un USB de recuperació del Windows, per si falla alguna cosa en la instal·lació i tenint en compte que el vols mantenir. 

En segon lloc li faria cas al gparted, i que arregli els problemes que troba.

En tercer lloc, faria la instal·lació "manual", reduint la mida de la partició principal del Windows (la de 900 GB),  i creant una partició formatejada en ext4 per a Ubuntu a l'espai alliberat. Després instal·laria l'Ubuntu a aquesta partició. 

Penso que si ho fas manual les probabilitats que perdis alguna de les particions que ja tens són menors.

---

### Post by Ddac on 2015-04-28
Sí, la còpia de seguretat ja la tenia feta merci. Ja vaig aprendre la lliçó en el seu moment. ;) 
Finalment he seguit el teu consell i he particionat manualment el disc dur amb el gparted i seguidament he instal·lat ubuntu 14.04. Tot correcte i rutllant. Per tant mooltíssimes gràcies pels consells wgarcia.
Només tinc un curiositat per comentar-te. Malgrat l'ordinador on ho he instal·lat és força potent ( i7 de 4a generació amb 12gb ram) trobo que la primera vegada que executo una aplicació en ubuntu, tarda força. Per exemple tarda més de 10 segons a obrir el firefox (sense carregar web). No és massa temps per les característiques del pc? (Òbviament la segona vegada que l'executo tarda milèssimes de segon, una vegada ja queda carregada en memòria). Em passa el mateix amb el thunderbird i demès aplicacions. Què pot ser? 

Gràcies

---

### Post by wgarcia on 2015-04-29
Algunes aplicacions com el LibreOffice sí que triguen més el primer cop, però el Firefox m'estranya que trigui tant, 10 segons em sembla excessiu. Mira d'iniciar-lo des d'una terminal amb l'ordre "firefox", i a veure si mostra algun missatge de coses que està fent abans d'obrir-se.

---

### Post by wgarcia on 2015-04-29
Per cert, si vols continuar mirant aquest tema, potser millor que obris un nou fil al fòrum amb un títol apropiat, i a aquest el marquis amb "Solved" obrint el teu primer missatge i escollint  "Thread tools" on veuràs l'opció de marcar el fil amb "Solved".

---

### Post by Ddac on 2015-04-29
I tant, gràcies. Ara m'hi poso. Dono el fil per tancat i resolt i n'obro un altre amb el l'arrencada lenta del firefox.

Salut!

---

