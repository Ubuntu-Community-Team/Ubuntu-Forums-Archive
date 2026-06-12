---
title: "Problemes amb el nm-applet"
date: 2011-01-02
forum: Catalan Team
---

### Post by tanreb20 on 2011-01-02
Bones!

Des de fa uns dies que el network manager es tanca sol tallant-me la conexió del wifi i per tant sense internet.. lo que é smooolt engorros.

Alguna idea de com puc aportar més informació i com puc començar a arreglar-ho?

```
alorma@Hogwarts:~$ nm-applet &
[1] 13760
alorma@Hogwarts:~$ ** Message: applet now removed from the notification area
** Message: applet now embedded in the notification area
** (nm-applet:13760): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:13760): DEBUG: foo_client_state_changed_cb
** (nm-applet:13760): DEBUG: foo_client_state_changed_cb
** Message: Caught signal 15, shutting down...
nm-applet &
```

AIxo es el que ha sortir després d'executarlo al terinaal fins a que s'ha tancat.

---

### Post by wgarcia on 2011-01-02
Jo diria que l'nm-applet ha de ser cridat per "network-manager", i per tant s'hauria d'iniciar amb

sudo service network-manager start   ( o restart si ja està corrent). 

Ara bé, si es tanca la connexió wifi, el problema pot ser un altre, i estar relacionat amb el mòdul de la targeta wifi i no tant amb el network-manager.

---

### Post by tanreb20 on 2011-01-02
Básicament la cosa és que desapareix del indicador, sense poder conectr-se ni activar res.

Simplement desapareix.

---

### Post by wgarcia on 2011-01-03
Fas servir kubuntu? Segons la teva signatura no, però si d'un cas...

---

### Post by tanreb20 on 2011-01-04
No pas, ubuntu 10.10

---

### Post by tanreb20 on 2011-01-05
Hola de nou.

Reobro el fil perque no hi ha manera de solucionar-ho!

Quan porta una estona engegat, i la conexio a internet del ruter cau, el network manager sembla que es solidaritzi amb ell i s'apagui del tot, lo qual.. esun engorro enorme!

ALguna ajuda?

---

### Post by kimet on 2011-01-05
Pots provar wicd...

---

### Post by tanreb20 on 2011-01-05
Mai m'ha funcionat massa bé pero ho tornaré a provar...

---

### Post by wgarcia on 2011-01-05
Potser hi hagi alguna configuració del network-manager que l'estigui fent tancar quant cau la connexió amb el router. No sé si ho solucionarà, però pots provar de reinstal·lar el network-manager intentant esborrar al màxim les configuracions prèvies. Des d'una terminal:

sudo apt-get remove --purge network-manager
sudo apt-get install network-manager

---

### Post by pezbaloo on 2011-01-07
Hola tanreb20:
Els meus problemes de conexió wifi, amb xubuntu 10.04 i un adaptador wifi per usb, es van solucionar amb el paquet ndiswrapper que pot adaptar els drivers de windows XP. També vaig haber de canviar el network manager per wicd, ja que nm em complicaba la existència amb les claus de conexió. Ara em funciona tot correctament.
salut!

---

