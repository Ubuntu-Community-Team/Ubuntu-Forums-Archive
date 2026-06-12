---
title: "problemes de sobreescalfament"
date: 2011-06-11
forum: Catalan Team
---

### Post by knuss on 2011-06-11
Hola a tothom!!!

Des que vaig posar la 11.04 quan visualitzo vídeos amb flash s'escalfa tant la maquina 
que fins i tot s'arriba a parar .

A algú de  vosaltres  us passa igual ?  

Be doncs la maquina es un portatil Packard Bell un Tj66 a 7600  amb una grafica nvidia geforce gt 240 m  amb 4gb de ram ,,, 

Salut a tohom !!

Cesc

---

### Post by wgarcia on 2011-06-11
Pot ser un problema del nucli de linux actual combinat amb el controlador de NVIDIA que estàs usant. 

Estàs usant el controlador propietari? Ho pots mirar a Paràmetres del sistem (al menú de tancar) -> Maquinari -> Controladors addicionals.

---

### Post by knuss on 2011-06-12
Jo crec que si que el tinc posat , però no estic del tot segur ja que em diu que no el fa servir .Et poso una captura dels controladors a veure que et sembla.
De fet el Unity si em funciona i per aixó suposso que si el fa servir ,,,

Salut i gracies !!!

Cesc

---

### Post by kukat on 2011-06-12
No, no utilitzes els controladors privats de Nvidia! 
El sistema tindrà acceleració 3D però amb els controladors lliures

Pot ser podries provar a instal·lar els privatius i provar a veure si és eixe el problema

salut!

---

### Post by wgarcia on 2011-06-12
Això que diu que no l'està fent servir és un error reportat que ja està en via de solució:

[https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/771788](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/771788)

Si tens més d'una opció de controlador NVIDIA pots provar amb alguna altra opció que la que estigui marcada (sempre i quan tinguis clar com arreglar-ho si arrenques i et quedes sense interfície gràfica, normalment entrant en mode "recovery" et deixa tornar a posar el controlador gràfic anterior).

---

### Post by knuss on 2011-06-12
porto tota la tarda intentant arreglar-ho i en cap cas consegueixo que els activi , he instalat el 173 i no funciona , tambe he desinstalat els noveau display drivers i tampoc aconsegueixo activar-los de cap manera ....
Tanmateix crec que es veu que es bastant comú .... no se seguire investigan el tema ,,,

Moltes gracies


Salutacions >> 
Cesc

---

### Post by wgarcia on 2011-06-13
El controlador privatiu sí que està fent-se servir, tot i que digui al "Controladors addicionals" que no s'està fent servir (aquest aplicació que mostra "Controladors addicionals" es diu "jockey" i és la que produeix l'error). 

En la major part dels casos això no té conseqüències, en el meu cas per exemple diu que no l'està fent servir però funciona perfectament. En altres casos no funciona l'acceleració.

No sé si el problema de reescalfament està relacionat amb això o no, sembla relacionat amb el sistema gràfic i per això era el primer a mirar. 

Altres estratègies per intentar solucionar-ho:

1) Intentar mirar si a la pàgina d'Adobe tenen una versió més recent del "plugin" d'Adobe per visualitzar Flash.

2) Veure si hi ha algun nucli més antic al grub i intentar utilitzar-ho per veure si el problema se'n va.

3) Intentar instal·lar una versió més recent del nucli, aquesta opció és una mica més complicada i pot causar altres problemes perquè els nuclis més recents poden no estar plenament configurats per a l'Ubuntu.

---

### Post by kukat on 2011-06-13
Ostres, no sabia això del bug este....


També pots provar d'utilitzar la versió anterior d'Ubuntu. 

O provar amb KDE en lloc de Unity o GNOME... però clar, aixó igual ja és acostumar-se a altre entorn completament diferent. 
:P 


PD:Utilitze KDE....;)

---

### Post by wgarcia on 2011-06-13
Em sembla que aquest bug també està al Kubuntu 11.04.

---

### Post by quitus on 2011-06-13
Per tal d'actualitzar el flash, hi ha una extensió anomenada flash-aid per firefox que ho facilita  moltíssim.

salut

---

### Post by knuss on 2011-06-19
Be de moment i des de que he actualitzat el flash ja no em passa , 
, jo també crec que tot i que diu que no fa servir els drivers privatius que te instalats crec que si que els utilitza ,,,


moltes gracies per les vostres respostes !!

Salut a tothom!!!

Cesc

---

