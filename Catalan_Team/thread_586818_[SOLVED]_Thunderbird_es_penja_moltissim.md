---
title: "[SOLVED] Thunderbird es penja moltissim"
date: 2007-10-22
forum: Catalan Team
---

### Post by trinkus on 2007-10-22
Ep gent... a veure si algu s'hi ha trobat o sap com solucionar-ho...

El Thunderbird es penja quan trio llegir algun missatge. Evidentment no sempre. Si el faig servir una estona.... de cop, canvio de missatge i s'esvaeix... i quan el torno a engegar (reiniciant i tot) segueix succeint. Nomes deixa de passar si el reinstal·lo amb el synaptic pero al cap d'un temps (indefinit) em passa igual. Es una murga absoluta... que pot ser? Amb la Feisty no em passava... i ara la Gutsy es de trinca (no he fet update) i he exportat els missatges antics...

???

---

### Post by guitacm on 2007-10-29
A mi em passa exactament el mateix. Si he de fer un missatge un pèl llarg, he d'anar guardant per si de cas.

---

### Post by jmaspons on 2007-10-29
a mi sempre m'ha anat molt fi... encara que de moment no he actualitzat a gutsy :P

Quan tingui temps per actualitzar i poder solucionar els possibles problemes ja us comentaré com em va el thunderbird.

em sap greu no poder ajudar...

---

### Post by guitacm on 2007-11-02
He desactivitat l'alerta de missatges nous, i he tret totes les extensions que tenia. Ara sembla que funciona bé.

---

### Post by eselma on 2007-11-02
També tinc el Thunderbird de la Gutsy (2.0.0.6 - 20071022 si no m'erro) amb el sac de missatges antics importats. Sense haver-ho activat, rebo avís gràfic i acústic de missatges nous. No m'ha donat problemes en aquesta versió (Kubuntu 7.10 intel 32). Abans hi tenia alguna extensió (potser pe r*phishing* i el corrector ortogràfic)  però ara ja no en tinc cap. 

Les extensions estan fora del control de Mozilla i, encara que fetes amb les millors intencions, a vegades presenten inconsistències, sobretot entre elles. Potser el teu problema vingui d'aquí.

---

### Post by trinkus on 2007-11-04
Jo tambe sembla que ho he solucionat i apunto a dues solucions, a veure si els experts saben veure quina es la bona:

1.-Tenia dos thinderbird instal·lats (un del paquet thunderbird i un altre del mozilla-thunderbird que es una mena de paquet de transicio segons diu el synaptic). En vaig desinstalar un i ara va to be. Es la cosa me sprobable

2.- La versio de Lightning que tenia no era compatible... pero no recordo que vaig fer

Personalment crec que el problema venia de 1, per tant, els que us passa el mateix mireu si es aixo. Entremig tambe em vaig trobar que els de mozilla van fer una actualitzacio del thunderbird pero crec que no era un bug que solucionessin...
D'altra banda jo no he variat es meves opcions pel que fa a res, per tant, ha de funcionar...

---

### Post by eselma on 2007-11-05
Per raons "històriques" també tenia al meu directori personal el directori *.mozilla-thunderbird*. En realitat, entre aquest i el* .thunderbird* només hi ha el primer amb contingut, l'altre és un enllaç tou (*ln -s*). Ara mateix no recordava si encara estaven actius els dos (atès que al directori */usr/lib/* tant el* firefox* com el* thunderbird* finalment han agafat autonomia i s'han després de l'arrel *mozilla-*. Doncs si, encara tinc els dos i va tot bé. Després en deixaré un de sol.

En qualsevol cas, a mi sempre m'ha anat bé des de la versió 0.7, passant per la 1.0.xx, 1.5,xx i ara la 2.0.xx.

---

