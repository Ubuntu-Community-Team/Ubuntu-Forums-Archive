---
title: "No veig el meu servidor des de internet"
date: 2009-12-02
forum: Catalan Team
---

### Post by blas.lopez on 2009-12-02
Hola a tothom,

   Us volia demanar alguna ajuda o indicació que em serveixi per solucionar el següent problema.

   Tinc un ubuntu amb una ip fixa on tinc un servidor web. A aquest servei web puc accedir perfectament indicant la url localhost, 127.0.0.1 o 192.168.1.20 (que és la seva ip fixa) i també puc accedir des de un altre ordinador amb la ip fixa.

   El problema que tinc és que no puc accedir des de el meu compte dyndns (es adir xxxx.dyndns.org) i no em troba el servidor. Fa uns dies em funcionava però no sé que em pot haver pasat (només he fet un update a karmic koala).

   La qüestió és que crec que no es resolt l'adreça des del router fins al servidor (al log del router apareix la petició) però no sé per què no arriba ni com buscar.

   Pensant que podia ser les iptables les he obert totes, doncs el router ja te un firewall,fent iptables -P INPUT ACCEPT (i també per OUTPUT i FORWARD) però continua igual...

   Alguna idea ??

  Gràcies per endavant,

blas

---

### Post by papapep on 2009-12-02
> Alguna idea ??


El primer que has de verificar és que la ip que tens configurada a Dyndns coincideixi amb la teva real externa actual.

[Aquí]("http://www.whatismyip.com/") pots veure la que tens, i a Dyndns has de mirar la que el servei es pensa que tens. Si no lliguen, ja ho tens.
Et caldrà instal·lar-te un paquet com [ddclient]("http://packages.ubuntu.com/karmic/ddclient"), que actualitza la ip en cas de canvi. Suposo que l'actualització es deu haver ventilat el que tenies funcionant abans.

---

### Post by blas.lopez on 2009-12-03
> **papapep said:**
> El primer que has de verificar és que la ip que tens configurada a Dyndns coincideixi amb la teva real externa actual.

[Aquí]("http://www.whatismyip.com/") pots veure la que tens, i a Dyndns has de mirar la que el servei es pensa que tens. Si no lliguen, ja ho tens.
Et caldrà instal·lar-te un paquet com [ddclient]("http://packages.ubuntu.com/karmic/ddclient"), que actualitza la ip en cas de canvi. Suposo que l'actualització es deu haver ventilat el que tenies funcionant abans.

El dyndns funciona correctament (el router te aquesta funcionalitat i no necessita cap client) i, de fet, tinc obert un port per administració remota del router (accedeix al servidor web del router) i funciona correctament i, com ja he dit, el mateix router deixa al log aquestes peticions.

blas

---

### Post by papapep on 2009-12-03
Doncs prova revisant les regles del NAT del router, per verificar si redirigeix bé els paquets dirigits al port 80, suposant que sigui http i no hagis canviat el port, al teu servidor, i esborra temporalment les regles de l'iptables amb un:

```
sudo iptables -F
```

---

### Post by orestesmas on 2009-12-03
Fes tot això que t'han dit, però tingues en compte que aquests dies hi ha algunes operadores (entre elles ya.com) que estan tenint molts problemes de connectivitat a causa d'una avaria que hi va haver fa uns dies a Madrid, i que encara porta cua.

Podria ser que no fos això, però podria ser que si, en espacial si t'ha deixat de funcionar sense haver fet cap actualització ni modificació a la configuració del sistema.

---

### Post by blas.lopez on 2009-12-04
OK. ja està. 

Sembla que te a veure amb un bug que no em carregava un mòdul (ip_conntrack).

FYI: [https://bugs.launchpad.net/ubuntu/+source/cutter/+bug/240147](https://bugs.launchpad.net/ubuntu/+source/cutter/+bug/240147)

Gràcies,

blas

---

