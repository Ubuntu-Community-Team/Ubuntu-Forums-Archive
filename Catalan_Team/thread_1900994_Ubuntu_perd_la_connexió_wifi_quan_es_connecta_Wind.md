---
title: "Ubuntu perd la connexió wifi quan es connecta Windows"
date: 2011-12-27
forum: Catalan Team
---

### Post by miquel6 on 2011-12-27
Hola a tots.
Tinc la següent instal·lació a casa:
* Internet amb Ono
* PC amb windows XP connectat per cable al cable-módem
* PC amb ubuntu connectat amb un USB-Wifi
* Netbook amb windowsd XP connectat amb Wifi

Normalment empro Ubuntu per tot i em funciona internet perfectament per wifi. Però quan encenc el PC amb windows, la connexió a internet del PC amb Ubuntu deixa de funcionar, o va escandalosament lenta: les pàgines deixen de carregar (chrome o firefox), si faig un ping o no respon o tarda moltíssim.

Quan em falla l'ubuntu, si poso el netbook amb Wifi si que em funciona. A la pàgina del router veig els tres ordinadors connectats, però el d'ubuntu no funciona.

Si aturo el PC que està connectat al cable-módem, el PC amb ubuntu torna a funcionar.

La connexió wifi a l'ubuntu no es talla en cap moment, només deixa de rebre informació: si vaig al monitor del sistema -> historial de xarxa, veig com s'envia informació però no se'n rep cap.

Se que sona una mica estrany, però com puc saber el que està passant? 

Moltes gràcies

---

### Post by wgarcia on 2011-12-28
Pots veure al configuració de l'enrutador quins IP assigna a cada ordinador?

---

### Post by miquel6 on 2011-12-29
> **wgarcia said:**
> Pots veure al configuració de l'enrutador quins IP assigna a cada ordinador?

Si, tots tenen IP diferent.
No he dit gaire cosa a l'anterior post. Els equips Windows són XP i l'Ubuntu és l'11.04

---

### Post by wgarcia on 2011-12-29
Hi ha una petita utilitat, nm-tool, que et mostra els paràmetres de la connexió. 

Per intentar entendre el que està passant, es tractaria doncs d'obrir una terminal, i entrar

```
nm-tool
```

primer quan el PC no està connectat i la connexió d'Ubuntu està funcionant bé, i després amb el PC connectat i l'Ubuntu sense connectivitat. 

Potser la diferència entre una situació i l'altra comenci a mostrar alguna cosa.

---

### Post by papapep on 2011-12-30
Has mirat les adreces MAC de les plaques de tots 3 ordinadors? que no hi hagi alguna història de filtrat o permisos al módem en funció d'això i que la del pc no tingui prioritats rares....
Un cop res no quadra, tota idea (ni que sigui boja) pot portar a la solució ;)

Salut.

---

### Post by miquel6 on 2012-01-04
Hola a tots, ja està solucionat.

No us creureu el que era, fins que la meva parella m'ho ha dit.

Resulta que fa unes setmanes vaig afegir un nou disc al PC amb windows i com que és una caixa mini-barebone, no vaig poder tancar el lateral de la caixa perquè el connector del cable SATA surt una mica (i encara n'he d'anar a comprar un).
Resulta que per questions d'espai el tinc a sobre d'una estanteria, i just al costat (del lateral que tinc ara obert), hi ha el cable modem. 

Idò la meva parella m'ha dit de moure el cable-modem de lloc... i voilà!

Resulta que eren les radiacions de la caixa que afectaven al wifi. Es veu que a la wifi del portàtil no li afectaven tant les radiacions, però al USB-wifi que tinc a l'ubuntu no li agraden gens.

Ja veis, de vegades un punt de vista extern és el millor per solucionar els problemes. Ja duia setmanes que li donava voltes i no hi havia manera. 

Gràcies a tothom!

---

### Post by wgarcia on 2012-01-05
Amb "Thread tools" pots marcar el fil com "Solved" i així queda marcat que s'ha solucionat.

---

