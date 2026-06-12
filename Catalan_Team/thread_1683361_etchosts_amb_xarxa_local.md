---
title: "/etc/hosts amb xarxa local"
date: 2011-02-07
forum: Catalan Team
---

### Post by amont on 2011-02-07
Hola,

Ho he intentat al forum general anglès però no he obtingut resposta. Veiem si aquí hi ha més sort.

Sobre una xarxa local connectada a un router tinc, entre d'altres coses, un PC (de nom "fura2" i un portàtil de nom "fura1". El PC té una interface de cable (eth0); i el portàtil en té dues: una per cable (eth0) i una de wifi (eth1). El meu dubte és sobre com he de configurar l'arxiu /etc/hosts del PC. Ara mateix el tinc així:

127.0.0.1	localhost
127.0.1.1	fura2

192.168.1.10    fura1 fura1.workgroup # portàtil cable
192.168.1.11    fura1 fura1.workgroup # portàtil wifi
192.168.1.102   PDA PDA.workgroup
192.168.1.103   MT MT.workgroup

He donat una IP diferent a cada interface del portàtil, però em trobo amb la contradicció de dues adreces IP que apunten al mateix nom de host "fura1" lo qual em sembla que no és lògic, perquè si, per exemple, faig un ping a "fura1", no sabrà a quina IP l'ha de enviar. (En el cas del /etc/hosts del portàtil no hi tinc cap problema, perquè tots els aparells que veu tenen una sola interface i una sola IP).

Agraït per endavant a qui em pugui orientar sobre la manera correcte de configurar aquest arxiu.
Toni

---

### Post by wgarcia on 2011-02-07
No sé si has vist aquesta entrada:

[https://groups.google.com/group/comp.unix.questions/browse_thread/thread/323528cfbc899190/45667f0a1ae31120%2345667f0a1ae31120?hide_quotes=no&hl=en&pli=1](https://groups.google.com/group/comp.unix.questions/browse_thread/thread/323528cfbc899190/45667f0a1ae31120%2345667f0a1ae31120?hide_quotes=no&hl=en&pli=1)

i si et servirà...

---

### Post by kimet on 2011-02-07
workgroup no es fa servir a unix.
Ha de posar:

IP                   fqdn                  alies

Amb les tabulacions.
Per saber l'fqdn:  hostname --fqdn
L'alies es opcional, si vols els pot configurar /etc/networks


Salut.

pd entre ip, fqdn i alies hi d'haver una tabulació,(no em deixa posar-la l'editor del forum)

---

### Post by amont on 2011-02-08
WGarcia,
M'he mirat l'enllaç però no n'he tret l'entrellat. El que es planteja és el meu mateix problema, però les respostes no veig que donin la solució. 

Kimet,
Sobre la *fully qualified domain name *(FQDN), d'acord, però no resolt el meu problema de un nom de host amb dos adreces.

Gràcies de totes maneres pels vostres suggeriments.
Toni

---

### Post by wgarcia on 2011-02-09
El que diu l'enllaç és que si vols posar dos IP amb el mateix nom els has de posar un a continuació de l'altre, però tens raó que no queda clar si soluciona el teu problema.

---

### Post by kimet on 2011-02-09
> ...però no resolt el meu problema de un nom de host amb dos adreces.
 Una interfaç virtual? eth0:0?
Busca per 'ifconfig dummy'

---

### Post by amont on 2011-02-10
> **wgarcia said:**
> El que diu l'enllaç és que si vols posar dos IP amb el mateix nom els has de posar un a continuació de l'altre, però tens raó que no queda clar si soluciona el teu problema.

Efectivament, això he fet: posar dos IP, una a continuació de l'altre, amb el mateix nom de host. Ho deixaré treballant així a veure si dona algun conflicte.

L'avantatge és que, al ser una interface de cable i l'altre de wifi, mai treballen les dues a l'hora.
Grácies

---

### Post by amont on 2011-02-10
> **kimet said:**
> Una interfaç virtual? eth0:0?
Busca per 'ifconfig dummy'

No, no és una qüestió de interfaces virtuals; les dues son reals. Marco el fil com a resolt en base al que dic més amunt.

---

