---
title: "Connexio wifi"
date: 2012-11-05
forum: Catalan Team
---

### Post by abosch on 2012-11-05
Hola, 

Fa pocs dies que he contractat el servei ADSL i tinc problemes de connexió via wifi. Em detecta el senyal i sembla que es conecti però no em carrega les pàgines. 

Una vegada ha anat bé. He llegit que recomanen engegar i apagar router però tampoc em funciona. També he llegit de provar el ndiswrapper però abans prefereixo preguntar-vos.  

Enganxo lspci,

abosch@abb-ntbk:~$ lspci | grep -i network
02:00.0 Network controller: Intel Corporation WiFi Link 5100


molt agraït

---

### Post by wgarcia on 2012-11-05
Dius que es connecta al enrutador, però aparentment no rep connexió d'Internet. Suposo que et consta que l'enrutador està ben configurat i està ben connectat amb Internet. 

Per veure si l'ordinador està rebent una direcció IP de l'enrutador, pots obrir una ternminal i entrar la següent instrucció:

```
ip addr
```

T'hauria de mostrar la connexió inalàmbrica activa i la direcció IP que li assigna l'enrutador al teu ordinador. Enganxa el resultats que obtens.

---

### Post by abosch on 2012-11-07
A vegades se'm connecta i a vegades no. Mentre tenia connexió he aprofitat per actualitzar el sistema per si això podia tenir-hi alguna cosa a veure. Ara, la darrera vegada que ho he probat, no en tenia. 

Enganxo el que em retorna l'ordre que em comentes:

abosch@abb-ntbk:~$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN qlen 1000
    link/ether 00:26:9e:0b:a0:bc brd ff:ff:ff:ff:ff:ff
3: wlan0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP qlen 1000
    link/ether 00:22:fb:6d:d5:e2 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.33/24 brd 192.168.1.255 scope global wlan0
    inet6 fe80::222:fbff:fe6d:d5e2/64 scope link 
       valid_lft forever preferred_lft forever

---

### Post by wgarcia on 2012-11-07
Les línies importants són 

```
3: wlan0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP qlen 1000
link/ether 00:22:fb:6d:d5:e2 brd ff:ff:ff:ff:ff:ff
inet 192.168.1.33/24 brd 192.168.1.255 scope global wlan0
inet6 fe80::222:fbff:fe6d:d5e2/64 scope link
valid_lft forever preferred_lft forever

```

on es veu (inet 192.168.1.33) que el teu ordinador veu l'enrutador, i que l'enrutador l'asssigna una direcció IP. 

Anem a veure si és un problema de servidor de noms. Prova alguna adreça, per exemple

[http://www.upf.edu](http://www.upf.edu)

Si no es pot connectar prova amb

[http://193.145.56.15](http://193.145.56.15)

Si es connecta amb el número en comptes del nom complet, voldrà dir que el servidor de noms (DNS) no està funcionant i això és el que t'impedeix connectar-te als llocs.

---

### Post by abosch on 2012-11-07
Ho he provat i no em puc connectar ni amb el nom ni amb els numeros.

---

### Post by wgarcia on 2012-11-08
El problema de connexió a Internet, sols li passa a aquest ordinador? Vull dir, tens constància que l'enrutador està ben configurat?

---

### Post by abosch on 2012-11-11
Amb aquest ordinador a vegades em puc connectar i a vegades no. Quan aquest no es connecta ho he probat amb un altre i sí que puc. 

Amb el telefon també em puc connectar al wifi sense problemes.

---

### Post by wgarcia on 2012-11-11
Però vull dir, tens constància que el router està funcionant bé i donant accés a connexió a Internet sense problema?

---

### Post by abosch on 2012-11-13
No sé si t'entenc. Podria ser que quan van venir a intalar-me la línia configuressin malament el router?

He trucat al servei tècnic i m'han fet una prova en remot, m'ha dit ja estic dintre el teu router ¿? i el problema continuava. Quan li he anat explicant i li he dit que vaig amb linux, m'ha dit que ja passaria la reclamació al servei tecnic i que ja em trucarien. 

De moment continuo igual, a vegades funciona a vegades no.

---

### Post by wgarcia on 2012-11-14
Si a vegades hi ha connexió, el més probable és que el problema no sigui del router sinó d'alguna cosa de l'ordinador. 

Abans de continuar remenant, es podria descartar la següent possibilitat. Una possibilitat és que el canal que utilitza l'antena wifi estigui massa ocupat en el teu entorn, i per aquesta raó a vegades es talli la connexió. Tens manual del router per canviar la configuració del canal que utilitza? Si és així es podria provar això. 

Hi ha un programa que es diu wifi-radar, que pots instal·lar des del Centre de Programari, que et mostra les senyals wifi que es veuen al teu entorn i quin canal estan utilitzant, a més d'altra informació. Amb això pots investigar si el teu senyal wifi té molta competència o no.

---

### Post by abosch on 2012-11-15
Tinc la guia d'instalació i el cd que va amb la caixa. Em sembla que el manual no.

He instalat el wifi radar. Em detecta 8 punts d'accés i pel canal que va em meu router en són 3.

Això de canviar el canal és el que hauria de dir al servei tecnic?

---

### Post by wgarcia on 2012-11-15
Sí, prova-ho a veure si dóna resultat. Normalment si tens accés al menú de configuració del router, que s'accedeix des d'un navegador (Firefox o un altre) amb una adreça de la xarxa ([http://192.168.0.50](http://192.168.0.50), [http://192.168.0.51](http://192.168.0.51) o  [http://192.168.1.1](http://192.168.1.1) o semblants), el pots canviar tu mateix. Els menús de configuració solen tenir un usuari i contrasenya però els fabricants posen "admin" sense clau o "admin/admin", de manera que si algú es pot validar a la senyal wifi té accés a l'administració del router i tot.

---

### Post by abosch on 2012-11-19
Ja he accedit al router, la direcció és [http://192.168.1.1:8000](http://192.168.1.1:8000)

He canviat el canal però continuo sense connexió wifi.

---

### Post by wgarcia on 2012-11-20
Doncs sembla que el canal no és el problema, seria important que verifiquessis que no hi ha problemes de configuració per part del router, és a dir que hi ha d'altres ordinadors que es connecten al mateix router sense problemes. 

També seria útil saber si el teu ordinador es pot connectar a altres punts wifi sense problemes, o si sempre presenta aquest problema. Així es pot investigar si és un problema específic amb aquest router, o general del teu ordinador i la configuració de la targeta wifi. 

La targeta wifi que tens en principi té controladors oberts i per tant no necessita controladors propietaris, el controlador ja ve al nucli de Linux. Mirant una mica en Internet he vist que alguna gent tenia problemes amb aquesta targeta amb ordinadors Dell perquè Dell té uns controladors específics, però aquesta gent no podia ni tan sols connectar-se al router, i en el teu cas segons el que es veu en alguns dels diagnòstics que has produït, es connecta bé al router i rep una direcció IP. Una altra cosa que em semble que es pot descartar és que pugui ser un problema de resolució de noms (la traducció del número IP a una adreça d'Internet concreta), perquè usant els números IP tampoc es pot connectar, com em vas comentar. 

Es pot doncs investigar ara sobre els mòduls que s'estan fent servir per la targeta wifi. Pots enganxar el resultat que dóna la següent instrucció  des d'una terminal?:

```
ls /etc/modprobe.d
```

---

### Post by abosch on 2012-11-20
Fa uns dies vaig comprovar la xarxa wifi amb un altre ordinador i m'anava bé, es va connectar sense problemes.

Pel que fa a aquest que utilitzo, en d'altres xarxes wifi em puc connectar bé. Fins ara no m'havia donat problemes.

T'enganxo el retorn de l'ordre que em cometes, 

abosch@abb-ntbk:~$ ls /etc/modprobe.d
alsa-base.conf           blacklist-framebuffer.conf   blacklist-watchdog.conf
blacklist-ath_pci.conf   blacklist-modem.conf         libpisock9.conf
blacklist.conf           blacklist-oss.conf           oss-compat.conf
blacklist-firewire.conf  blacklist-rare-network.conf  vmwgfx-fbdev.conf

---

### Post by wgarcia on 2012-11-21
Pots enganxar també el retorn de:

```
lsmod | grep -i wifi
```

Aquesta ordre "lsmod" mostra tots els mòduls (controladors) que hi ha carregats al nucli de Linux, i "grep -i wifi" selecciona els que diguin "wifi".

---

### Post by abosch on 2012-11-23
Aquest és el retorn a l'ordre que em comentes, 


abosch@abb-ntbk:~$ lsmod | grep -i wifi
iwlwifi               362374  0 
mac80211              436455  1 iwlwifi
cfg80211              178679  2 iwlwifi,mac80211


molt agraït pel teu temps, a veure si en treïem l'entrellat. 


Paral·lel·lament he trucat unes quatre vegades al servei tècnic i la darrera resposta que m'han donat és que això que em passa és normal. Que tal i fa el sistema que utilitzi. Que això és normal a les connexions wifi. Quan no es connecta s'ha de parar l'ordinador i tornar-lo a engegar. Lo bo del cas és que hi ha hagut un parell de vegades que efectivament, aturant la màquina i reiniciant-la, llavors la xarxa wifi m'ha anat bé.

---

### Post by abosch on 2012-11-23
Aquest és el retorn a l'ordre que em comentes, 


abosch@abb-ntbk:~$ lsmod | grep -i wifi
iwlwifi               362374  0 
mac80211              436455  1 iwlwifi
cfg80211              178679  2 iwlwifi,mac80211


molt agraït pel teu temps, a veure si en treïem l'entrellat. 


Paral·lel·lament he trucat unes quatre vegades al servei tècnic i la darrera resposta que m'han donat és que això que em passa és normal. Que tal i fa el sistema que utilitzi. Que això és normal a les connexions wifi. Quan no es connecta s'ha de parar l'ordinador i tornar-lo a engegar. Lo bo del cas és que hi ha hagut un parell de vegades que efectivament, aturant la màquina i reiniciant-la, llavors la xarxa wifi m'ha anat bé.

---

### Post by wgarcia on 2012-11-23
A veure, un altre suggeriment. Es pot mirar si el problema ve de què s'està usant "wifi N" i no és estable. No és una solució del tot afortunada perquè aquesta modalitat de wifi és més moderna, però potser navegant amb les modalitat "a, b i g" de wifi no presenta el mateix problema. 

Per tant prova les següents comandes:
```

sudo rmmod iwlagn
sudo modprobe iwlagn 11n_disable=1
```

i prova una estona a veure si no cau la connexió. Si és així es pot fer el canvi permanent per no haver d'entrar aquestes comandes cada cop.

---

