---
title: "Desfer els canvis (actualitzacions), és possible?"
date: 2010-11-17
forum: Catalan Team
---

### Post by pserra on 2010-11-17
Hola,
no sé que m'ha passat, l' ordinador amb ubuntu fa molt temps que em anava de conya, ahir recordo que vaig fer els updates/uprades (no vaig mirar els paquets que s'instal·laven) i vaig continuar  navegant fins que vaig parar l'ordinador.
El cas es que avui no hi ha manera de connectar-me, miro els paràmetres de connexió i estan correctes... en windows em funciona, que m'ha pogut passar? com es pot restaurar?
Gràcies

---

### Post by pserra on 2010-11-17
Estic que no entenc perquè m'ha petat!!
passo més informació:
- tenia el manager que em funcionava de conya el internet(adsl i wifi)
- he mirat de posar al navegador l'adreça del router i no hi té accés...
-estic amb el ubuntu 10.04..

Que puc fer? ara que estava acostumat a treballar amb aplicacions ubuntu...
Merci

---

### Post by kimet on 2010-11-17
Donç es molt poca la informació que dones.
Está aixecat el gestor de xarxes?
Està aixecada la interfície?
Sortida de sudo ifconfig.
Busca per errors:
/var/log/el_manager_que_facis_servir
Per saber els paquets que has instal.lat recientment:
/var/log/apt/term.log o /var/log/aptitude.

---

### Post by pserra on 2010-11-17
> **kimet said:**
> Donç es molt poca la informació que dones.
Está aixecat el gestor de xarxes?
Està aixecada la interfície?
Sortida de sudo ifconfig.
Busca per errors:
/var/log/el_manager_que_facis_servir
Per saber els paquets que has instal.lat recientment:
/var/log/apt/term.log o /var/log/aptitude.

Merci kimet per l'interés...
per el que em passa... estic flipant..no li trobo el motiu...
tinc un netbok en ubuntu que funciona com sempre i l'altre...m'ha petat
la connexió amb el router....
el que no entenc com es que no puc trobar el router... entrant la ruta per el navegador....
en quant ahir la darrera actualització  que vaig fer va ser la de instal·lar un programa de edició de fórmuiles que es diu lyx i és molt 'feixuc'... no he vist cap actulitzacio del networkmanager, que tinc la versió 8

en quan a la sortida de ifconfig  tinc:
> pere@pere-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:8b:98:f0:45  
          inet6 addr: fe80::223:8bff:fe98:f045/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4636 (4.6 KB)  TX bytes:1494 (1.4 KB)
          Interrupt:26 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:313 errors:0 dropped:0 overruns:0 frame:0
          TX packets:313 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:21903 (21.9 KB)  TX bytes:21903 (21.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:2c:1a:02:f1  
          inet6 addr: fe80::224:2cff:fe1a:2f1/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4186 (4.1 KB)  TX bytes:2850 (2.8 KB)

pere@pere-laptop:~$

potser hauria de reinstal·lar el manager... però sense connexió...

Merci

---

### Post by wgarcia on 2010-11-18
Tens algun nucli més antic per provar si amb aquest altre nucli pots tenir accés al router wifi?

---

### Post by pserra on 2010-11-18
doncs en aquests moments no en tinc cap, 
quan s'instal·la un de nou, tinc la 'mala costum' de que si el nou durant unes setmanes va bé, elimino  el vell....
que més puc provar?

---

### Post by pserra on 2010-11-18
Em volia saltar la 10.10 però en vista de que no se que provar, ja l'estic instal·lant... com que tinc l'arrel i la home apartades no em suposarà massa estona..

---

### Post by pserra on 2010-11-18
Ja està, el internet torna a funcionar!!
ara ja em surten altres problemes que elsexposaré en un altre fil

---

