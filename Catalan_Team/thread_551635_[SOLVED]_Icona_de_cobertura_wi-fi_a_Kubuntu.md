---
title: "[SOLVED] Icona de cobertura wi-fi a Kubuntu"
date: 2007-09-15
forum: Catalan Team
---

### Post by cadebou on 2007-09-15
Hola a tothom,

Sistema: KUbuntu Feisty.

Usava el KNetworkManager en "roaming mode" per poder canviar de xarxa wi-fi, però me n'he cansat i li he dit que sempre es connecti a la mateixa xarxa (mitjançant la configuració manual).

El problema és que, ara, la icona ja no és el "mesurador de la intensitat de senyal" sinó una espècie d'endoll i no puc saber com vaig de cobertura wi-fi. Hi ha manera de tornar-lo a habilitar?

Gràcies, Pau.

---

### Post by orestesmas on 2007-09-16
Doncs a mi no em sona, però pots mirar la cobertura wifi amb una altra aplicació. Fins i tot des de la consola, si n'obres una i tecleges "iwconfig" et sortirà quelcom així:

```
ath0      IEEE 802.11g  ESSID:"Mas-Pastor"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0F:CB:AB:20:E8
          Bit Rate:48 Mb/s   Tx-Power:16 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=41/94  Signal level=-49 dBm  Noise level=-90 dBm
          Rx invalid nwid:15  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
El que tu cerques és a "Link Quality" i "Signal level"

Això de la consola pot semblar una mica pesat, però realment no es necessita saber _en cada moment_ quin nivell de senyal tens, sinó només en ocasions puntuals. Obrir una consola llavors tampoc no és tan molest.

Penso que també hi ha utilitats per l'escriptori (jo no me les conec, però pots mirar per exemple el Korner Monitor del superkaramba), però bàsicament totes van a cercar la informació al mateix lloc.

---

### Post by cadebou on 2007-09-16
Gràcies Orestes per la resposta.

Sabia que existien altres aplicacions com el kwifimanager o el kinternet (o la mateixa consola) que podrien donar-me aquesta informació, però no sabia si aquest bug del kNetworkManager ja era conegut i potser tenia solució.

Moltes gràcies igualment.

Pau.

---

### Post by patrickfromspain on 2007-09-16
no es un bug del network manager: el NM es un programa bastant limitat. Quan has fet servir configuració manual, has deixat de fer servir el network manager per conectarte i en fas servir un altre, que suposo (no conec kubuntu) deuen ser o bé el kinternet, o bé el kwifimanager (el qual te una miniaplicacion per la barra de menu que t'indica la senyal).

salut!

---

