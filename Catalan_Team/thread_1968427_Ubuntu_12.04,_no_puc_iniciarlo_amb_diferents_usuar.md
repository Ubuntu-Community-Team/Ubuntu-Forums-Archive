---
title: "Ubuntu 12.04, no puc iniciarlo amb diferents usuaris"
date: 2012-04-29
forum: Catalan Team
---

### Post by akyra on 2012-04-29
Hola,

He acabat d'instalarme la versió 12.04 de 64 bits, i després de posar tot el programari que em feia falta vaig a iniciar Ubuntu amb un usuari diferent i em retorna tota l'estona a la pantalla del LightDM i no puc inicar la sessió amb un usuari que no sigui el meu.

El meu usuari es administrador i els altres usuaris estandards.

Em sembla molt fort que es llenci una distribució LTS i que una cosa tan bàsica no funcioni, em tenen l'ordinador parat !!

Bé, si algu té idea de que pot ser li agrairia ajuda.

Salutacions

---

### Post by akyra on 2012-04-30
Hola,

Volia preguntar si algú fa servir més d'un usuari al seu ordinador i li funciona bé.

Salutacions

---

### Post by kimet on 2012-04-30
Verifica a quins grups pertanyen els usuaris. 
```
Groups usuari
```
Estan al grup gdm o gdm3?. 

Salut.

---

### Post by akyra on 2012-04-30
Hola Quimet,

Excepte el meu usuari, els altres nomes pertanyen al seu propi grup, o sigui:
laia : laia

El meu usuari, que és el que funciona té:
jordi: jordi adm cdrom sudo dip plugdev lpadmin sambashare

Salutacions

---

### Post by kimet on 2012-04-30
Si aquests usuaris tene home propia, verifica que els pertany a ells,
i  si hi ha un fitxer .ICEauthority o .Xauthority que sigui de la seva propietat. 
Si cal pots esborrar aquests fitxers, es tornaràn a crear.

No s'em acud res mes.

---

### Post by akyra on 2012-04-30
Hola Quimet,

Ets lo puto crack!!

Si senyor, les /home i els fitxers ".ICEauthority" i ".Xauthority" estan creuats, o sigui que el que és de la meva dona es propietaria la meva filla i a l'inrevés. També tinc tots els altres fitxers i carpetes amb permisos creuats.

Com puc canviar tots a la vegada? 
Pel moment ho estic fent amb el botó dret en el Nautilus com a root i ho canvio, però quan faig "aplicar permiso als arxius continguts" no m'ho canvia.

No ho entenc com ha pasat ??
Jo només vaig fer un "sudo adduser laia" i el mateix per la dona

Salutacions.

---

### Post by akyra on 2012-04-30
Finalment he fet un "chown -R laia:laia" i el mateix per la dona i em deixa començar la sessió de la dona però no la sessió de la nena.

Estic perdudisim.

---

### Post by kimet on 2012-04-30
Has provat:
```
chown -R /home/laia
```

---

### Post by akyra on 2012-04-30
Ja ho havia fet i no funcionava.
Finalment he hagut d'esborrar l'usuari i crear-ne un de nou.

Ara tot funciona, però deunidó quin bug.

Bé, moltes gracies per l'ajuda i ara ho marcu com solucionat.

També ho havia enviat a launchpad.

Adeu

---

### Post by wgarcia on 2012-05-01
És estrany el que t'ha passat, he mirat i no he trobat cap informe d'error semblant recent. 

El que sí hi ha és un informe d'error del "lightdm", que és l'aplicació d'inici on es mostren els usuaris, perquè no dóna cap informació quan l'usuari no pot escriure sobre la seva carpeta d'inici:

[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/861330](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/861330)

Però em sembla estrany que a l'actualització s'hagin canviat els propietaris de les carpetes d'inici, i certament no he vist altres casos semblants. Per aquest cicle de l'Ubuntu s'ha insistit molt en la qualitat de l'actualització i em consta que des de fa dos mesos s'han fet tot tipus de proves d'actualització per intentar minimitzar els possibles errors. I mirant els informes d'error crec que en gran part s'aconseguit, perquè al cicle anterior (11.10) hi havia moltíssims més informes d'actualitzacions fallides.

---

### Post by akyra on 2012-05-01
Jo primer vaig fer una actualització de la versió 11.10 a la 12.04 però quan semblava que ja estava acabant es va quedar unes 4h actualitzant programes antics, i vaig decidir instal·lar-lo des de zero formatejant la partició "/".

Després, una vegada instal·lat, nomes vaig fer va ser un "sudo adduser laia" i el mateix per la meva dona. El que jo no esperava que es "confongués" de propietari del directori /home.
Potser el que va canviar va ser la id del usuari que estava relacionada amb el directori /home, això ja no ho sé.

Vaig obrir aquest cas amb el launchpad:
[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/990948]("https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/990948")

Això que dius que s'han fet moltes proves abans de fer aquest llançament, suposo que sí, però em van sortin informes de fallo per enviar a Ubuntu alguna que altre vegada i no sé a que es deuen.

Salutacions.

---

