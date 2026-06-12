---
title: "Portatil, xarxa i avahi"
date: 2007-08-22
forum: Catalan Team
---

### Post by guillemsola on 2007-08-22
Al portàtil i he possat una 7.04. És un asus a6jc, la wifi  una ipw3945. La detecta bé i es conecta sense problemes a les xarxes però en arrancar diu:

> la vostra xarxa actual te un domini local que no es recomenat i es incompatible amb la descoberta de serveis de la xarxa avahi. S'ha inhabilitat el servei,

De fet no puc accedir a recursos d'altres màquines.

gràcies

---

### Post by muleta on 2007-08-23
És el mateix que em surt a mi, no sé què vol dir però abans no m'ho déia. Jo penso que dec haver fet alguna modificació que no tocava.

Per si et serveix de res, el meu portàtil és un HP Pavilion connectat al router Speed Touch de Thomson per Ethernet i el meu proveïdor d'Internet él Orange.

---

### Post by lluisanunez on 2007-08-23
Avahi és un programa de linux que gestiona la cerca de DNS. Si us funciona la connexió a internet, jo no em preocuparia. Aparentment el missatge fa referència a la xarxa local. Si teniu problemes per connectar, potser us ajudaria revisar la configuració de Host, DNS, DHCP, etc. a Sistema >> Administració >> Xarxa

Però, ja sabeu, si funciona, no ho toquis...

---

### Post by muleta on 2007-08-23
Funciona però potser podria funcionar més bé. Per exemple, per obtenir més velocitat en les descàrregues...

Però no m'ho miraré pas :lol:

---

### Post by lluisanunez on 2007-08-23
No, no crec que el DNS tingui res a veure amb les descàrregues d'Emule. De quin color veus la icona de la mula al panel? Si està groga, és que no has pogut obrir els ports correctes. Si està marron, és que tot va bé.

---

### Post by muleta on 2007-08-23
Està verda!!!!. Parlem d'[COLOR="Red"]_A_[/COLOR]mule, eh?.

Tinc verda, de sempre, la d'eD2k. Entenc que això vol dir que tinc l'ID alta.

En canvi, no hi ha manera de posar en funcionament la de KAD. Sempre està apagat o firewallat i es veu que això és normal perque ho he consultat a alguns forums i ningú em sap respondre res.

No tinc cap Firewall i, si el tingués ocult i per defecte, també em caparia els altres ports.

---

### Post by papapep on 2007-08-23
Prova a veure amb aquesta ordre

```
netstat -n |grep 4662
```

si et surt alguna cosa semblant a això:

```

tcp        0      0 192.168.1.34:4662       84.77.7.191:3938        ESTABLISHED
tcp        0      0 192.168.1.34:4662       83.55.63.151:10011      TIME_WAIT  
tcp        0      0 192.168.1.34:4662       217.224.114.249:2993    ESTABLISHED
tcp        0      0 192.168.1.34:4662       200.128.60.11:6783      ESTABLISHED
tcp        0      0 192.168.1.34:4662       83.3.17.210:3381        ESTABLISHED
tcp        0   3820 192.168.1.34:4662       201.141.213.68:4862     ESTABLISHED
tcp        0      0 192.168.1.34:4662       79.4.37.106:3412        TIME_WAIT  
tcp        0      0 192.168.1.34:4662       87.30.36.4:2071         ESTABLISHED
tcp        0      0 192.168.1.34:4662       84.221.150.104:1293     ESTABLISHED
tcp        0   2600 192.168.1.34:54224      85.58.10.224:4662       ESTABLISHED
tcp        0      0 192.168.1.34:4662       77.203.10.226:1136      TIME_WAIT  

```

---

### Post by muleta on 2007-08-23
Que jo no tinc obert el 4662 eh?

Ho faig amb el meu?

---

### Post by papapep on 2007-08-23
> Que jo no tinc obert el 4662 eh?

Ostres, no entenc si estàs preguntant o afirmant...

> Ho faig amb el meu?

El què, executar la ordre??

---

### Post by lluisanunez on 2007-08-23
Insisteixo, ha de ser marron (com el teu avatar)
una manera fàcil és clicar a la icona amb el botó contrari, i triar "client information", et dirà quins ports oberts i quin estat  tens

---

### Post by muleta on 2007-08-23
Vull dir que el meu port UTP obert en el router no és el 4662.

Preegunto si he d'executar l'rdre canviant 4662 pel nº del port TCP que tinc obert o si, l'he de copiar exactament.

---

### Post by papapep on 2007-08-23
Lluïsa, és ben bé que mai es deixa d'aprendre...10 punts per tu :-D

---

### Post by papapep on 2007-08-23
És que el port més important que has de tenir obert és el 4662 TCP, si no vaig errat. La nostra gurú d'Amule Lluïsa (aka MulHacker), igual controla més... :-P

---

### Post by lluisanunez on 2007-08-23
Et juro per TUX que no havia engegat l'emule en mesos :-P . I sí, això diu a la configuració, el port 4662.

---

### Post by muleta on 2007-08-23
Sí que ho diu a la configuració "oficial" però els que venim de windows i de l'emule hem hagut d'aprendre a burlar els "invasors" que utilitzen habitualment els ports "oficials" per hackejar, apropiar-se de dades i omplir-nos el pc de virus, spyware i altres porqueries. 

A més, aleshores n'obrim d'altres menys freqüentats al router i ens entren els fitxers més nets i rápids.

Jo, com que tenia oberts aquells altres, hi vaig continoar, els vaig canviar a la configuració i m'han anat funcionant força bé. D'entrada, vaig provar la configuració per defecte i no m'anava res, tot i que no recordo haver tancat el 4662.

Quan faig això que m'indiques, Lluïsa, em surt la configuració que tinc feta i sí, m'hi figuren els ports que jo tenia oberts, diferents del 4662.

Però em dec haver tornat daltònica... Jo veig les fletxetes verdes.

---

### Post by muleta on 2007-08-23
MERDA...

Perdona, Lluïsa, ara me'n adono: Tu parlaves de la icona de la mula i jo em refería al color de les fletxetes que indiquen la pujada i baixada, així com la ID alta o baixa.

Em sap greu. [-o<

---

### Post by lluisanunez on 2007-08-23
A linux els invasors dolents ho tenen moooolt més difícil, pots estar tranqui&#320;la

---

### Post by papapep on 2007-08-23
A no ser que hagis entrat al sistema com a root :-D 

(és per recordar-te que NO s'ha d'entrar en mode gràfic, ni en consola, com a root sinó fer servir "sudo" (en entorn gràfic "gksudo")) ;-)

---

### Post by pserra on 2007-08-23
Estava 'curiosejant' aquests missatges i precissament al posar la comanda de PAPAPEP em surt molt més llarg:
ere@Ubuntu:~$ netstat -n |grep 4662
tcp        0      0 192.168.0.128:52821     84.78.130.220:4662      TIME_WAIT  
tcp        0      0 192.168.0.128:52654     85.48.156.127:4662      ESTABLISHED
tcp        0      0 192.168.0.128:37348     81.34.70.75:4662        TIME_WAIT  
tcp        0      0 192.168.0.128:34631     83.36.21.136:4662       ESTABLISHED
tcp        0      0 192.168.0.128:47257     84.76.133.206:4662      ESTABLISHED
tcp        0      1 192.168.0.128:47814     185.233.155.85:4662     SYN_SENT   
tcp        0      0 192.168.0.128:38375     84.78.100.2:4662        ESTABLISHED
tcp        0      0 192.168.0.128:55530     88.1.79.236:4662        TIME_WAIT  
tcp        0      0 192.168.0.128:57969     83.42.44.190:4662       TIME_WAIT  
tcp        0      1 192.168.0.128:55896     75.247.165.83:4662      SYN_SENT   
tcp        0      0 192.168.0.128:52533     88.23.117.20:4662       TIME_WAIT  
tcp        0   2600 192.168.0.128:35148     83.33.125.46:4662       ESTABLISHED
tcp        0      0 192.168.0.128:46582     83.45.72.136:4662       ESTABLISHED
tcp        0      0 192.168.0.128:51512     85.56.22.63:4662        TIME_WAIT  
tcp        0      0 192.168.0.128:35476     84.122.209.153:4662     ESTABLISHED
tcp        0      1 192.168.0.128:56878     76.234.87.85:4662       SYN_SENT   
tcp        0      0 192.168.0.128:42074     195.251.213.60:4662     ESTABLISHED
tcp        0      0 192.168.0.128:60588     88.11.139.186:4662      ESTABLISHED
tcp        0      0 192.168.0.128:51181     88.20.50.214:4662       TIME_WAIT  
tcp        0      1 192.168.0.128:44781     196.148.155.85:4662     SYN_SENT   
tcp        0      0 192.168.0.128:39622     85.59.201.124:4662      ESTABLISHED
tcp        0      0 192.168.0.128:52339     89.6.218.164:4662       TIME_WAIT  
tcp        0      0 192.168.0.128:59392     88.22.73.67:4662        TIME_WAIT  
tcp        0      0 192.168.0.128:47134     213.60.100.52:4662      TIME_WAIT  
tcp        1    100 192.168.0.128:38680     81.44.194.236:4662      LAST_ACK   
tcp        0      0 192.168.0.128:52288     89.129.151.72:4662      TIME_WAIT  
tcp        0      0 192.168.0.128:47849     83.54.102.24:4662       ESTABLISHED
tcp        0      0 192.168.0.128:54904     83.43.2.239:4662        TIME_WAIT  
tcp        0      1 192.168.0.128:53973     68.21.184.81:4662       SYN_SENT   
tcp        0      0 192.168.0.128:46093     83.32.8.32:14662        ESTABLISHED
tcp        0      0 192.168.0.128:48705     83.43.148.140:4662      ESTABLISHED
tcp        0      0 192.168.0.128:44515     83.40.111.231:4662      TIME_WAIT  
tcp        0      0 192.168.0.128:60659     81.39.13.140:4662       ESTABLISHED
tcp        0     46 192.168.0.128:37818     77.225.18.10:4662       ESTABLISHED
tcp        0      0 192.168.0.128:34799     82.158.146.161:4662     TIME_WAIT  
tcp        0      0 192.168.0.128:59923     88.18.175.92:4662       ESTABLISHED
tcp        0      0 192.168.0.128:48084     83.44.53.138:4662       ESTABLISHED
tcp        0      1 192.168.0.128:36601     201.51.39.83:4662       SYN_SENT   
tcp        0      0 192.168.0.128:35561     81.172.67.35:4662       TIME_WAIT  
tcp        0      1 192.168.0.128:38934     152.48.31.80:4662       SYN_SENT   
tcp        0      0 192.168.0.128:57879     85.53.156.207:4662      ESTABLISHED
tcp        0  11008 192.168.0.128:47076     84.125.146.60:4662      ESTABLISHED
tcp        0      0 192.168.0.128:55111     190.30.131.238:4662     ESTABLISHED
tcp        0      0 192.168.0.128:40645     81.172.113.167:4662     TIME_WAIT  
tcp        0      0 192.168.0.128:33136     87.235.194.109:4662     ESTABLISHED
tcp        0      0 192.168.0.128:45146     87.216.163.206:4662     ESTABLISHED
tcp        0      1 192.168.0.128:46651     126.165.33.80:4662      SYN_SENT   
tcp        0      0 192.168.0.128:55558     84.78.41.62:4662        ESTABLISHED
tcp        0      0 192.168.0.128:58239     62.174.112.157:4662     TIME_WAIT  
tcp        0      1 192.168.0.128:44597     62.57.217.238:4662      SYN_SENT   
tcp        0      0 192.168.0.128:39110     84.121.25.216:4662      TIME_WAIT  
tcp        0      0 192.168.0.128:40085     81.184.84.144:4662      ESTABLISHED
tcp        0      0 192.168.0.128:36084     81.202.139.108:4662     TIME_WAIT  
pere@Ubuntu:~$ 

PERÒ AIXÒ QUE SURT PER CONSOLA... QUE ES?? no tinc tantes descàrregues....ni de bon tros...
Disculpeu perquè potser és una pregunta 'tonta' però he quedat intrigat....
A reveure.

---

### Post by pespin on 2007-08-23
Quan tinguis dubtes sobre una ordre de consola normalment pots informar-te amb la ordre "man" seguit de la ordre que vulguis veure. per exemple utilitzant "man netstat" surt això (i moltes coses més)

> 
netstat  - Print network connections, routing tables, interface statis&#8208;
       tics, masquerade connections, and multicast memberships

Per tancar el manual que surt a la consola dona-li a SHIFT+q

I ara algú farà la traducció al cristià i ho explicarà :lolflag:

---

### Post by papapep on 2007-08-23
Doncs tot això que et surt pel terminal Pere (i no és que en tinguis més ni menys que jo, que tot pot ser, sinó que jo no ho he posat tot el que sortia perquè no calia, que només era un exemple :-D) són les connexions que tens per la placa de xarxa.

Que, evidentment, no tot són gent que estigui descarregant, ni descàrregues que facis tu. Pensa que hi ha molta gent en cua esperant que algú dels que estan descarregant del teu ordinador acabi per a poder fer-ho ells. Doncs la manera que tenen de control·lar-ho tot plegat és amb "converses" entre el teu i el seu Amule.

 I com ho fan? Doncs evidentment per xarxa, i això, entre d'altres coses, és el que veus amb l'ordre **netstat.**

---

### Post by pserra on 2007-08-24
[SIZE="4"]Merci PAPAPEP per l'aclaració....ja saben una coseta més.. 
a reveure[/SIZE]

---

