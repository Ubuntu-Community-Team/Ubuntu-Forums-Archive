---
title: "No puc accedir al router"
date: 2011-02-19
forum: Catalan Team
---

### Post by joaquimrubio on 2011-02-19
Vull accedir al router per modificar uns pots.
Faig el següent:
Obro la consola, teclejo "ipconfig" i premo la tecla "enter"
La consola en torna això (les cometes són per acotar):

"joaquim@joaquim-laptop:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:1f:d0:12:43:78  
          inet addr:192.168.1.128  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:d0ff:fe12:4378/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4855 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4796 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4547115 (4.5 MB)  TX bytes:761089 (761.0 KB)
          Interrupt:26 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:194 errors:0 dropped:0 overruns:0 frame:0
          TX packets:194 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17195 (17.1 KB)  TX bytes:17195 (17.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1d:1a:04:7e:95  
          inet6 addr: fe80::21d:1aff:fe04:7e95/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:15322 errors:0 dropped:0 overruns:0 frame:0
          TX packets:304 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1544362 (1.5 MB)  TX bytes:0 (0.0 B)
          Interrupt:20 

joaquim@joaquim-laptop:~$ "

Aleshores, obro el navegador i a la barra d'adreces teclejo: [http://192.168.1.128](http://192.168.1.128) i altre cop premo la tecla "Enter".

El navegador em contesta(les cometes són per acotar):

"No s'ha pogut connectar.
El Firefox no ha pogut establir una connexió amb el servidor a 192.168.1.128.
    *   El lloc web podria estar temporalment no disponible o massa ocupat. Torneu-ho a provar d'ací uns moments.
    *   Si no podeu carregar cap pàgina, comproveu la connexió a la xarxa del vostre
          ordinador.
    *   Si el vostre ordinador o la vostra xarxa estan protegits per un tallafocs o per un servidor intermediari, assegureu-vos que el Firefox tingui permís per a accedir al WWW."

Per a tota la resta, la nevagació funciona perfecte.
Què faig malament?

---

### Post by kimet on 2011-02-19
Company, aquesta no es la direcció del teu router, es la del teu ordinador...

```
cat /etc/network/interfaces | grep gateway
```
Segurament serà 192.168.1.1

---

### Post by joaquimrubio on 2011-02-20
Correcte, no era la direcció de router, la que has propositat si ho era.
Problema resolt.
Gràcies.

---

