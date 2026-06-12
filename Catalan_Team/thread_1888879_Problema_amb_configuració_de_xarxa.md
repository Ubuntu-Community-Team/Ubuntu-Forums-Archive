---
title: "Problema amb configuració de xarxa"
date: 2011-11-30
forum: Catalan Team
---

### Post by jaumell on 2011-11-30
Bon dia,

M'he adonat que l'ordinador es connecta a Internet a través del wifi, enlloc de pel cable de xarxa. 

Tinc un Dell Studio 15, amb Ubuntu 10.04 actualitzat.

Descarto un problema de cablejat i de router ADSL, donat que si poso el cable a un netbook amb Windows7 es connecta a l'instant i sense problema.

Mirant Sistema>Preferències>Connexions de xarxa, em posa que la connexió eth0 va ser utilitzada per darrer cop fa un any.

En els paràmetres de la connexió s'indica Mètode Automàtic (DHCP).

Si faig ifconfig, m'apareixen eth0, wlan0 i lo, però eth0 no té cap IP assignada.

Alguna idea de quin pot ser el problema?

Salutacions,

Jaume

---

### Post by wgarcia on 2011-12-02
Has tocat alguna cosa dels arxius de configuració de la xarxa? Jo m'he trobat que en alguns casos que editant el fitxer /etc/NetworkManager/NetworkManager.conf i canviant 

```
managed=false
```

a

```
managed=true
```

m'ha solucionat problemes semblants al teu, es pot provar, però en principi si el NetworkManager gestiona les connexions hauria d'estar posat a "false". Si s'ha tocat algun arxiu tipus "/etc/network/interfaces" llavors sí que pot ser necessari posar-lo a "true".

---

### Post by jaumell on 2011-12-02
Alguna cosa he provat... però ho he tornat a deixar tot igual, crec...

No he trobat l'arxiu que comentes, però si /etc/NetworkManager/nm-system-settings.conf amb el següent contingut:


```
# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file:
#
# /etc/default/NetworkManager
#

[main]
plugins=ifupdown,keyfile

no-auto-default=00:22:19:e2:97:00,

[ifupdown]
managed=false
```

He provat a posar managed=true, però llavors ja no funciona cap mena de xarxa.

Un comentari més. L'arxiu /etc/network/interfaces indica el següent:

> # The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
# iface eth0 inet dhcp

Vaig provar a canviar-ho:

> # The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

Però tampoc funcionava.

Gràcies per l'ajut,

---

### Post by wgarcia on 2011-12-03
Prova de comentar "auto eth0", és a dir deixar-lo com

 ```
# auto eth0
```

---

### Post by jaumell on 2011-12-04
Doncs ara ho tinc així:
```
# The primary network interface
# auto eth0
# iface eth0 inet dhcp
```

I pel que sembla no ha canviat res. La connexió es segueix realitzant per wifi.

A més, he tornat a provar a posar-ho com a managed=true i ara mateix està funcionant així, però només pel wifi.

Pel que sembla, no hi ha manera que la tarja agafi una adreça IPv4, però en canvi si que en té una IPv6.

He intentat donar-li una adreça IPv4 fixa amb el Network Manager, però tampoc hi ha manera.

---

### Post by wgarcia on 2011-12-05
Per veure què està veient la connexió de xarxa, posa que faci per dhcp automàticament, inhabilitat momentàniament les connexions inalàmbriques, i des d'una terminal entra

```
dhclient
```

Això t'hauria de mostrar què és el que veu quan li demanes que es connecti.

---

### Post by jaumell on 2011-12-05
Al Network Manager tinc eth0 configurat amb accés Automàtic (DHCP) i, després de desactivar el wifi i fer un ```
sudo dhclient
``` això és el que veig:

```
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/pan0/92:7b:f1:72:00:00
Sending on   LPF/pan0/92:7b:f1:72:00:00
Listening on LPF/wlan0/00:22:fb:24:00:00
Sending on   LPF/wlan0/00:22:fb:24:00:00
Listening on LPF/eth0/00:22:19:e2:00:00
Sending on   LPF/eth0/00:22:19:e2:00:00
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```
(he editat les adreces mac)

Entenc que troba la tarja, però no li assigna IP.

---

### Post by kimet on 2011-12-05
**iface eth0 inet dhcp** Això ha d'estar descomentat per que et doni la direcció per dhcp.

Mira amb **[B]sudo ifconfig**[/B] si eth0 està aixecada. 
I fas:```
sudo ifconfig eth0 up
``` si no ho estava.
Sempre que facis algún canvi a /etc/network/interfaces has de abaixar i trona apujar la interfaç per que facin efecte els canvis.

Salut.

---

### Post by jaumell on 2011-12-13
Actualització del tema:

Després de provar alguna de les idees que heu aportat, pel que sembla sense resultat, he fet vàries proves més.

Vaig desintal·lar completament el network-manager i vaig substituir-lo pel Wicd, amb el mateix funcionament del sistema, reconeixia la tarja però no li assignava una adreça ip4.

Vaig desinstal·lar Wicd completament i vaig instal·lar de nou el network-manager (després d'haver esborrat la carpeta etc/NetworkManager/), però tot seguia igual.

La gràcia està en que vaig agafar el portàtil, el vaig portar a la feina, vaig deshabilitar-li el wifi i el vaig endollar a la xarxa i voilà, en menys de tres segons ja tenia accés a internet plenament operatiu per cable. Després vaig provar el wifi i tot anava perfecte.

Mirant-ho amb més detall, veig que la connexió es fa a Auto Ethernet, que fins llavors no havia sortit mai per enlloc.

Quan torno a casa, repeteixo la operació, desactivo wifi i connecto per cable. Al moment el portàtil es connecta a la xarxa, se li assigna ip4 i té connectivitat a internet. Durant els següents 5 minuts, ell sol va perdent i recuperant la connexió per cable, almenys cinc vegades, fins que finalment ja no la recupera i només em puc connectar a internet per wifi, quan el torno a habilitar.

Actualment l'arxiu etc/network/interfaces és exactament:
```
auto lo
iface lo inet loopback

```

L'arxiu etc/NetworkManager/nm-system-settings.conf ha quedat:
```
[main]
plugins=ifupdown,keyfile

no-auto-default=00:22:19:e2:97:1a,

[ifupdown]
managed=false
```

A etc/NetworkManager/system-connections hi tinc els arxius Auto etho i Auto Ethernet. El contingut és exactament el mateix en ambdos casos, només canvia el camp id:

```

[connection]
id=Auto Ethernet
uuid=b33f510d-40d3-4198-b1c3-78f3824b1585
type=802-3-ethernet
autoconnect=true
timestamp=0

[ipv4]
method=auto
ignore-auto-routes=false
ignore-auto-dns=false
dhcp-send-hostname=false
never-default=false

[802-3-ethernet]
speed=0
duplex=full
auto-negotiate=true
mac-address=0:22:19:e2:97:00
mtu=0

[ipv6]
method=ignore
ignore-auto-routes=false
ignore-auto-dns=false
never-default=false
```

El següent pas ha estat eliminar la connexió Auto eth0 i reiniciar, però tampoc es soluciona el problema.

He desactivat el wifi i he intentat veure el router per cable, però no puc. Connecto el wifi del portàtil i ja puc entrar al router. Comprovo a DHCP Clients List que només hi surt la wlan. He provat a canviar el cable de xarxa i el port del router, sense canvis.

Per avui ja en tinc prou, qualsevol idea serà benvinguda!

---

### Post by papapep on 2011-12-30
Jaumell,

Has provat què fa arrencant el mateix ordinador des d'un LiveCD o un pendrive? és per veure si el problema està en la configuració que tens a l'OS que tens instal·lat al disc dur.

Salut.

---

### Post by jaumell on 2012-01-03
Abans de res, perdoneu pel retard en la resposta, però he estat fent proves.

Em sembla que ja tinc el problema més encarat. Em sento talment així:

](*,)

El problema està localitzat en la relació entre el router ADSL i el portàtil.

Resumint: el portàtil va malament a casa però perfecte a la feina. Torno a casa, canvio el router per un de vell i voilà, funciona tant la xarxa per cable com per wi-fi. Algú ho entén?

Ho he provat arrancant el portàtil amb un live-cd de fedora16 i d'ubuntu 10.04 i tampoc hi ha manera que es connecti per cable de xarxa, però si per wi-fi.

He tornat a provar el router habitual i efectivament un netbook amb windows7 es connecta per cable sense problema. Tinc un router anti-linux? Fa anys que el tinc i sempre havia anat bé.

Em sembla que mataré el router, mort el gos...

Salutacions,

---

### Post by jaumell on 2012-01-17
Bon dia,

Finalment he canviat el router.

Sense canviar cap configuració de l'ubuntu, ara ja funciona tot perfectament.

Gràcies per la vostra ajuda!

Jaume

---

