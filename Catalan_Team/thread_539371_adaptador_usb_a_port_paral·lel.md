---
title: "adaptador usb a port paral·lel"
date: 2007-08-31
forum: Catalan Team
---

### Post by muleta on 2007-08-31
He trobat el driver del meu Scanmagic 1200cp per a Linux. Ara només em falta l'adaptador usb a port paral·lel i també el que ha de connectar l'scanner amb l'impressora.](*,)

En trobo per a Windows però encara no per a Linux. Ens en sortirem de fer-ho funcionar tot?.:-k

---

### Post by papapep on 2007-08-31
> En trobo per a Windows però encara no per a Linux

De què, de cable adaptador USB -> RS232?

---

### Post by muleta on 2007-08-31
Sí, deu ser que porten un driver per fer-los funcionar només en l'entorn windows.

---

### Post by muleta on 2007-08-31
> **papapep said:**
> De què, de cable adaptador USB -> RS232?

Però aquest que em dius, és el port sèrie petitó oi?. Em sembla que no és el port paral·lel o d'impressora (LPT1 em sona)

---

### Post by papapep on 2007-08-31
Sembla ser que d'experiències d'aquests adaptadors de USB a port paral·lel hi ha experiències de tot. N'hi ha que els funciona sense haver de fer res més que endollar, i d'altres que expliquen el contrari. 

Serà qüestió de provar-ho.

Per cert, aquí en tens alguns: [http://www.optize.es/servlet/showProductsSearch?pag=1&orden=9&modo=false](http://www.optize.es/servlet/showProductsSearch?pag=1&orden=9&modo=false)

---

### Post by muleta on 2007-08-31
> **papapep said:**
> Per cert, aquí en tens alguns: [http://www.optize.es/servlet/showProductsSearch?pag=1&orden=9&modo=false](http://www.optize.es/servlet/showProductsSearch?pag=1&orden=9&modo=false)

Tots indiquen que són per a Windows. És possible que funcionin iigualment?.

---

### Post by papapep on 2007-08-31
No tinc experiència al respecte, per això t'he dit abans "que era qüestió de provar-ho".

---

### Post by eselma on 2007-09-01
> **muleta said:**
> Tots indiquen que són per a Windows. És possible que funcionin iigualment?.

En el teu cas ( un escàner, crec ) necessites segurament un port paral·lel i el corresponent cable que suporti tràfic bidireccional complert ( crec que és ECP o semblant ). Pensa que la velocitat de transferència serà baixa si escaneges a gran resolució.

Quant als adaptadors port-USB, només n'he provat de port sèrie ( el RS232 que esmentàveu abans ). L'ubuntu *Edgy* i el *Feisty* el reconeixien a la primera, tot i que em sembla que li donaven un altre nom ( mira al directori /dev/ ) ; les proves "manuals" amb* loopback* anaven bé, però... la connexió amb l'aparell que necessitava (un *palmtop* PSION) no rutllava pas. Amb cap dels dos que he provat, un d'ells Conceptronic.

Com deia el Pep, crec que, si no son molt cars, potser val la pena provar-los primer ( especialment si es tracta d'una compra condicional ) : pots trobar resultats de tota mena. 

En qualsevol cas, si no funciona, pensa que la connexió d'escàners per port paral·lel ja és obsoleta ( i lamentablement, sembla que també per impressores ) . Si no funciona l'invent, et pots preguntar si a la teva filla li convé un escàner...  :)

---

### Post by muleta on 2007-09-14
El tinc!!!!. He trobat l'adaptador a Hong Kong, després de patejar totes les grans superficies informàtiques de Barcelona i contactar amb els principals fabricants de cables i adaptadors.

Ja el tinc a casa i l'he connectat a l'scanner i al pc però, com que el Xsane no veu  el perifèric, he pensat que potser és culpa de l'adaptador. Porta un driver per a linux però li dec donar l'ordre malament perque el terminal diu que no el localitza.

Com li he de dir que està en el CD?.

---

### Post by papapep on 2007-09-15
Nosaltres no tenim ni el CD amb el controlador, ni els fitxers que tens tu on deuen ser les instruccions (suposo). Ni tan sols ens has dit la marca de tot plegat....
Si no ens dones més pistes, ho tenim un pèl de res complicat.... :-)

---

### Post by muleta on 2007-09-16
El cable no té marca o ho diu en xinès. Porta un mini-cd amb el driver. Hi ha dues carpetes: la 2.0-PCLink 2501 i la Driver.

D'instruccions no en trobo enlloc. A la Driver, si obro la subcarpeta 810Driver, n'hi ha una altra anomenada Linux que conté 3 subcarpetes Redhat8, Redhat9 i Redhat73.

No sé si serveixen de res o no cal que continüi...

---

