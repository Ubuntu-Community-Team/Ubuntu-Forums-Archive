---
title: "els drivers de l'Ubuntu?"
date: 2008-12-04
forum: Catalan Team
---

### Post by jinglada on 2008-12-04
1) Fa dues setmanes que tinc el portàtil nou dels que fan els pcbox (innobo) i el primer problema que se'm va presentar és que a l'engegar-lo no es connecta mai a internet i l'he de reiniciar, de vegades fins i tot dos cops. La connexió és ADSL amb cable. Ho vaig dir a PC-Box i em diuen que "els drivers de l'Ubuntu ...", així amb punts suspensius.

Què us sembla?

---

### Post by albandy on 2008-12-04
pots fer un lspci a la consola i empegar-ho aqui?

sudo lspci

---

### Post by papapep on 2008-12-04
> He d'obrir un fil diferent per a cada problema?

Sí, si us plau. I modifica, també si us plau, el títol del fil per a que sigui indicatiu del teu problema real, sigui de xarxa o del que sigui.

---

### Post by jinglada on 2008-12-04
joan@joan-laptop:~$ sudo lspci
[sudo] password for joan: 
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.5 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
14:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
1a:00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
1a:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
1a:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
1a:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller

---

### Post by papapep on 2008-12-04
Fes un:

```
ifconfig
```

tant quan es connecta, com quan no. I enganxa el resultat d'ambdós casos.

---

### Post by jinglada on 2008-12-04
Ho faré quan torni a engegar i ho enviaré.
Ara recordo que no ho he escrit, que si estic treballant sense connexió i vull connectar-me, endollo el cable de xarxa i marcant l'"Auto eth0" no ho he aconseguit mai; sempre he d'engegar l'ordinador tenint el cable de xarxa connectat prèviament i tot i així, com he dit abans, gairebé sempre he de reiniciar.
Tant amb el Mac que tenia com amb el Samsung de la meva filla, just en el moment de connectar el cable es connectava automàticament a la xarxa en breus instants.

---

### Post by albandy on 2008-12-04
prova sudo dhclient eth0

---

### Post by jinglada on 2008-12-04
**abans de desconnectar per anar a dinar:**

joan@joan-laptop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:58:76:6d  
          inet addr:192.168.1.78  Bcast:192.168.1.255  Mask:255.255.255.0 
          inet6 addr: fe80::21e:ecff:fe58:766d/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:44620 errors:0 dropped:21726657420 overruns:0 frame:0 
          TX packets:32201 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:55895496 (55.8 MB)  TX bytes:4301528 (4.3 MB) 
          Interrupt:250 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:242 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:242 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:15140 (15.1 KB)  TX bytes:15140 (15.1 KB) 

joan@joan-laptop:~$ 

**Després de dinar he engegat i no s'ha connectat a la primera:**

joan@joan-laptop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:58:76:6d  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:42949672950 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:250 Base address:0xa000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B) 

joan@joan-laptop:~$ 

**He reiniciat i s'ha connectat:**

joan@joan-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:58:76:6d  
          inet addr:192.168.1.78  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:1092882715 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1424 (1.4 KB)  TX bytes:3426 (3.4 KB)
          Interrupt:250 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)

joan@joan-laptop:~$

---

### Post by jinglada on 2008-12-04
joan@joan-laptop:~$ sudo dhclient eth0
[sudo] password for joan: 
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1e:ec:58:76:6d
Sending on   LPF/eth0/00:1e:ec:58:76:6d
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER of 192.168.1.78 from 192.168.1.1
DHCPREQUEST of 192.168.1.78 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.78 from 192.168.1.1
bound to 192.168.1.78 -- renewal in 32479 seconds.
joan@joan-laptop:~$

---

### Post by albandy on 2008-12-04
Pot ser un problema de negociacio amb el switch.
Quan no et conecti prova a fer:
sudo mii-tool eth0
i poses la resposta.

També pot ser un problema amb el cable o amb la targeta. Dubto que sigui el driver perque es una targeta bastant estandard, jo tinc la mateixa i funciona perfectament.

---

### Post by jinglada on 2008-12-04
Aquesta vegada he hagut de reiniciar dues vegades però desconnectat dóna:

joan@joan-laptop:~$ sudo mii-tool eth0 
[sudo] password for joan: 
  No MII transceiver present!. 
joan@joan-laptop:~$ 

Quan s'ha connectat em dóna:
joan@joan-laptop:~$ sudo mii-tool eth0 
[sudo] password for joan: 
eth0: negotiated 100baseTx-FD, link ok 
joan@joan-laptop:~$

---

### Post by albandy on 2008-12-04
mal rotllo.
Això és que per algun motiu no inicia la interficie al arrencar.
Has provat amb un altre cable?

Prova també quan et digui "No MII transceiver present" a fer això:
sudo ifconfig eth0 up
sudo mii-tool eth0

Si d'aquesta manera funciona potser es pot fer un petit "Workarround" encara que ja et dic que jo tinc la mateixa targeta de xarxa i funciona a la primera.

---

### Post by jinglada on 2008-12-05
Hola, 
no fa res quan faig "sudo ifconfig eth0 up".
mal rotllo? 

joan@joan-laptop:~$ sudo mii-tool eth0 
[sudo] password for joan: 
  No MII transceiver present!. 
joan@joan-laptop:~$ sudo ifconfig eth0 up 
joan@joan-laptop:~$ 
joan@joan-laptop:~$ sudo mii-tool eth0 
  No MII transceiver present!. 
joan@joan-laptop:~$ 

Què és Workarround?

---

