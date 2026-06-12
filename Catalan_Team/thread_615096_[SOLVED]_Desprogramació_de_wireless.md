---
title: "[SOLVED] Desprogramació de wireless???"
date: 2007-11-16
forum: Catalan Team
---

### Post by alhanduin on 2007-11-16
Avui em conectava perfectament a internet via wireless xo la meva xicota ha estat putinejant les tecles per molestar-me una estona jejejej i aquesta nit no em conecta al wireless de casa al que sempre s'em conectava, he reiniciat l'ubuntu 2 cops i res.... no se si ha tocat una combinació de tecles que hagi desconectat el wireless...pot ser?

he fet un  lspci i em surt:

02:02.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
02:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:06.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
02:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller

i si faig un iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Aps si conecto l'ordenador per cable al modem si que s'em conecta... Sabeu què pot ser???? us ha passat mai?

---

### Post by alhanduin on 2007-11-16
He estat llegint i he vist que hi ha dispositius que es poden apagar i encendre i he fet:

sudo lshw -C network
[sudo] password for alhanduin:
  *-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 01
       serial: 00:c0:9f:68:82:d9
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=full ip=192.168.1.33 latency=64 link=yes module=b44 multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:82:18:3c
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.0kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 link=no maxlatency=24 mingnt=3 module=ipw2200 multicast=yes **wireless=radio off**

Sabeu com ho puc posar on???

---

### Post by alhanduin on 2007-11-16
Ja ho he solucionat!!!! Com que tot estava bé he hagut de posar (no se ben b com actua):

sudo modprobe acerhk

echo 1 > /proc/driver/acerhk/wirelessled

I ja sta!!!

---

### Post by farigola on 2007-11-16
Hola 
Avui he instal·lat una targeta de so al ordinador i m'ha funcionat a la primera. Després he fet una instal·lació de una nova targeta SMC SMCWPCIT-G a 802.11g 108Mbps i tinc ara per ara el mateix problema.

 lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=1/1
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-94 dBm  Noise level=-94 dBm
          Rx invalid nwid:16211  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

De ben segur que tenim la configuració malament. Estic verificant que podria ser.

---

### Post by farigola on 2007-11-16
Hola,
Perdoneu per no haver obert un nou tiquet. El problema el tenia amb la IP del portàtil doncs l'ordinador tenia la mateixa direcció I. He configurat el router per marcar les MAC que només tenen accés, un cop fet això he configurat un marge de IP d'aquesta manera al iniciar un altre cop la wireless aquest ha configurat una nova direcció.

Gràcies per tot i fins la propera.

---

### Post by alhanduin on 2007-11-17
Ei avui quan he obert el portàtil m'ho ha tornat a fer!!!! si reinicio el portàtil s'inicia amb la radio wireless off!!!! si poso els comandos que vaig escriure ahir torna a funcionar pero només fins que reinicio un altre cop l'ordenador!!!!!

Algú sap dir què puc fer????

---

### Post by papapep on 2007-11-17
Fica la instrucció dins /etc/modules.

---

### Post by alhanduin on 2007-11-17
Ei papapep he fet això (no se si ho fe fet be) i no mfunciona...:

sudo gedit /etc/modules

i allí dins he copiat la primera vegada les 2 frases i la segona vegada que ho he provat la segona frase. i cap de les 2 maneres m'ha funcionat... Ho faig malament??? si us plau diguem com ho he de fer xo com si fos tonto okis??? xq sóc novatillo

Això és el que tinc:

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
echo 1 > /proc/driver/acerhk/wirelessled

També he provat ficant les 2 frases (la que diu modprobe acerhk)

---

### Post by papapep on 2007-11-17
Has de ficar el mòdul que vols carregar dins el fitxer que t'he esmentat.

Afegeix una línia amb el nom del mòdul sota "sbp2". Segons tu, es diu **acerhk**. La resta que has posat abans, esborra-la.

---

### Post by alhanduin on 2007-11-17
mmmmm a vere... si t'he entes bé... he tret les linies que havia escrit i sota el sbp2 he escrit acerhk, i he guardat, quedant-me la cosa així:

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
acerhk

He reiniciat l'ordenador i no m funciona..... He buscat l'acerhk i és un arxiu .ko (que no se el que és i no puc obrir). Està ubicat a la capeta:   /lib/modules/2.6.22-14/generic/ubuntu/misc

MMMM.. A vere si entre tots m'ajudeu a trobar el que em passa!!! Sento que sempre em passin coses, i hagi de preguntar tant! La veritat és que us estic molt agraït ja que sempre acabo solucionant els problemes gràcies a vosaltres!

Merci! Sobretot a tú papapep

---

### Post by papapep on 2007-11-17
Fica la altra ordre dins /etc/profile:

```
sudo nano /etc/profile
```

i fica al final la ordre que has posat abans:

```
echo 1 > /proc/driver/acerhk/wirelessled

```

reinicia i a veure què tal.

---

### Post by alhanduin on 2007-11-17
Siiiiiiiiiiiiiiiiiiiiiiiiiiii ara sí!!!! Moltíssimes gràcies!!!! He fet el que m'has dit i he reiniciat i encara no s'havia obert l'escriptori que ja estava conectat x wifi!

No entenc massa el que he fet xo moltes gràcies papapep!

---

### Post by girotix on 2007-11-24
Salutacions, 

A mi també se'm desprograma la meva tarja de wifi. 

Només porto uns mesos amb l'Ubuntu (i amb Linux en general). Quan vaig instal·lar-lo al meu portàtil vaig tenir els habituals problemes amb la tarja wifi. (ho indicava en aquest post: [http://ubuntuforums.org/showthread.php?t=503259](http://ubuntuforums.org/showthread.php?t=503259)). 

La solució que en vau dir es trobava en un post del fòrum general d'Ubuntu, anomenat  HOWTO: Dell Inspiron E1505 Wireless (Broadcom 1390 WLAN) ([http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)). 

A l'actualitzar la nova versió d'Ubuntu aquesta configuració es va perdre. Després de cercar un xic vaig veure que la manera de configurar aquesta tarja era la mateixa que amb la anterior versió. Ho vaig fer i efectivament va tornar a funcionar.

El problema és que cada vegada apago l'ordinador es perd la configuració i he de tornar a escriure els comandaments en línia. Després d'uns quants prova i error (incloent reinstal·lacions de l'Ubuntu) he vist que hi ha un comandament que si l'escric em torna a funcionar, És aquest: SUDO MODPROBE NDISWRAPPER Així ho faig cada vegada però, és clar, això és un nyap. 

Em podeu dir com ho faig per què em quedi això configurat permanentment?

Moltes gràcies pel vostre fòrum,
Carles.

---

### Post by papapep on 2007-11-24
Crec que ficant la línia **ndiswrapper** al fitxer /etc/modules et farà la feina:

```
su -
```

i després:

```
echo ndiswrapper >> /etc/modules
```

Finalment:

```
exit
```

---

### Post by girotix on 2007-11-25
Quan accedeixo al Superusuari (tinc entès que el comandament "su -" serveix per això) em demana un password i quan li poso el meu em diu "authentication failure".

Ara no ho tinc clar però que jo sàpiga el meu password és... és el que jo sé (és l'únic que tinc).

Carles.

---

### Post by papapep on 2007-11-25
Si, primer et cal assignar password a root:

```
sudo passwd root
```

Aquesta serà la que et demanarà el sistema en fer su -.

---

### Post by girotix on 2007-11-26
Funciona! 

Moltes gràcies,
Carles.

---

