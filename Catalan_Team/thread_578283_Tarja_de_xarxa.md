---
title: "Tarja de xarxa"
date: 2007-10-17
forum: Catalan Team
---

### Post by slink on 2007-10-17
He perdut la conexió a Internet i el meu proveidor em diu que he de canviar la tarjeta de xarxa (ethernet, modem ADSL). 

He provat de fer:

```
lspci |grep eth
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
```

pero si faig:

```
dmesg |grep eth
[   19.737197] eth0: VIA Rhine II at 0x1b400, , IRQ 17.
[   19.737911] eth0: MII PHY found at address 1, status 0x7849 advertising 01e1 Link 0000.

[   29.645427] eth0: link down

[   48.175872] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  455.575087] eth0: link down
[  455.575257] ADDRCONF(NETDEV_UP): eth0: link is not ready
```

Fa referència a link down. He canviat el cable ethernet PC-MODEM, per lo que entenc que no és el cable. 

El problema ve de que no aconsegueixo adreçes IP vàlides de DHCP:

```
ifconfig
eth0      Link encap:Ethernet  HWaddr 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xb400 

eth0:avah Link encap:Ethernet  HWaddr 
          inet addr:169.254.9.22  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0xb400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2280 (2.2 KiB)  TX bytes:2280 (2.2 KiB)
```

Que penseu? He de canviar la tarja?

---

### Post by Ferri on 2007-10-17
Pots fer ping al teu router? Per exemple:
```
ping 192.168.1.1
```
Posa-hi la IP que hi tinguis configurada (pasarel·la per defecte o default gateway). La que he posat jo és bastant habitual, però no sempre és la mateixa.
Si et funciona, indicaria que el problema és del router enfora i no a la teva tarja.

---

### Post by slink on 2007-10-18
> Posa-hi la IP que hi tinguis configurada

És que no sé quina és la meva passarela. Fent ifconfig es veu que no s'em assigna cap IP. El sistema s'autoassigna una IP que comença per 169.254.x.x però no és vàlida. 

Puc provar 169.254.255.255. o 192.168.1.1 però no podré estar segur d'estar fent ping al módem...


COM PUC SABER LA MEVA GATEWAY ?

---

### Post by slink on 2007-10-18
I si faig route em diu:

```
route
Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
link-local      *               255.255.0.0     U     0      0        0 eth0
default         *               0.0.0.0         U     1000   0        0 eth0
```

---

### Post by Ferri on 2007-10-18
Què et diu si fas:
```
sudo ifdown eth0
```
i després:
```
sudo ifup eth0
```

---

### Post by slink on 2007-10-18
Guaita, em diu:

```
felix@ordinador:~$ sudo ifdown eth0
Password:
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 5239
killed old client process, removed PID file
Listening on LPF/eth0/
Sending on   LPF/eth0/
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 10.127.36.140 port 67


felix@ordinador:~$ sudo ifup eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Listening on LPF/eth0/
Sending on   LPF/eth0/
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

També he provat:

dhclient

sudo /etc/init.d/networking restart

/var/run/dhclient.eth0.pid

He reinstalat el sistema, res...

Crec que és cosa del modem, perque si faig route -n no m'apareix, pero el meu proveidor ONO no m'el vol canviar perque diu que està be. Diu que m'he de canviar la tarjeta de xarxa.

---

### Post by slink on 2007-10-18
Serà que tinc el port 67 tancat i l'he d'obrir?

---

### Post by papapep on 2007-10-18
El que sembla és que no tinguis cap servidor DHCP funcionant a la xarxa:

> No DHCPOFFERS received.

"No s'han rebut ofertes DHCP"

---

### Post by Ferri on 2007-10-18
Se suposa que fas servir DHCP, no deus tenir una IP fixa?

---

### Post by slink on 2007-10-18
La questió és que no aconsegueix que el servidor DHCP li assigni una IP. 

De fet, crec que no pot establir contacte amb el modem. Crec.

El proveïdor diu que el senyal arriba al modem, per lo que és problema de:

a) Configuració del Sistema

b) Tarjeta de Xarxa


He descartat que sigui l'Ubuntu. He baixat l'instal.lador aquest matí, he instalat de nou. Segueixo igual. 

Només em queda comprar-me una tarja de xarxa nova, total només costa 10 euros, i és compatible amb Linux. 

El que em fa por és que el sistema ara reconeix la tarja, no? Entenc que està be.
```

lspci |grep eth
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)

dmesg |grep eth
[   19.737197] eth0: VIA Rhine II at 0x1b400, , IRQ 17.
[   19.737911] eth0: MII PHY found at address 1, status 0x7849 advertising 01e1 Link 0000.
[   29.645427] eth0: link down
[   48.175872] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  455.575087] eth0: link down
[  455.575257] ADDRCONF(NETDEV_UP): eth0: link is not ready
```

Si li afegeixo una altra tarja... armaré on bon cacau!!!

O puc desactivar-ne una ? Com ?

O l'Ubuntu reconeix automàticament en quina de les 2 està conectat el cable ethernet ?

Estic una mica desesperat... qualsevol opinió que tingueu serà ben rebuda. Gràcies.

---

### Post by slink on 2007-10-18
Si el llum PC-LINK del modem està apagat, vol dir aixó que és la tarja ethernet la que no funciona?

---

