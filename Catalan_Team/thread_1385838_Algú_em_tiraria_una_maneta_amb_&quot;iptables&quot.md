---
title: "Algú em tiraria una maneta amb &quot;iptables&quot;?"
date: 2010-01-20
forum: Catalan Team
---

### Post by kukat on 2010-01-20
Uff...porte ja uns dies barallant-me amb "iptables", i no hi ha forma de fer-lo anar amb una política "DROP" per defecte...
He llegit manuals a tort i a dret: pello, "administración sistemas linux anaya", apunts del professor....tot!
És una llàstima, per què es lo últim que em falta en la documentació d'informatització d'una xarxa amb Virtualbox.:(

Algú se li dona bé el tema de "iptables" i podria tirar-me una mà? 

La xarxa és aquesta: [http://img189.imageshack.us/img189/4902/jordicat.png](http://img189.imageshack.us/img189/4902/jordicat.png)
(creada amb Dia)

I el tallafocs, està a l'arxiu ".sh" adjunt

Probablement siga algun petit detall...o no se...
Salutacions!

---

### Post by papapep on 2010-01-20
A les línies 23 a 25 defineixes una política per defecte d'ACCEPT. Si hi fiques DROP, tindràs el que dius que vols. No m'he mirat la resta de l'script, però això juraria que això ho tens just al revés.

---

### Post by kukat on 2010-01-20
ostres...clar. Es que ho vaig canviar per a poder copiar el fitxer mitjançant ssh al meu ordinador!
però clar, el script és amb DROP en lloc d'ACCEPT....

El problema és quan canvie l'ACCEPT per DROP, que no em diexa fer absolutament res, a pesar d'obrir (o això pense) les serveis necessaris:(.

---

### Post by papapep on 2010-01-20
Fes un cop d'ull a [aquest script]("http://cipherdyne.org/LinuxFirewalls/ch01/"), crec que et servirà d'ajut.

---

### Post by kukat on 2010-01-20
Estic mirant-ho i està agradant-me molt! ;) Prou més complet que els que he vist fins ara!

A veure si puc solucionar-ho i et comente alguna cosa!
Gràcies! ;)

---

### Post by akyra on 2010-01-21
Hola kukat,

Has de tenir en compte l'ordre de les instruccions, així crec que potser hauries d'afegir el INPUT con a primera linia de la connexió SSH i després el FORWARD, i així per les demés connexions que facis:

#Obrim el port SSH que gastarà el Client linux
[COLOR="RoyalBlue"]iptables -A INPUT -s 192.168.103.4 -p tcp --dport 8022 -j ACCEPT[/COLOR]

iptables -A FORWARD -d 192.168.103.4 -p tcp --sport 8022 -j ACCEPT

També podries fer una politica que no deixis entrar res que no vulguis però si deixis sortir tot
iptables -P INPUT DROP
iptables -P OUTPUT ACCEPT


Una pregunta si fas un : sudo iptables -L, quin resultat et dóna.

Salutacions

---

### Post by CarlesOriol on 2010-01-24
Per que no gestiones el MASQUERADE en comptes de l'ACCEPT? Si la regla és vàlida masquerade... sinò drop.

Jo uso el iptables-save i iptables-restore per desar les regles.

I en comptes de carregar-ho a l'init.d jo ho tinc posat al /etc/network/intefaces amb la comanda post-up iptables-restore....

Una altra cosa que va de nassos és fer un log amb l'Ip tables i així veus quines comunicacions t'arriben i com 

iptables -A INPUT -j LOG 

Molt important. Un 90% dels problemes de l'iptables son regles escrites en ordre incorrecte. Fins i tot el LOG és una regla, si és processa alguna abans que aquesta no t'arrivarà a "LOGEJAR".

---

### Post by kukat on 2010-01-26
Bé, he modificat i traduït  l'script que m'ha passat papapep, [d'aquesta web]("http://cipherdyne.org/LinuxFirewalls/ch01/")

El resultat és el de l'arxiu adjunt, adaptant-lo [a la meua xarxa]("http://img189.imageshack.us/img189/4902/jordicat.png"). 

Però no puc fer ping al servidor (xartux.jordi.cat) ni, per suposat, a "www.google.cat"...:(

El servidor "xartux" em dona IP per DHCP, i puc fer-li ping a la seua IP (192.168.103.1)
No se si serà alguna cosa del NAT que he fet malament, però veient l'script, em sembla que hi ha que posar la ip del servidor web i el servidor dns, que en aquest cas és xartux(192.168.103.1)...

No se que pot passar, però alguna cosa no comprenc bé em sembla...

Per cert, em tira una errada l'script a l'executar-lo. Sembla que és un bug en la negació...(!)

"Using intrapositioned negations ('--option ! this') is deprecated in favor of extrapositioned ('! --option this').
 
?? em sembla que no passa res, però és estrany....

Ja no se que fer! :(

EDITO: Per cert Carles, em recomanes ficar-ho al arxiu "interfaces" ?? El mestre no ha comentat res, però primer faig cas al LoCo, i després als mestres...;)

---

### Post by kukat on 2010-02-01
"Using intrapositioned negations ('--option ! this') is deprecated in favor of extrapositioned ('! --option this').

Açò ja està solucionat! :D

Únicament hi ha que canviar !XARXA , per **! -i** --> ** !-o**   i  --> **! -s **

Bé, el que possa en el missatge en anglès...
Deprecated: desaprovació....
hehehe

Ara falta veure quu tinc mal per a que no vagen les coses en política de negació.

---

### Post by kukat on 2010-02-03
Açò ja és un escàndol.

Li he dit al mestre de l'institut que quin problema puc tindre en aquest script de iptables, i el senyor professor m'ha contestat: 

"utilitzes coses de nivell superior al
que demane. Crec que val la pena que no et compliques en voler adaptar
un exemple d'Internet al que necessiten a classe."

Però no m'ha dit que puc tindre malament....
Vaja educació que tenim, senyores i senyors...lamentable.

---

### Post by falsospam on 2010-02-03
Amb això i trovaras moltes vegades, el meu profe deia:
"Aixo encara no ho hem donat, per tant no pots utilitzar-ho"
Jo entenia "Desapren", es una llastima els profesors no son Deus y la seva feina es enseñar fins on els hi diuen, deixen o saben. 
T'acompaño en el sentiment, però tu no decaiguis

---

### Post by kukat on 2010-02-03
La veritat és que si....Tindrem que aguantar-nos! :)

Ara ja és un repte, açò del iptables hi ha que solucionar-ho com siga! 

Salut!

---

### Post by ilku on 2010-02-04
La resposta a sigut la de una persona que no en sap i que nomes es regeix per allo que te apuntat als seus apunts. Per tant no pot ajudar-te.

La resposta haguera hagut d'estar, "(...) ja ho se que no ho demanes, però jo ho vull saber i aprendre".

---

### Post by kukat on 2010-02-04
Lo bo del cas és que ens ha donat els típics manuals de PELLO de l'any del cinema en blanc i negre (sense menysprear als manuals PELLO d'iptables), i algun més, i bàsicament ens ha explicat alguna cosa i ens ha dit que ens busquem la vida. 

Algú veu que l'script d'en papapep i els manuals aquestos de Pello hi ha moltes diferències??? 
La veritat és que comencen a ser subrealistes aquestes classes. ;)

---

