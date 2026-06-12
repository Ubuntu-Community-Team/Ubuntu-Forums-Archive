---
title: "Problemes WIFI WPA2 amb jaunty"
date: 2009-09-10
forum: Catalan Team
---

### Post by akyra on 2009-09-10
Hola a tothom,
Ahir vaig comprar el nou ordinador amb, wifi n,i vaig particionar i instalar ubuntu 9.04 64 bits (el mateix que tenia en l'ordinador vell), i m'ha succeit una cosa que no acabo d'entendre.

Abans de tot aclarir que vaig estar tot el matí connectat a la feina amb wifi en una xarxa oberta sense cap problema.

A l'arribar a casa, a on tinc un router Belkin Visio N1 (wifi n) amb seguretat WPA2-personal, veig en el network-manager que em demana la clau i es connecta a la xarxa wifi, però realment no funciona.
Si faig un ping a la porta d'enllaç, em surt "Destination host unreachable".

El cas és que amb l'ordinador vell que tenia, wifi g, em connectava diariament sense problemes aparents i amb l'encriptació WPA2.

Vaig fer una prova treient la seguretat del router i es va connectar a la primera, i provant amb el modem amb encriptació web també ha funcionat.

He googlejat una mica i sembla que hi ha problemes amb l'encriptació WPA2 i ubuntu, però la veritat no veig una raó (alguns diuen que es culpa del anell de claus), ja que amb jaunty i l'ordinador vell m'havia funcionat.

Pot ser que faci falta instal·lar alguna cosa apart?
Alguna idea

Moltes gracies.

---

### Post by sianeu on 2009-09-10
Problemes amb la tarjeta de red del nou ordinador o combinacions de hardware que provoquen incompatibilitats estranyes. Jo m'hi vaig trobar canviant la placa base d'un vell ordinador de sobretaula connectat amb wifi i seguretat wpa1 (psk/tkip). Tot i mantenir la mateixa tarja de red usb, ara només em connecta si no amago el ssid, cosa que abans sí podia fer. Prove-ho si tens la xarxa oculta.

Salut

---

### Post by akyra on 2009-09-10
Perdona, però que vol dir la xarxa oculta?

Jo la veig amb el network manager i m'hi connecto, i de fet em diu "conectado", però no puc ni fer un ping.
En canvi si deshabilito la seguretat WPA2 i la deixo lliura, es connecta a la primera, o en el cas del modem que es WEP també es connecta sense cap problema.

Gracies.

---

### Post by sianeu on 2009-09-10
El networkmanager identifica les xarxes wifi que troba amb un nom (SSID) i molts routers tenen la opció d'amagar-lo (llavors per connectar-t'hi a més de la contrasenya has de saber el nom de la xarxa). Però si no ho sabies vol dir que no ho tens configurat així.

Deu ser una imcompatibilitat de la teva tarja de red wifi amb el networkmanager i wpa2. Prova amb el wicd (está en els repositoris de Jaunty). Moltes vegades soluciona el problema.

Salut

---

### Post by akyra on 2009-09-10
Hola de nou,

Bé amb el meu router s'ha connectat una vegada i he pogut fer un ping però no em deixava connectar a internet, he reiniciat i ja no es connectava.

Després he provat a fer la connexió amb protecció WEP i després sense connexió, i no  hi hagut manera.

Ara mateix estic connectat de forma inhalambrica amb el meu modem wifi amb encriptació WEP de 128 bits i funciona de conya.
Entenc que si fos el network manager tampoc funcionaria.

Probaré el wicd, a veure que pasa, però vaig una mica perdut.

Salutacions

---

### Post by akyra on 2009-09-12
Hola a tothom, Primer de tot amb el WICD no he notat cap millora, així que he tornat al network-manager.

Sembla que finalment he aconseguit connectar-me, pero sembla que tinc algun problema amb el router

Bé el que em succeix ara, és que quan engego ubuntu em surt que estic connectat a la xarxa inhalambrica de casa, (em connecto de forma manual amb ip estatica), però quan faig un ping al router que és la porta d'enllaç, triga bastant a contestar i ho fa com host unreacheable i al cap d'uns 25s apareix la contesta del ping com si no hagues pasat res.
> jordi@jordi-ubuntu:~$ ping 192.168.2.1
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
From 192.168.2.3 icmp_seq=45 Destination Host Unreachable
From 192.168.2.3 icmp_seq=46 Destination Host Unreachable
From 192.168.2.3 icmp_seq=47 Destination Host Unreachable
64 bytes from 192.168.2.1: icmp_seq=1 ttl=64 time=48093 ms
64 bytes from 192.168.2.1: icmp_seq=2 ttl=64 time=47085 ms
64 bytes from 192.168.2.1: icmp_seq=3 ttl=64 time=46077 ms
64 bytes from 192.168.2.1: icmp_seq=4 ttl=64 time=45069 ms
64 bytes from 192.168.2.1: icmp_seq=5 ttl=64 time=44061 ms
64 bytes from 192.168.2.1: icmp_seq=6 ttl=64 time=43053 ms
64 bytes from 192.168.2.1: icmp_seq=7 ttl=64 time=42045 ms
64 bytes from 192.168.2.1: icmp_seq=8 ttl=64 time=41037 ms
64 bytes from 192.168.2.1: icmp_seq=9 ttl=64 time=40029 ms


D'altre banda la conexió a internet quan porto una estona no funciona, la xarxa inhalambrica segueix connectada però internet no funciona, de fet ara mateix m'ha pasat i portava 3 minuts conectat.
La conexió cablejada funciona bé.

Si algú té alguna idea, li estaria molt agrait

---

### Post by akyra on 2009-09-15
Bé ja estic connectat a la meva wifi, no sé ben be que he fet però ara funciona. He tornat a instalar l'ubuntu fent una instal·lació neta.

He posat la IP estática i es connecta i he pogut descarregar fitxers a 750KB/s però encara tinc el problema del ping inicial.

Obro un altre fil preguntant temes the interficies de xarxa

Salutacions

---

