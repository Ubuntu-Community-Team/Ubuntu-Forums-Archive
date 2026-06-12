---
title: "He perdut la conexió a internet amb el mobil, via USB"
date: 2020-05-01
forum: Catalan Team
---

### Post by elbocha40 on 2020-05-01
Bon dia Estimats del Team .cat.

Fa temps que em conecto a inteernet amb el mobil fent servir la opció "modem USB"
Ahir estava navegant per internet mentre tractava d'instal.lar Tor i de cop i volta s'em va desconectar la maquina i tampoc vaig poder acabar instal.lant el navegador Tor.

Vaig probar de reiniciar la PC aixi com el telèfon i res.
Com a l'ordinador hi tinc win7, vaig provar alla si hi podia navegar i en aquest S.O. si que puc, fent servir el cable USB i la mateiza opció al telèfon de "modem USB"

A l'Ubuntu 18.04, s'em queda dient "conectant..." i acaba amb "error de conexió"

El que m'extranya es que pases mentre instal.lava el Tor.
He desabilitat el tallafocs UFW i he probat de forçar que agafi la dhcp a la interficie que en el meu cas es diu "enp5s0"

Us estare molt agraït si em podeu guiar per on podria probar d'arreglar-ho.
Una Abraçada a totes i tots.

PD: per si serveix, la PC es una P.B. Gigabyte Z68MX-UD2H-B3 amb 8GB de Ram i un proc. Intel i5 2500k

---

### Post by wgarcia on 2020-05-04
Pots enganxar la sortida de l'ordre:

```
lsusb
```

quan tens el mòbil connectat per cable USB i l'opció "modem USB" escollida?

---

### Post by elbocha40 on 2020-05-08
Bon dia,aquesta es la sprtida del lsusd

Bus 002 Device 003: ID 0458:0186 KYE Systems Corp. (Mouse Systems) 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 006: ID 1bbb:0174 T & A Mobile Phones 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 05e3:0732 Genesys Logic, Inc. All-in-One Cardreader
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 0951:1614 Kingston Technology 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04d9:2519 Holtek Semiconductor, Inc. Shenzhen LogoTech 2.4GHz receiver
Bus 001 Device 003: ID 0a5c:21e8 Broadcom Corp. BCM20702A0 Bluetooth 4.0
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

he probat un Linux Lite live USB i la conexio funciona perfecte pero cuan vaig a Ubuntu es queda "conectant"

Moltes gracies per l'atenció

---

### Post by wgarcia on 2020-05-08
No tinc clar si el teu Ubuntu està detectant el Modem USB o no. La línia:

```
Bus 005 Device 006: ID 1bbb:0174 T & A Mobile Phones 
```

sembla mostrar que està veient el mòbil, però no queda clar en qualitat de què ho veu, si com a espai d'emmagatzematge, dispositiu de xarxa o què.

Potser seria d'utilitat saber quina versió de l'Ubuntu tens instal·lada i quin és el model del mòbil. També pot ser útil la sortida de:

```
ifconfig -a
```

tant directament a l'Ubuntu, com a la sessió life que mencionaves.

---

### Post by elbocha40 on 2020-05-09
Hola WGarcia

la versió que tinc instal.lada de l'Ubuntu és la 18.04.4 i el teléfon que faig servir per conectar-me és un Alcatel One

Aqui la sortida de l'Ubuntu:

jaija@jaija-Z68MX-UD2H-B3:~$ ifconfig -a
enp5s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 50:e5:49:5f:fd:25  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

enp6s0u2: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        ether fe:76:c9:85:2b:ce  txqueuelen 1000  (Ethernet)
        RX packets 3  bytes 328 (328.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 58  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 12707  bytes 1262114 (1.2 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 12707  bytes 1262114 (1.2 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


I aqui les sortides de la versio live del Linux Lite v3.4

  	 	 	 	   linux@linux:~$ lsusb
 Bus 002 Device 003: ID 0458:0186 KYE Systems Corp. (Mouse Systems)  
 Bus 002 Device 004: ID 18a5:0302 Verbatim, Ltd Flash Drive
 Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
 Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
 Bus 005 Device 003: ID 1bbb:0174 T & A Mobile Phones  
 Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 Bus 004 Device 002: ID 05e3:0732 Genesys Logic, Inc. All-in-One Cardreader
 Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
 Bus 003 Device 002: ID 0951:1614 Kingston Technology  
 Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 Bus 001 Device 004: ID 04d9:2519 Holtek Semiconductor, Inc. Shenzhen LogoTech 2.4GHz receiver
 Bus 001 Device 003: ID 0a5c:21e8 Broadcom Corp. BCM20702A0 Bluetooth 4.0
 Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 
 
 linux@linux:~$ ifconfig -a
 enp5s0    Link encap:Ethernet  HWaddr 50:e5:49:5f:fd:25   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
 
 
 enp6s0u2  Link encap:Ethernet  HWaddr 06:f6:d8:cf:04:1b   
           inet addr:192.168.42.72  Bcast:192.168.42.255  Mask:255.255.255.0
           inet6 addr: fe80::1113:d0fb:d307:526d/64 Scope:Link
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
           RX packets:13193 errors:0 dropped:0 overruns:0 frame:0
           TX packets:13439 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000  
           RX bytes:11368192 (11.3 MB)  TX bytes:1986993 (1.9 MB)
 
 
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0
           inet6 addr: ::1/128 Scope:Host
           UP LOOPBACK RUNNING  MTU:65536  Metric:1
           RX packets:2841 errors:0 dropped:0 overruns:0 frame:0
           TX packets:2841 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1  
           RX bytes:269255 (269.2 KB)  TX bytes:269255 (269.2 KB)
  
Be doncs, espero la teva resposta.

Moltes gràcies

---

