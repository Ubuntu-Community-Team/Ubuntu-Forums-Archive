---
title: "Conexions ONO vs UBUNTU"
date: 2007-10-25
forum: Catalan Team
---

### Post by Quartcreixent on 2007-10-25
[SIZE="3"][COLOR="DarkRed"]Bon dia! Com anam? Ja em començ a manejar dins l'ubuntu sense problemes, i més ara amb el 7.10!, però a la connexió de ca meva no hi ha manera. Tenc la connexió per Cable de ONO de 3 mg. Amb telefònica no tenc cap problema, ni amb IP estàtica ni automàtic. Sabeu com ho puc fer? Fa dies que cerc qualque solució però no trop res que em vagi bé.
Estaré molt agraïda! 
Fins aviat tuxets![/COLOR][/SIZE]
:lolflag:

---

### Post by RafaelCarreras on 2007-10-25
Hola Quartcreixent.
Les connexions per cable són automàtiques. No recordo haver hagut de configurar mai res. Ens pots donar més dades? Surt algun missatge d'error?

---

### Post by slink on 2007-10-25
Hola Quartcreixent, 

jo he tingut conexió amb ONO durant molt temps. No he hagut de configurar res, l'Ubuntu s'encarrega d'aixó. 

Fins i tot ara que he perdut la conexió per ethernet (cable de telèfon), puc conectar amb el mòdem (THOMSON TCM 390) via USB, ell solet ho ha fet tot, sense drivers ni res.

Prova de fer:

[FONT="Courier New"]ping 192.168.100.1[/FONT]

i
[FONT="Courier New"]
ifconfig[/FONT]

a veure que diu.

---

### Post by slink on 2007-10-26
consell: si escrius el que diu ifconfig, amaga alguns valors com HWaddr , inet addr 


```
felix@ordinador:~$ ifconfig | cat
eth0      Link encap:Ethernet  HWaddr XXX
          inet addr:62.57.XXX.XXX  Bcast:255.255.:XXX.XXX  Mask:255.255.XXX.XXX
          inet6 addr: fe80::20b:6aff:fef2:1dfc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:214719 errors:0 dropped:0 overruns:0 frame:0
          TX packets:214212 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:122849388 (117.1 MiB)  TX bytes:34522244 (32.9 MiB)
          Interrupt:17 Base address:0xb400

lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:60 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3577 (3.4 KiB)  TX bytes:3577 (3.4 KiB)
```

---

### Post by Quartcreixent on 2007-10-27
Ho he provat tot el que em dieu i no hi ha manera... :(

---

