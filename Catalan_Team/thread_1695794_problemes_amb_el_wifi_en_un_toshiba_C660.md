---
title: "problemes amb el wifi en un toshiba C660"
date: 2011-02-26
forum: Catalan Team
---

### Post by ibea on 2011-02-26
Hola. M'acabo de comprar un toshiba C660-10H i la sorpresa inicial fou que després d'instal·lar-hi ubuntu en una partició no em reconeixia l'antena del wifi. Després de googlejar una mica vaig trobar uns drivers Realtek [aquí]("http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE") que em van permetre mig sortir del pas. 
El problema és que l'ordinador es connecta al wifi i al cap de poca estona es desconnecta tot sol i m'he de tornar a connectar clicant damunt de la xarxa un altre cop, cosa que amb el Windows i el mateix ordinador no passa. Sabeu alguna possible solució?

Merci

---

### Post by wgarcia on 2011-02-27
Saps quina targeta de wifi tens instal·lada a l'ordinador? Has provat 

Sistema -> Administració -> Controladors addicionals 

si et troba algun controlador per a la teva targeta de wifi?

---

### Post by ibea on 2011-02-27
Em troba la targeta Realtek RTL819x Wifi cards, controlador activat i en ús. Ja és el que vaig instal·lar.

---

### Post by wgarcia on 2011-02-27
Mira si tens al Gestor de paquets Synaptic

linux-backports-modules-wireless-maverick-generic

i en cas afirmatiu pot provar d'instal·lar-lo a veure si han actualitzat els controladors de la teva targeta wifi i funciona millor. 

En cas que no vegis aquest paquet prova d'activar el dipòsit "backports" de de fons de programari del mateix Synaptic.

Alguns recomanen desinstal·lar-se el paquet "network-manager" i instal·lar el paquet "wicd", però en el meu cas i en molts ordinadors diferents sempre m'ha funcionat el network-manager i si no ha funcionat ho he pogut arreglar actualitzant controladors.

---

### Post by kimet on 2011-02-27
Jo m'asseguraria primer de que el controlador que has instal.lat sigui exactament el que correspon a la placa, despres mirar els moduls que tens carregats ```
lsmod | grep rt
``` I veure si no n'esta carregant un d'equivocat, si fos així pots posar-lo a blacklist per que no el carregui al inici.




Salut

---

### Post by ibea on 2011-02-27
Gràcies per les respostes. He provat d'instal·lar els paquets linux-blackports i també el wicd, però no m'ha funcionat la cosa per aquesta via. El wicd em diu que no aconsegueix que em donin una IP.
Respecte al controlador, podria ser que no fos exactament el que correspon a la placa. Si executo l'ordre que em comentes, Kimet, em surt això:

cristina@cristina-Satellite-C660:~$ lsmod | grep rt
parport_pc             30086  0 
parport                37032  3 parport_pc,ppdev,lp

---

### Post by kimet on 2011-02-27
El rpimer que hauries de fer es identificar exactament la teva tarja.
amb:
```
lspci | grep Network
```
o simplement 
```
lspci
```

Despres instal.lar els drivers i possiblement posar algún mòdul a blacklist (al menys així ho he fet alguna vegada) editant /etc/modprobe.d/blacklist.conf 

Mirat aquests posts (en anglès)si hi trobes mes informació:

[http://ubuntuforums.org/showthread.php?t=1691359](http://ubuntuforums.org/showthread.php?t=1691359)
[http://ubuntuforums.org/showthread.php?t=1689148](http://ubuntuforums.org/showthread.php?t=1689148)

Si tot i això s'et continua desconectant, wicd te una opció que reconecta automaticament, (no se si network manager també...)

Salut.

---

### Post by ibea on 2011-03-04
Hola nois.
Després d'haver estat una colla de dies intentant les mil i una per solucionar el tema exposat la cosa continua mínimament igual. Pel tema de connectors crec que tinc instal·lat el correcte.
De moment el que veig és que amb les connexions WPA no hi tinc cap mena de problema per accedir-hi, però amb les WEP, el wicd em diu que no pot obtenir l'adreça IP.

Sabeu per què pot ser?
Merci!

---

### Post by wgarcia on 2011-03-05
Quan no està connectat, prova d'entrar aquesta instrucció en una terminal: 

sudo dhclient

i enganxa els resultats a veure si es pot esbrinar alguna cosa sobre l'IP que està assignant el router al teu ordinador.

---

### Post by ibea on 2011-03-05
El resultat del dhclient és aquest:



Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/wlan0/88:25:2c:6c:15:9c
Sending on   LPF/wlan0/88:25:2c:6c:15:9c
Listening on LPF/eth0/88:ae:1d:f9:4d:09
Sending on   LPF/eth0/88:ae:1d:f9:4d:09
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by wgarcia on 2011-03-06
Es veu que és un problema del servidor DHCP que és el que li assigna l'adreça IP al teu ordinador. Una primera opció és assignar-li una adreça estàtica, cosa que pots fer si tens informació sobre les adreces que assigna el teu router (normalment del tipus 192.168.*.*) i un servidor de noms DNS, editar la connexió a la interfície gràfica de xarxa i entrar la informació "manualment" a "Paràmetres ipv4". 

Per investigar més i veure si es pot arreglar l'assignació automàtica d'IP (DHCP) pot ser útil mirar exactament si el controlador de la targeta s'està usant correctament amb:

sudo lshw -C network

---

### Post by ibea on 2011-03-06
Passa això:

 *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 05
       serial: 88:ae:1d:f9:4d:09
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:43 ioport:4000(size=256) memory:d0404000-d0404fff memory:d0400000-d0403fff
  *-network DISABLED
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 01
       serial: 88:25:2c:6c:15:9c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192CE driverversion=0005.1116.2010 firmware=56 latency=0 link=no multicast=yes wireless=802.11bg
       resources: irq:17 ioport:2000(size=256) memory:d1500000-d1503fff

---

### Post by wgarcia on 2011-03-07
La comanda "lshw" mostra "*network DISABLED", és a dir "xarxa no habilitada" per la part de l'antena wifi. Tens habilitada la "xarxa sense fil" al teu escriptori?

---

### Post by ibea on 2011-03-07
En el moment d'executar la comanda "lshw" tenia la xarxa deshabilitada. Si ho faig en estat de connexió el resultat és el mateix exceptuant el "*-network DISABLED".

---

### Post by wgarcia on 2011-03-07
Sembla que hi ha un dipòsit PPA per la targeta wifi que tens. Primer hauries de desinstal·lar el controlador que tens instal·lat (suposo que es pot fer primer deshabilitant el controlador a Sistema ->  Administració -> Controladors addicionals i després buscant Realtek a Gestor de paquets sinàptic i escollint desinstal·lar). 

Un cop desinstal·lat el controlador, des d'una terminal s'han de donar les instruccions següents:

sudo add-apt-repository ppa:lexical/hwe-wireless
sudo apt-get update
sudo apt-get install rtl8192ce-dkms

Finalment has de reiniciar el sistema i a veure si ara el wifi va bé.

---

### Post by ibea on 2011-03-08
Finalment!!!
He instal·lat els controladors des dels repositoris i de moment la connexió es manté estable.

Moltes gràcies wgarcia, kimet i la resta que sempre ajudeu. Ubuntu no seria possible sense tots vosaltres.

---

### Post by wgarcia on 2011-03-09
Si realment s'ha solucionat (creuem els dits) recorda't de posar-li "Solved" al fil perquè quedi referència.

---

### Post by ibea on 2011-03-12
perdó per tardar tant, però no sé com es fa...  :?

---

### Post by wgarcia on 2011-03-12
Un cop que obres el fil, a la primera línia veuràs una opció que posa "Thread tools". Si cliques s'obre un desplegable una de les opcions del qual diu "Solved" en algun lloc. La cliques i ja està. 

Aquesta opció sols la veu l'usuari que ha creat el fil.

---

### Post by ibea on 2012-03-30
Fa un temps vaig escriure en aquest forum comentant un problema amb ubuntu i el wifi. Despres d'uns quants posts em va semblar que el tema s'arreglava, pero realment no va ser aixi. El wifi se'm connecta sense cap problema, pero al cap de mig minut, tot i que marca que esta connectat, he perdut la connexio.
He decidit reobrir aquest post perque he descobert que amb un LiveCD de Linux Mint aixo no em passa. la connexio es mante tota l'estona. esperancat (ce trencada), l'he instal.lat, pero no ha funcionat.

Sabeu perque pot passar?

P.S. perdoneu pels accents, pero escric des del liveCD i no els trobo...

---

### Post by wgarcia on 2012-03-31
Primer de tot, convindria que desmarquessis el fil com a "solved" per no despistar si alguna persona el veu.

Segon, el que et pugui funcionar amb una distribució i no amb una altra, depèn del nucli que estigui utilitzant cada distribució. A Linux els controladors ("drivers") venen amb el nucli, a vegades es poden baixar mòduls addicionals (per exemple quan són privatius o de codi tancat) que no estan integrats al nucli. 

Per tant una primera cosa que provaria abans de no trencar-se més el cap és mirar si amb l'última versió d'Ubuntu (el Live CD de la 12.04 beta 2) et funciona. Si no funciona es pot seguir buscant la solució, una que pot funcionar en cas desesperat que no hagi controladors específics per a Linux és usar el controlador per a MS Windows (que sí que proveeixen els fabricants en tots els casos) amb el programa "ndiswrapper".

---

### Post by ibea on 2012-04-04
A grans mals...

cansat de les desconnexions m'he decidit per una solució dràstica:
[http://www.youtube.com/watch?v=z19kc5fERsE](http://www.youtube.com/watch?v=z19kc5fERsE)
encara tenia l'ordinador en garantia, però la cosa feia massa temps que durava. He aprofitat una targeta Atheros que tenia d'un HP que va petar de la placa base. 
De moment sembla que l'antena "nova" funciona.

Moltes gràcies pels consells.

---

