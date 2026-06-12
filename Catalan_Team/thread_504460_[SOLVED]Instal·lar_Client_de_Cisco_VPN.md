---
title: "[SOLVED]Instal·lar Client de Cisco VPN"
date: 2007-07-19
forum: Catalan Team
---

### Post by xoldy on 2007-07-19
Hola a tots, ara estic intentant connectar via vpn a la xarxa de la meva feina. Amb windows, feia servir el client de Cisco.
Allà no tenia cap problema per configurar, sabia exactament on posar les dades.
Per començar tinc una adreça IP a la qual he de connectar. Tinc un usuari de grup i una contrasenya, i un cop connecta em demana les meves credencials personals, usuari i contrasenya.

On hauria de posar aquestes informacions en el kvpnc? és compatible amb cisco oi?

Em podeu donar un cop de mà, perquè he llegit alguna solució a forums per instal·lar el client cisco per linux, però no sembla fàcil instal·lar-lo perquè sembla que he de tocar el tema d kernel. La veritat es que no se massa de que es parla.

Llegeixo poquet encara, però és molt pel temps que li puc dedicar.

Moltes gràcias

---

### Post by papapep on 2007-07-19
Respecte el KVPN ni flowers, no el tinc ni el faig servir.
Si dius que has mirat les indicacions del meu blog i no te'n surts, explica on t'has quedat i ho anirem fent. Veuràs que no és res de l'altre món.

---

### Post by xoldy on 2007-07-19
Hola papapep,
com que soc una mica tossut me n'he sortit amb el kvpnc. Llegint bé els errors que donava al intentar connectar al gateway m'he adonat que no estava posant les dades en el lloc adient.
L'error estava en que repetia la contrasenya de grup IPSec on havia d'anar la contrasenya d'usuari de grup, per la resta, tot molt similar al client de windows.

JA HE POGUT CONNECTAR A LA XARXA DE LA MEVA FEINA!!!!
Estic molt content, perquè era un dels passos que em feia retornar a l'xp, perquè porto ja 15 dies integrament en linux.
Genial

Moltes gràcies per tot, de vegades pensar que tens suport darrera fa que pensis millor les coses.
Per mi podem donar per tancat el fil.

---

### Post by laa on 2008-10-25
Hola xoldy jo també em trobo amb el mateix problema. Des de l'entorn windows em connectava remotament amb l'vpn client de cisco a la meva feina i tot i que m'han passat un programa per connectar-me des de l'ubuntu, no ho aconsegueixo. 
Em pots donar un cop de mà? 
Gràcies

---

### Post by xoldy on 2008-10-27
Hola, laa, ho intentaré, ara faig servir el paquet vpnc que és el que dóna compatibilitat amb vpn de cisco. Jo el vaig instal·lar directament pel synaptic, i ja veuràs que és un moment.
Al principi, l'utilitzava amb l'entorn gràfic amb el kvpnc, però un dia em va deixar de funcionar, i ja no l'he tornat a utilitzar.

Vaig obrir la consola, i vaig cridar el programa amb privilegis de root:
```
sudo vpnc
```

i a partir d'aquí et demana la ip de la vpn, el nom de grup, la contrasenya de grup, i finalment l'usuari i contrasenya personal.

Va perfecte, ja que et fa el tunel directament. A més amb la Hardy, quan engegues el vpnc, et dóna el número de treball per quan acabis, el puguis "matar".

Espero que t'hagi servit, sinó, ja saps, aquí estem!

Salut

---

