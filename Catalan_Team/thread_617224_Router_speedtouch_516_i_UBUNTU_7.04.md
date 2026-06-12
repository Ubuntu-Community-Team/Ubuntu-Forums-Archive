---
title: "Router speedtouch 516 i UBUNTU 7.04"
date: 2007-11-19
forum: Catalan Team
---

### Post by Gisela on 2007-11-19
Bon dia!

Mireu, jo sóc molt nova amb Linux. De fet, he decidit fa poquet fer el salt (amb un ordinador Acer, una mica vell, però encara amb molta corda). Quan vaig fer la instal·lació d'Ubuntu 7.04 no tenia el router prèviament instal·lat a l'ordi, potser per això no el va reconèixer i no el va detectar. En qualsevol cas, ara voldria fer-ho manualment i no me'n surto.

Tinc internet amb Ya.com (ethernet) (amb un router thomson speedtouch 516) i en les instruccions per instal·lar el router només m'han proporcionat una direcció IP fixa (tot i que ja m'avisen que no em cal perquè haig d'utilitzar la via ethernet).

Si provo de fer la connexió manual a Ubuntu i escullo IP, tan sols puc completar una dada. A la documentació de Ya.COM no tinc cap número per a la màscara subred, porta d'enllaç, etc. I això m'ho demana l'Ubuntu per fer la connexió amb IP. 
Per això he provat de fer la connexió a través de l'opció DHCP, però tampoc no em funciona.
He mirat en alguns fòrums i he trobat algunes dades pel que fa als números de subred/porta d'enllàç, etc. Ho he provat i tampoc no em funciona...

Potser tot plegat és més fàcil del que sembla però he mirat per internet i he vist comentaris amb instruccions complexes quan volen configurar un router. Tot i això, malauramdament en cap forum he trobat res específic per al router st516. 

Us faria res donar-me un cop de mà? O bé indicar-me si hi ha algun forum on puc trobar les instruccions concretes per al meu cas?

Moltes gràcies per la vostra col·laboració! 

Gi

---

### Post by CarlesOriol on 2007-11-19
Eps. Bones. Jo tenia un router d'aquests fins que el vaig canviar la setmana passada.

Cal una mica més d'informació per ajudar-te. La linia adsl és nova? El router és nou? El tens funcionant en algun altre sistema antic?

I ara preguntes tècniques. 
Configura el router en mode DHCP. ves a un terminal i escrius ( i ens copies tot el que respongui l'ordinador)

> sudo dhclient eth0

> sudo ifconfig eth0

> cat /etc/resolv.conf

---

### Post by papapep on 2007-11-19
Bones Gisela,

Per la màscara posa 255.255.255.0
Per la passarela, o porta d'enllaç, fica la ip del router que t'han dit els de Ya.com
Suposant que la ip del router fos: 192.168.1.1, fica com a ip del pc 192.168.1.2 (per exemple, el que vull dir és que només et cal variar la última xifra per a estar al mateix rang de xarxa i poder-hi accedir), i ja podràs accedir a configurar el router via navegador posant la ip del mateix (la abans suposada 192.168.1.1).

---

### Post by SiscoGarcia on 2007-11-19
Benvinguda al fòrum,Gisela.
A part dels consells dels "mestres" papapep i CarlesOriol, que hauries de seguir fil per randa, em permeto suggerir-te la pàgina [http://www.adslayuda.com/Thomson.html](http://www.adslayuda.com/Thomson.html)  on pots trobar alguna idea per configurar-te i "tunejar-te" el router.

I ara, a gaudir amb l'ubuntu!

---

### Post by Gisela on 2007-11-20
Bon dia i gràcies per la vostra ràpida resposta i els vostres consells!

A veure, responc primer els detalls que em demana CarlesOriol:

--La línia ADSL la vaig donar d'alta el passat mes de setembre (2007), amb ya.com

--El router és el que em va assignar ya.com (setembre 2007): thomson speedtouch 516 v6.

--He instal•lat Ubuntu 7.04 en un PC pentium IV. Estic molt satisfeta del disseny i les aplicacions, etc. Ubuntu és genial! Tan sols em caldria la connexió a internet.

--Utilitzo el mateix router per connectar-me a internet des d'un altre ordinador (amb Windows XP). És des d'aquest que miro el fòrum i us escric aquest missatge.

--Després d'escriure a la terminal les teves indicacions, la resposta és:

Gi@Bobby:~$ sudo dhclient eth0 
Password: 
Sorry, try again. 
Password: 
sudo: 1 incorrect password attempt 
Gi@Bobby:~$ dhclient eth0 
Internet Systems Consortium DHCP Client V3.0.4 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 

can't create /var/lib/dhcp3/dhclient.leases: Permission denied 
Can't create /var/run/dhclient.pid: Permission denied 
drop_privileges: could not set group id: Operation not permitted 
Gi@Bobby:~$ ifconfig eth0 
eth0      Link encap:Ethernet  HWaddr 00:0A:E4:42:F1:72  
          inet6 addr: fe80::20a:e4ff:fe42:f172/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:1115 (1.0 KiB)  TX bytes:2325 (2.2 KiB) 
          Interrupt:22 

Gi@Bobby:~$ cat /etc/resolv.conf 
Gi@Bobby:~$ cat /etc resolv.conf 
cat: /etc: Is a directory 
cat: resolv.conf: No such file or directory 

Tinc la sensació que potser no he fet bé alguna cosa...No sé.
Et serveix de res el que m'ha proporcionat la terminal? Espero que sí.

--He deixat la connexió (a "network settings") en DHCP. Per si és útil, t'informo que a la pestanya DNS em diu 192.168.1.254, i a la pestanya de "HOsts", d'entre les moltes que hi ha, em ressalta l'adreça IP 127.0.0.1 localhost


Per altra banda, Papapep, he provat el que m'aconselles i em temo que no em va bé.
La IP que m'indica ya.com és 89.131.39.48.
En canvi, a les instruccions per configurar el router (procés que vaig seguir en el cas de Windows XP) hi ha un moment en què, amb l'EXplorer obert, l'usuari ha d'escriure la direcció 192.168.1.254 per accedir a la configuració del router i anar seguint els passos...

Us puc donar alguna dada més? Només cal que m'ho digueu!
Se us acut alguna nova estratègia a partir de les dades que he proporcionat en aquest missatge?

De nou us dono les gràcies a tots per la vostra col·laboració i confio que, finalment, pugui configurar el router, accedit a internet i gaudir d'Ubuntu al 100x100.


Fins aviat, ubuntaires!

Gi

---

### Post by CarlesOriol on 2007-11-20
Torna a fer el sudo dhclient eth0 i posa be la password.

---

### Post by papapep on 2007-11-20
Una altra possibilitat que tens és passar olímpicament de DHCP i ficar una ip fixa al pc. Igual t'estalviaries maldecaps. Tens alguna necessitat concreta de tenir-ho per DHCP?

---

### Post by Gisela on 2007-11-21
Ostres! Tens raó. Ho sento! Ara he posat bé la password (com que abans no em sortia res a la pantalla quan l'escrivia, devia equivocar-me) i et copio tot el que m'ha dit la terminal a partir de les 3 indicacions que em vas donar. Espero que serveixi.

gi@Bobby:~$ sudo dhclient eth0 
There is already a pid file /var/run/dhclient.pid with pid 134993416 
Internet Systems Consortium DHCP Client V3.0.4 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 

Listening on LPF/eth0/00:0a:e4:42:f1:72 
Sending on   LPF/eth0/00:0a:e4:42:f1:72 
Sending on   Socket/fallback 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 
No DHCPOFFERS received. 
No working leases in persistent database - sleeping. 
gi@Bobby:~$ sudo ifconfig eth0 
eth0      Link encap:Ethernet  HWaddr 00:0A:E4:42:F1:72  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:22 Base address:0xa000 

gi@Bobby:~$ cat /etc/resolv.conf 
search lan 
nameserver 192.168.1.254 


Caldria alguna dada més? Ja m'ho direu!

Cada vegada m'agrada més l'Ubuntu (de moment, el 7.04) i tinc moltes ganes de fer-hi cosetes. L'accés a internet serà fonamental...

Moltes gràcies per tot (de veritat) i fins aviat!

Gi

---

### Post by patrickfromspain on 2007-11-21
Proba aixo: 

Sistema -> Administracio -> Xarxa
alla, elegeix la teva tarja ethernet i hi poses aixo:

Adreça IP: 192.168.1.60
Mascara: 255.255.255.0
Porta d'enllaç: 192.168.1.254

A la pestanya DNS, hi poses:
208.67.222.222
208.67.220.220

salut i a veure si aixo et funciona!

---

### Post by Gisela on 2007-11-23
Bon dia!

Em sap greu però la suggerència de Patrick no em funciona. He posat l'IP i les altres dades tal com molt amablement m'indiques però no em puc connectar a internet.

Una pregunta: quan dius "elegeix la teva tarja ethernet", a què et refereixes? A la pestanya de "Xarxa" només puc triar el tipus de connexió (IP fixa, DHCP...). Per si de cas, he anat a Sistema> Admin.> "Networking", i allà he configurat eth0 tal com m'has recomanat. Tampoc no em va bé.

Hi ha alguna cosa que no faig bé. Això està clar. Algú té idea de què es tracta?

CarlesOriol: tens prou dades per trobar la fòrmula d'accés a internet via DHCP? Si et cal res més, ja m'ho diràs! Merci!

Estic molt agraïda per totes les respostes i el "bon rotllo" de la comunitat Ubuntu. Gràcies de nou a tots!

Gi

---

### Post by CarlesOriol on 2007-11-23
Un cop fet el que et diu en patrick prova dues coses:

1 - Si va la xarxa fins el router. Fes

ping 192.168.1.254

2 - Si això no dona errors fas
 
ping 66.249.93.99


3 - Si això no dona errors fas:

ping [www.google.com](www.google.com)

i ens copies el resultat  (fins on arribis)

---

### Post by Gisela on 2007-12-03
Gràcies per la resposta i perdoneu que contesti tant tard (he estat mig engripada uns dies, sense energies per engegar l'ordi...)

He provat això del ping (després d'haver introduit les coordenades que m'ìndicava el PatricK) i em temo que no em funciona.

Ara bé, per si de cas, vull assegurar-me que ho he fet bé:

--el ping el faig des del terminal i em dóna errors: una seqüència inacabable d'intents fallits amb el missatge final: Destination Host Unreachable.

--el ping el faig dins de "Administració" > "Eines xarxa" i tampoc no em funciona.

Vaig perduda i un xic desanimada perquè no me'n surto.

Espero que els vostres consells (molt amables, per cert) em puguin treure d'aquest enrenou.

Gràcies de nou i fins aviat, Ubuntaires!

Gi

---

### Post by CarlesOriol on 2007-12-06
Repassem:

Posa la configuració d'en patrick i fes els pings que t'he demanat.
Prova també un ping a 192.168.1.1

Més informació:

Si disposes d'un sistema operatiu d'aquells vells configurat pots fer inicio > ejecutar > cmd i allà escriure ipconfig i copiar-nos el resultat.

---

### Post by Gisela on 2007-12-11
Bon dia!

Em temo que no segueixo sense tenir bones notícies.

A veure. M'explico i així repassem:
No aconsegueixo connectarme a internet amb el router Speedtouch 516 Thomson. Engego el portàtil, amb el cable ethernet connectat i es carrega l'Ubuntu 7.04. Entro l'usuari i la password. Tot seguit vaig a "Sistema">"Administració"> Xarxa. Dins de "connexions", selecciono "wired connection" i configuro la IP estàtica amb l'adreça, la màscara i la porta d'enllaç que m'ha indicat el Patrick. Un cop fet això, em connecto al Firefox i res. No hi ha connexió. Torno a sistema>administració> eines xarxa, i a la primera pestanya ("devices"), veig dues opcions: 
(a) loopback interface (lo); 
i (b) ethernet interace (eth0). 
Selecciono el segon (eth0) i m'adono que hi ha "2 IP informations" dins d'eth0: 
(a) Protocol IPv$ / 192.168.1.60 / 255.255.255.0 / 192.168.1.255;
i (b) procolo IPv6 / fe80::20a:e4ff:fe42:f172 / 42 / link (scope).
M'imagino que haig de seleccionar la primera opció, és a dir, la que té la mateixa configuració que he fet abans.
Firefox segueix sense funcionar.
Provo els pings que m'indica el Carles Oriol. Primer ho faig des del terminal i em respon amb una llarguíssima llista de frases d'error amb la informació final "Destinatrion HOst Unreachable".
En segon lloc, provo de fer els pings anteriors dins de Sistema>administració>"Network tools (eines xarxa), dins de la pestanya "ping" i tampoc no va bé.

Vaja, començo a témer que la cosa no pita gaire bé i que hi ha més d'una cosa que no faig bé. Estic una mica desanimada...vaja!

Algú en pot treure l'entrellat? Merci!

Us agraeixo molt el vostre interès i la vostra paciència amb una ubuntaire tan poc hàbil...

Gràcies i a reveure!

Gi

---

### Post by patrickfromspain on 2007-12-11
comprova les DNS, a veure que no ens estiguessin emprenyant. Administracio -> Xarxa -> pestanya DNS   i alla hi poses 208.67.222.222 i 208.67.220.220

---

### Post by papapep on 2007-12-11
Crec que ha arribat el moment de "enfocar" una mica el tema, que entre tots plegats hem anat fent trets a l'aire.

Executa aquestes ordres i ves enganxant el resultat que et vagin donant:

> ifconfig

> route

```
cat /etc/resolv.conf
```

```
cat /etc/network/interfaces
```

Amb aquesta informació crec que podrem anar definint una mica millor com resoldre el tema.

---

### Post by Gisela on 2007-12-12
Hola,

Potser tens raó, Papapep. 
He fet el que m'aconselles i aquí teniu els resultats (per cert, Patrick, he comprovat els DNS i són els que em vas indicar):

gi@Bobby:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:0A:E4:42:F1:72   
          inet addr:192.168.1.60  Bcast:192.168.1.255  Mask:255.255.255.0 
          inet6 addr: fe80::20a:e4ff:fe42:f172/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:180 (180.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:21 Base address:0x6000  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:1177 (1.1 KiB)  TX bytes:1177 (1.1 KiB) 
 
gi@Bobby:~$ route 
Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0 
link-local      *               255.255.0.0     U     1000   0        0 eth0 
default         192.168.1.254   0.0.0.0         UG    0      0        0 eth0 

gi@Bobby:~$ cat /etc/resolv.conf 
nameserver 208.67.222.222 
nameserver 208.67.220.220 
search lan

gi@Bobby:~$ cat /etc/network/interfaces 
auto lo 
iface lo inet loopback 
  
auto eth1 
iface eth1 inet dhcp 
 
auto eth2 
iface eth2 inet dhcp 
 
auto ath0 
iface ath0 inet dhcp 
 
auto wlan0 
iface wlan0 inet dhcp 
 
 
iface eth0 inet static 
address 192.168.1.60 
netmask 255.255.255.0 
gateway 192.168.1.254 
 
auto eth0 

==================================

Vinga, de nou moooltes gràcies a tots!
Espero amb gran expectació les vostres respostes...

Gi

---

### Post by ilku on 2007-12-12
Hola Company:

Però quantes tarjetes de xarxa tens sembla un macro servidor ;).
Jo de tu miraria a quina es la que utilitza realment i suprimiria les altres, potser es fa un embolic.

Per exemple pel que he vist en el cat /etc/network/interfaces: eth0 es la utilitzada, llavors treu eth1, eth2, ath0 i wlan0 (si no té wi-fi)

Ja diras

---

### Post by papapep on 2007-12-12
A veure, fes que el **/etc/network/interfaces** et quedi de la següent manera:

```
sudo nano /etc/network/interfaces
```

```

# The loopback interface
auto lo

iface lo inet loopback

auto eth0
iface eth0 inet static
  address 192.168.1.60
  netmask 255.255.255.0
  network 192.168.1.0
  broadcast 192.168.1.255
  gateway 192.168.1.254 
```

Surt desant amb Ctrl+X

El fitxer **/etc/resolv.conf**, hauria de quedar així:

```
search lan
nameserver 62.151.2.8
nameserver 62.151.4.21
```

A veure què tal així.

---

### Post by Tomàs M. on 2007-12-15
I si té el filtrat de MAC activat? Això et pot fer perdre l'oremus...
Prova d'entrar al router amb el sistema operatiu antic ([http://192.168.0.1](http://192.168.0.1) o [http://192.168.1.1](http://192.168.1.1) segurament.. o potser [http://192.168.1.254](http://192.168.1.254), pel que he vist).
Ara pot ser que sigui molt semblant a això o no; al 580 és així:
-Básico - inalámbrico - seguridad - control de acceso. Què hi diu a modo de acceso ACL? Per a descartar coses... 
Si estés a nuevas estaciones permitidas (mediante registro), potser tens un botó a l'encaminador que t'obre l'accés i el registre automàtic de noves estacions durant un minut després de prémer-lo (o hauries de provar amb nuevas estaciones permitidas automàticamente)
Sort!

---

### Post by Miquel Ubuntero on 2007-12-15
Hola Gisela.
Jo tic el mateix módem que tú i també ya.com
Hem funciona be. T'explico com el vaig configurar.
Sistema - Administració - Xarxa
Tries la connexió i a propietats posa DHCP.
A la pestanya DNS posa la IP del router (la trobaràs a la "guia rápida de instalación" de ya.com al "PASO 1") En el meu cas era 192.168.1.254
es molt important que facis amb cura tot el que la guia de ya.com diu. tenin en conte el tipus de conexió tens. A la carta de "Bienvenida" verifica el tipus de conexió.
Anims, que segur que funcionarà.
Salut!

---

