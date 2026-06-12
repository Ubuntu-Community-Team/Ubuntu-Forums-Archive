---
title: "roda del ratolí"
date: 2012-05-14
forum: Catalan Team
---

### Post by rosa d'abril on 2012-05-14
Hola,
He instal·lat l'Ubuntu 12.04 en una màquina virtual creada en W7. Tot ha rutllat sense problemes però ara em trobo que els botons esquerre i dret funcionen perfectament però  la roda del ratolí no roda, vull dir, no fa l'*scroll*. 
A algú li ha passat i sap com arranjar-ho?
Gràcies

---

### Post by wgarcia on 2012-05-16
Com sempre és necessari tenir més informació sobre el maquinari que fas servir per intentar veure què pot estar passant. 

Per exemple, si és un ratolí "USB", des d'una terminal es pot donar l'ordre:

```
lsusb | grep -i mouse
```

i el sistema t'escopirà quin model és.

---

### Post by rosa d'abril on 2012-05-16
Doncs imagino que ni tan sols me'l detecta perquè li he escrit al terminal la instrucció que m'indicaves (exactament com me la escrivies) i no em dóna cap informació.
Per altra banda, el ratolí, roda inclosa, em funciona perfectament en el W7, que és l'host de la màquina virtual.
Salut i gràcies

---

### Post by wgarcia on 2012-05-16
Però confirmes que és un ratolí connectat per un port USB?

---

### Post by rosa d'abril on 2012-05-16
De veritat que t'ho confirmaria si, ehem, entengués la pregunta. Vols dir si és un ratolí USB? La resposta és que sí.
Salut!

---

### Post by wgarcia on 2012-05-16
Sí, la pregunta era si el conectes a través d'una conexió USB, pots enganxar tot el que surt quan entres al terminal:

```
lsusb
```

Una altra manera que hi ha de donar informació del que està passant és desendollar el ratoli, tornar-ho a endollar, obrir una terminal i entrar:

```
dmesg
```

i enganxar aquí les últimes 10 línies de la parrafada llarguíssima que surt després d'entrar aquesta comanda.

---

### Post by rosa d'abril on 2012-05-17
Uf, gràcies per la paciència.
A la primera de les opcions la resposta és:
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 80ee:0021 VirtualBox USB Tablet

Pel que fa a la segona, vet'ho aquí:
[  146.119455] type=1400 audit(1337249235.758:30): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1410 comm="apparmor_parser"
[  146.193945] type=1400 audit(1337249235.834:31): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince" pid=1411 comm="apparmor_parser"
[  146.201143] type=1400 audit(1337249235.842:32): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince//launchpad_integration" pid=1411 comm="apparmor_parser"
[  146.202842] type=1400 audit(1337249235.842:33): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince//sanitized_helper" pid=1411 comm="apparmor_parser"
[  146.205161] type=1400 audit(1337249235.846:34): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince-previewer" pid=1411 comm="apparmor_parser"
[  146.209122] type=1400 audit(1337249235.850:35): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince-previewer//launchpad_integration" pid=1411 comm="apparmor_parser"
[  146.210113] type=1400 audit(1337249235.850:36): apparmor="STATUS" operation="profile_replace" name="/usr/bin/evince-previewer//sanitized_helper" pid=1411 comm="apparmor_parser"
[  148.088514] init: plymouth-stop pre-start process (1511) terminated with status 1
[  532.675859] hrtimer: interrupt took 6280529 ns

---

### Post by wgarcia on 2012-05-17
Bé, no es pot llegir massa més informació del que has enganxat. De totes maneres si l'Ubuntu està corrent dins d'una màquina virtual dins de Windows 7, el que pot estar passant és que els ports USB no estiguin ben configurats a la màquina virtual i per això no e funcioni bé ratolí. 

No et puc donar massa ajut sobre això, perquè no sé com funciona el Virtualbox dins de Windows 7. Sé una mica més sobre com funciona dins Ubuntu.

---

### Post by rosa d'abril on 2012-05-17
Moltes gràcies per la pista. De fet, també vaig instal·lar la VB en un altre ordinador que corre en W7 i l'Ubuntu tampoc no acaba d'anar-m'hi del tot fi. Pot ser que la VB estigui més pensada per a Linux que per a Windows?
Gràcies per tot

---

### Post by wgarcia on 2012-05-17
No sé, almenys per a Ubuntu hi ha dues versions de Virtualbox, una que és codi obert (versió OSE) i l'altre que és codi tancat. Les dues són gratuïtes però la segona versió té més funcionalitats, per exemple l'accés als ports USB sols funciona a la versió de codi tancat. 

De totes maneres si fas un ús continuat d'Ubuntu potser et convingui fer una instal·lació en una partició del disc dur, tot i que reconec que si fas servir habitualment programes d'un altre sistema operatiu és una mica empipant haver de tancar un sistema i obrir un altre per canviar de programa. En aquest sentit és millor fer servir la màquina virtual. En aquest cas òbviament la meva preferència seria que l'amfitrió de la màquina virtual fos Linux...

---

### Post by rosa d'abril on 2012-05-17
Ah, no sabia que hi hagués dues versions de la VB. Jo me l'he descarregada d'aquí:
[https://www.virtualbox.org/](https://www.virtualbox.org/)
On puc trobar la de codi tancat?
Gràcies una altra vegada

---

### Post by wgarcia on 2012-05-18
Em sembla que la que et descarregues directament de la seva pàgina web és la de codi tancat, però no estic segur. La que et descarregues dels depòsits Ubuntu és l'"OSE".

---

### Post by rosa d'abril on 2012-05-18
He trobat una manera de fer anar la roda: desactivar la integració del punter i fer que me'l capturi automàticament cada vegada que entro a la finestra de l'Ubuntu instal·lat en la màquina virtual. Inconvenient? Doncs que he d'anar prement la tecla *ctrl dreta* cada vegada que vull tornar a passar al sistema amfitrió (W7). És una mica pesat però pitjor era que la roda no fes l'scroll.
Salut!

---

### Post by wgarcia on 2012-05-18
I allò de les "Guest additions" o com es digui de Virtualbox no t'ho soluciona? Això és una cosa addicional que es pot instal·lar, almenys a Linux, que et permet tenir la pantalla virtual a pantalla completa, intercanviar el portapapers entre sistemes operatius i integrar el ratolí.

---

### Post by rosa d'abril on 2012-05-18
Sí que les tinc. Precisament és el que he desactivat perquè, per defecte , les GA m'integraven el punter i aquest em circulava perfectament d'un SO a l'altre, però el preu a pagar era que la roda no feia l'scroll.

---

### Post by rosa d'abril on 2012-05-18
Ostres, ostres, rectifico. 
Em pensava que tenia instal·lades les Guest Additions perquè me les vaig baixar juntament amb la Virtual Box i, diria, les vaig executar. 
Però, ara, com que m'hi has fet pensar, he potinejant  per la pestanya Dispositius, he vist que el menú oferia un Instal·la les Guest Additions, hi he clicat i, ara sí, me les ha instal·lades. Resultat? El punter es mou per tot arreu amb plena llibertat i, oh miracle, la roda del ratolí fa l'scroll.
Gràcies mil

---

