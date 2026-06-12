---
title: "pasarela a internet"
date: 2007-04-23
forum: Catalan Team
---

### Post by Hugolp on 2007-04-23
Hola

Tinc un ordinador amb dues targes ethernet i vull que faci de pasarela (em sembla que es la paraula que susa) entre dos xarxes.

eth1 està conectada al router que te accés a internet (xarxa externa) amb una ip estatica i eth0 ha de fer de servidor dhcp i a més donar accés a internet a aquesta xarxa interna.

eth1 te acces a internet. He aconseguit que eth0 faci de servidor dhcp per la xarxa interna, pero no aconsegueixo que doni acces a internet. Es a dir conectar eth0 amb eth1, ip forwarding es diu segons he llegit a internet. He probat amb firestarter pero em diu que no pot enxegar el firewall si li dic que doni acces a internet a la xarxa interna. Tb he probat guarddog peró tampoc a funcionat.

eth1 
ip 192.168.1.251
subxarxa 255.255.255.0
gateway 192.168.1.1

eth0
ip 192.168.80.1
subxarxa 255.255.254.0
gateway 192.168.80.1

Estic bastant segur que la ip i la gateway estant bé. La subxarxa no la domino gaire, peró si poso la mateixa a les dues conexions no em puc conectar a internet, amb lo que suposo que no han de ser la mateixa.

Algú em pot ajudar?

Gracies

Hugo

---

### Post by Hugolp on 2007-04-23
Mhe estat informant i la mascara de subxarxa només indica el rang total dadreces que pot tenir una subxarxa, amb lo cual no veig perque hauria de donar problemes que hi hagúes el mateix per eth0 o eth1, pero si poso el mateix no va. Algú sap perque?

Gracies

Hugo

---

### Post by ilku on 2007-04-24
Em sembla que a la eth0 li hauries de posar
 ip 192.168.80.1
subxarxa 255.255.254.0
gateway 192.168.1.251 (es l'altre xarxa) pero no n'estic gaire segur avui tinc un mal dia

---

### Post by CarlesOriol on 2007-04-25
eth1
ip 192.168.1.251
subxarxa 255.255.255.0
gateway 192.168.1.1

eth0
ip 192.168.80.1
subxarxa 255.255.25**5**.0  - El 0 del darrer digit binari (255 = 11111111 254 = 11111110) et fa col·lisionar xarxes
gateway - buit, en aquesta xarxa si no troba una ip no ha d'anar enlloc.

Comprova també que: 

l'arxiu /etc/sysctl.conf  tingui la línia net.ipv4.conf.default.forwarding=1 sense # davant.
(això canvia els valors al reiniciar si vols fer-ho sols a la sessió actual has de fer: echo 1 > /proc/sys/net/ipv4/ip_forward  (com a root naturalment).

Després segueix amb el firestarter no has de tenir cap altre problema.

---

### Post by CarlesOriol on 2007-04-25
Compte la resposta de l'ilku està malament.

---

### Post by ilku on 2007-04-25
Gracies Carles per corregir-me estava una mica espes. Tens raó

---

