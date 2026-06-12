---
title: "[SOLVED] Problemes amb el wifi, gràfica i so - Acer Travelmate 5520"
date: 2007-10-23
forum: Catalan Team
---

### Post by fonde on 2007-10-23
HOLA

sóc nou en tot aixó de l'ubuntu i tinc problemes amb la xarxa
tinc la versio 7.10 d l'ubuntu en una partició,en l'altra hi tinc el windows vista

tinc un adaptador de xarxa Broadcom(versio de driver 4.102.15.61) i un Marvell Yukon 88E8071 PCI-E Gigabit controller(versio de driver 10.22.1.3)

despres de dies d'intentar-ho tot el maxim que he aconseguit ha estat que el dispositiu de wifi detecti les xarxes pero no s'hi aconsegueix connectar mai.
vaig instalar un paquet(bm43xx) i aqui va millorar la cosa peró com us he dit la cosa va quedar curta

em sabrieu dir què he de fer per solucionar-ho?

gràcies :guitar:

---

### Post by Kosimo on 2007-10-23
Entenc que has fet servir l'opció de controladors restringits de l'ubuntu i has actualitzat el firmware.

Dius que pots veure les xarxes i no connectar-te
A la que vols connectar-te tens cap mena de protecció wep per casualitat?  Com fas per connectar-te?  Escrius el password? Tens en compte si és hexadecimal?

---

### Post by fonde on 2007-10-24
si, vaig fer servir els controladors restringits i ara tinc el bm43xx activat.
no em puc connectar ni en xarxes sense contrasenya ni amb una xarxa amb clau wep d 128bit

---

### Post by CarlesOriol on 2007-10-24
Hi ha cap raó especial per posar aquest titol?

---

### Post by Kosimo on 2007-10-24
Escrius la clau WEP, 

has escollit la opció HEX ?

Veuras que quan escrius la clau, et permet escollir diverses opcions, escull HEX.

---

### Post by fonde on 2007-10-24
ei kosimo

ho he intentat, he posat la clau WEP amb hex i ha fet el mateix...continua detectant les xarxes però no hi ha manera que l'ubuntu es connecti a la xarxa :'(

---

### Post by CarlesOriol on 2007-10-24
Ara el titol està molt millor. :-)

Si has insta&#320;lat el controladors **bcm43xx** comprova fent un **dmesg** que no t'avisa que falti el firmware. En qualsevol cas crec que el controlador lliure amb el firmware privatiu té problemes per funcionar a més d'11 Mb (**comprova que el punt d'accés estigui en mode mixte b/g**)

Si ho estas installant per **ndiswrapper**, afegeix a /etc/modules/blacklist **bcm43xx**. Tot i que per començar a configurar-ho pots aturar el controlador lliure amb **modprobe -r bcm43xx**

Fes les probes amb:

**sudo iwconfig eth1 essid latevaxarxa mode managed key 1234ABCD  (password en hexadecimal o s:Password)**

Passats uns segons has de veure amb sudo iwconfig que l'access point està enllaçat. Això vol dir que la primera part funciona correctament.

Un cop fet això pots posar la ip a ma amb 

**sudo ifconfig eth1 123.123.123.123**

o demanar-la per dhcp 

**sudo dhcpclient eth1**

(T'ho indico en mode consola per que és més fàcil que ens indiquis els missatges que veuras i en mode gràfic perds tot el control del que està passant)

Espero que escriguis i seguim si cal...

---

### Post by fonde on 2008-04-06
hola,
sóc bàsicament nou en tot això de l'ubuntu.
Farà uns quants mesos vaig escriure a aquest fórum per si em podieu solucionar un problema amb la targeta de xarxa.No ens vem acabar d'entendre i total,ho vaig deixar estar lu de l'ubuntu.

però fa unes setmanes m'hi vaig tornar a posar,i com que al final me n'he ensortit he decidit fer això: una guia per aquells novells que com jo es fiquen en l'ubuntu amb un Acer TravelMate 5520.

abans de la "mini-guia" vull donar les gràcies als que veu intentar donar-me un cop de mà fa uns mesos(kosimo i CarlesOriol)i espero que us sigui d'utilitat!

FNd
p.d: actueu segons l'ordre establert a continuació.
p.d2:tingueu paciència,no naixem ni molt menys ensenyats!el principi no és fàcil,ja us hi anireu acostumant!

1r: instalat la distribució i386 d'ubuntu


2n: instal·lació de la targeta gràfica:

des d'un altre pc baixat el paquet Fwcutter: [http://packages.ubuntu.com/gutsy/i386/bcm43xx-fwcutter/download](http://packages.ubuntu.com/gutsy/i386/bcm43xx-fwcutter/download)
baixa't el wl_apsta.o:
[http://mural.uv.es/alacer/wl_apsta.o](http://mural.uv.es/alacer/wl_apsta.o)

instal·la el fwcutter,després de reiniciar vas a SYSTEM>ADMINISTRACIÓ>GESTOR DE CONTROLADORS RESTRINGITS i actives el bcm43xx...etc.
reinicia un altre cop

SOBRETOT:no remenis la pestanya del wifi,acostumat com estaves a que fes pampellugues amb el windows ho trobaràs a faltar,creu-me!


3r:actualitzar els repositoris
com que ja tenim internet,ara toca actualitzar.
ves a SYSTEM>ADMINISTRACIÓ>SOFTWARE SOURCES
apareix una finestra,doncs bé: de la primera pestanya selecciona-ho tot i deselecciona l'apartat del cd d'instal·lació d'ubuntu.de la segona pestanya i de la següent ho selecciones tot,de les seguënts pestanyes no has de tocar res.
et sortirà que s'actualitzaran i baixaran els paquets

4t: instal·lació de la targeta gràfica(ATI RADEON XPRESS 1250)
ves a SYSTEM>ADMINISTRACIÓ>GESTOR DE PAQUETS SYNAPTIC i cerca: xorg-driver-fglrx
selecciona,instal·la i reinicia
en reiniciar,vas a SYSTEM>ADMINISTRACIÓ>GESTOR DE CONTROLADORS RESTRINGITS i actives ATI RADEON...ETC.
reinicia un altre cop(crec)

5e: fes cas del pc!si et diu que hi ha actualitzacions de software per instalar,fes-ho!

6e: targeta de so
obre el terminal: APPLICATIONS>ACCESSORIS>TERMINAL
escriu
sudo apt-get install linux-backports-modules-generic 
posa la contrasenya
seguidament escriu:
sudo gedit /etc/modprobe.d/alsa-base
s'obrirà un arxiu amb un text amb xino pels que no som informàtics i al final de tot,crees una línia nova i hi poses això:
options snd-hda-intel model=acer

reinicia i tindràs ho tindràs configurat

---

### Post by papapep on 2008-04-06
Fonde, t'he mogut el post al fil original, a fi de que tot plegat tingui continuitat.
Gràcies per exposar la teva solució després de tant de temps ;-)

---

### Post by CarlesOriol on 2008-04-06
Per cert fonde... passa a presentar-te pel fil de benvinguda.

[http://ubuntuforums.org/showthread.php?t=562776](http://ubuntuforums.org/showthread.php?t=562776)

I com ja saps aquest mes fem una festa a caldes de Montbui on us esperem a tots [http://ubuntuforums.org/showthread.php?t=712412](http://ubuntuforums.org/showthread.php?t=712412)

---

