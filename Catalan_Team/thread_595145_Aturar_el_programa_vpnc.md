---
title: "Aturar el programa vpnc"
date: 2007-10-28
forum: Catalan Team
---

### Post by xoldy on 2007-10-28
Bona nit, com puc aturar el programa vpnc que he iniciat des d'un terminal?

em funciona el programa sense problemes. Connecto a la vpn, i quan ja voldria tancar la sessió, com que no se acabar el programa, digue'm cutre acabo reiniciant.

Moltes gràcies

---

### Post by papapep on 2007-10-28
Cutre (ho has demanat tu :-P)

Doncs si l'obres a un terminal, si el tanques es tanca el programa. No li veig més complicació.
Si, pel que sigui, això no funciona (que NO hauria de passar), fes:

```
ps -e|grep vpn
```

i després amb el codi numèric que et dóni el procés del VPNC:

```
kill codi_numèric
```

si, tot i així, es fa el dur:

```
kill -9 codi_numèric
```

---

### Post by xoldy on 2007-10-28
Moltes gràcies papapep, he provat i sembla que em mata el procés amb la primera comanda ```
sudo kill codi_numeric
```, però quan comprovo que torno a tenir accés a internet, no el tinc. El vpnc fa que tingui el tunel de connexió i fa que no pugui navegar quan estic connetat amb la vpn de la meva feina.
total que he de reinciar igualment. Em penso que ho deixo. de vegades vull filar massa prim.

salutacions

---

### Post by papapep on 2007-10-28
No, no files massa prim.
Quan mates el vpnc ha "d'alliberar" la xarxa. 

Quin script crides? I com?

Potser l'script que fas servir té alguna cosa malament...

---

### Post by xoldy on 2007-10-29
de fet només faig un```
sudo vpnc
```
em demana la ip del gateway, l'usuari de grup, la contrasenya de grup, i el meu usuari i contrasenya personal.
Es connecta i ja puc accedir normalment a les màquines de la meva feina.

Quan ja no em fa falta, faig la crida que m'has suggerit amb el ```
kill num_de_procés
```
i sembla que no el talla, perquè obro el firefox i no connecta amb les pàgines d'inici.

ja et donaré el missatge exacte que em dona quan connecto per si serveix de pista quan sigui a casa.

Merci pel teu temps.

---

