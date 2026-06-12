---
title: "internet no funciona"
date: 2015-11-17
forum: Catalan Team
---

### Post by josep-maria on 2015-11-17
Bon dia,

Tinc l'ubuntu 15.04. Després d'un temps sense fer servir el PC, he volgut entrar a internet, però no he pogut.
He fet clic a la icona de dalt de tot, la de l'acés a internet que té forma de ventall. 
He fet clic a: edita les connexions > cable > connexio de xarxa amb fil > edita.
Surt una finestra que diu dues adreces MAC, però estan en blanc.

Què cal fer-hi?

---

### Post by wgarcia on 2015-11-18
Entenc doncs que tens connectat el PC per cable a una xarxa que saps que té connectivitat amb Internet. La següent ordre a una terminal

```
ifconfig
```

et donarà informació sobre les connexions de xarxa de l'ordinador. 

Pots enganxar el resultat aquí (si no tens connexió per fer copia i enganxa potser pots fer un foto amb el mòbil i enganxar-la).

---

### Post by josep-maria on 2015-11-19
diu això:

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:836 errors:0 dropped:0 overruns:0 frame:0
          TX packets:836 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:94225 (94.2 KB)  TX bytes:94225 (94.2 KB)

---

### Post by wgarcia on 2015-11-22
Segur que arriba senyal de xarxa? Normalment el connector del cable de xarxa té una llumeta que s'ha d'encendre si hi ha senyal de xarxa.

---

### Post by josep-maria on 2015-11-24
Sí que hi ha un led verd molt petit al costat del connector, i sí que està encès.

Tinc uns altres pc, i si els dic ifconfig, em diuen això:

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:22:64:14:f9:aa  
          inet addr:192.168.0.201  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::222:64ff:fe14:f9aa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29862 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24584 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:30651867 (30.6 MB)  TX bytes:3454528 (3.4 MB)
          Interrupt:19 Memory:f0180000-f01a0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1864 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1864 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:194191 (194.1 KB)  TX bytes:194191 (194.1 KB)

Al pc que no funciona no hi surt tot el primer paragraf (el del títol eth0). Només surt el que té el títol de "lo".

---

### Post by wgarcia on 2015-11-24
Per això preguntava allò del cable de xarxa, sembla com si el PC no estigués veient la targeta de xarxa. Saps de segur que la connexió de xarxa funciona? Per exemple, perquè funciona amb algun altre sistema operatiu.

---

### Post by josep-maria on 2015-11-28
Sí que funciona l'accés a internet, perquè l'he provada amb un altre pc, que també és un ubuntu. També he posat el pc espatllat a un altre lloc on hi ha una connexió a internet, i el pc no funciona. Cal dir que tot el pc funciona bé menys l'accés a internet. Per tant, o l'ubuntu s'ha desmanegat o el pc s'ha espatllat. Com ho podem saber?

---

### Post by wgarcia on 2015-11-29
A una terminal

```
lspci | grep Ethernet
```

et mostrarà si el sistema veu la targeta de xarxa.

---

### Post by josep-maria on 2015-11-30
Contesta això:

00:19.0 Ethernet controller: Intel Corporation 82566DM Gigabit Network Connection (rev 02)

---

### Post by wgarcia on 2015-11-30
Bé, sembla que sí que veu la targeta de xarxa. Ara el que pots fer és desendollar el cable de xarxa i tornar-lo a endollar, i mirar les últimes línies del que et diu l'ordre:
```
dmesg
```
Això mostra el registre del sistema que es va actualitzant en temps real. Aixó es podrà veure si es produeix algun error en endollar el cable de xarxa.

---

### Post by Biscarri on 2015-11-30
hola wgarcia,

tinc el mateix problema que en josep-maria, amb un PC ubuntu 14.04 connectat via ethernet a un repetidor Wi-Fi AirPort express d'apple
l'ordre...   lspci | grep Ethernet     ...no em dóna cap output
l'ordre...   ifconfig     ...em dóna el mateix output que a en Josep-Maria (no apareix cap linia [COLOR=#417394][FONT=Ubuntu Mono][COLOR=#000000]eth0 Link...[/COLOR][/FONT][/COLOR])[COLOR=#417394][FONT=Ubuntu Mono]

[/FONT][/COLOR]moltes gràcies per l'ajuda
Lluís

---

### Post by wgarcia on 2015-12-01
Benvingut Lluís, crec que seria millor si obres un fil específic per al teu problema, a vegades els problemes semblen semblants però tenen les seves coses específiques, i és millor tractar-lo en un tema separat així queden registrades les característiques del teu sistema.

---

### Post by josep-maria on 2015-12-01
Si faig el dmesg, les darreres línies de la resposta són:

[   21.661679] audit; type=1400 audit (1448987522.857:11) apparmor="STATUS" operation="profile_load" profile="unconfined" name="usr/bin/evince-previewer "pid=433 comm="apparmor_parser"

Sempre surten les mateixes línies, tant és que tingui el conector d'internet ficat o tret.

---

### Post by Biscarri on 2015-12-01
finalment he pogut resoldre el meu problema amb les ordres següentes...

[COLOR=#000000][COLOR=#000000]echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee /etc/resolv.conf[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]sudo /etc/init.d/networking restart[/COLOR][/COLOR]

i després rebotant el sistema

moltes gràcies per respondre, wgarcia!!

---

### Post by wgarcia on 2015-12-02
LLus_Biscarri, és estrany, perquè /etc/resolv.conf en principi és sobreescrit pel sistema, o fins i tot em sembla que no es fa servir actualment, no sé quina versió d'Ubuntu tens. En tot cas si s'ha arreglat millor no remenar-lo de moment.

---

### Post by wgarcia on 2015-12-02
josep-maria, pel que es veu al registre del sistema (amb "dmesg") sembla que no funciona el connector de xarxa. Quan endolles i desendolles el cable s'hauria de generar un missatge de sistema i no es genera cap.

---

### Post by Biscarri on 2015-12-02
OK wgarcia, moltes gràcies per l'ajut.
Lluís

---

### Post by josep-maria on 2015-12-07
He esborrat tot el sistema operatiu i hi he ficat l'ubuntu 14.04. Segueix sense funcionar. Com que hem comprovat que internet arriba bé al pc, sembla clar que està malament la placa d'interface amb internet.

Moltes gràcies.

---

