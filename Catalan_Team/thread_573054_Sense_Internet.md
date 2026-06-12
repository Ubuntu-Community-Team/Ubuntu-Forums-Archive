---
title: "Sense Internet"
date: 2007-10-11
forum: Catalan Team
---

### Post by slink on 2007-10-11
Hola, 

desde la tempesta de dilluns que no tinc Internet. Avui el modem ADSL ha tornat a pampallugejar. Segons la companyia, el senyal ara arriba al modem, per tant cal que comprovi si em funciona be la tarja d'ethernet. Aixó no ho se fer. M'han dit que amb windows seria algo com Inici>Preferencies>Sistema>Hardware>Dispositius i comprovar que la tarja no tingui una creu o un triagle groc... però no tinc Windows...

Com puc comprovar si la tarja d'ethernet em funciona correctament ?

Cal que faci [FONT="Courier New"]ifconfig[/FONT] ? 

Quines dades cal que faciliti?

Gràcies per l'ajut

---

### Post by papapep on 2007-10-11
Bé, amb ifconfig veuràs els dispositius de xarxa que tens i si tenen ip assignada.
A més,  a fi de veure si es veuen amb el router, pots fer a un terminal:

```
ping ip_del_router
```

Si et respon amb els paquets que envia i els temps que triguen, doncs la targeta et va bé. Si et posa alguna cosa que digui que els paquets no van enlloc, doncs alguna cosa falla.

A partir d'aquí, verificar que a /etc/hosts tens l'entrada:

```
127.0.0.1 localhost
```

Que a /etc/resolv.conf hi tens els servidors de DNS de la manera:

```

nameserver ip_del_servidor_de_DNS
nameserver ip_del_servidor_de_DNS
```

i que la comanda route (tal qual) et mostri la ruta a la teva passarela de sortida de xarxa (normalment, el router ADSL).

---

### Post by slink on 2007-10-11
Com puc saber la IP del router ?

---

### Post by papapep on 2007-10-11
....si no la saps assumeixo que no l'has configurat tu. A partir d'aquí, si ho ha fet el teu proveïdor d'ADSL, has de tenir documentació que t'ho digui. Si t'ho ha fet alguna altra persona, doncs li hauràs de preguntar.

Tot i això, normalment, el router és la ip acabada en 1 del rang de xarxa que es fa servir. O sigui, que si el teu pc té la 10.10.10.15, el router és molt probable que sigui 10.10.10.1.

---

### Post by slink on 2007-10-11
Mirant aquesta captura

[IMG]http://picasaweb.google.com/lh/photo/gQhw-K7iBrrrI1dPY8_89Q[/IMG]


es dedueix que la meva adreça ip és 169.254.9.22 ?

---

### Post by slink on 2007-10-11
ups!

[IMG]http://picasaweb.google.com/lh/photo/gQhw-K7iBrrrI1dPY8_89Q[/IMG]

---

### Post by slink on 2007-10-11
uff!

[http://picasaweb.google.com/lh/photo/gQhw-K7iBrrrI1dPY8_89Q](http://picasaweb.google.com/lh/photo/gQhw-K7iBrrrI1dPY8_89Q)

---

### Post by papapep on 2007-10-11
Les presses són males conselleres, eh! :-D

Doncs sembla que si, que aquesta és la teva ip. I, probablement, la obtindràs per DHCP. 
Prova a fer ping a 169.254.9.1,  a veure què surt.

I per properes vegades, no cal que facis tota la història d'un volcat de pantalla. Si copies el text del terminal i l'enganxes aquí aniràs molt més ràpid ;-)

---

### Post by slink on 2007-10-11
A veure...


```
felix@ordinador:~$ ping 169.254.9.1
PING 169.254.9.1 (169.254.9.1) 56(84) bytes of data.
From 169.254.9.22 icmp_seq=2 Destination Host Unreachable
From 169.254.9.22 icmp_seq=3 Destination Host Unreachable
From 169.254.9.22 icmp_seq=4 Destination Host Unreachable
From 169.254.9.22 icmp_seq=6 Destination Host Unreachable
From 169.254.9.22 icmp_seq=7 Destination Host Unreachable
From 169.254.9.22 icmp_seq=8 Destination Host Unreachable
From 169.254.9.22 icmp_seq=10 Destination Host Unreachable
From 169.254.9.22 icmp_seq=11 Destination Host Unreachable
From 169.254.9.22 icmp_seq=12 Destination Host Unreachable

--- 169.254.9.1 ping statistics ---
12 packets transmitted, 0 received, +9 errors, 100% packet loss, time 11000ms
, pipe 3


felix@ordinador:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 ordinador

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


felix@ordinador:~$ cat /etc/resolv.conf 
nameserver 62.42.230.24
nameserver 62.42.63.52


felix@ordinador:~$ route
Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
link-local      *               255.255.0.0     U     0      0        0 eth0
default         *               0.0.0.0         U     1000   0        0 eth0

```

---

### Post by papapep on 2007-10-11
Et falta route:

```
route
```

sense més, a veure què diu.

---

### Post by slink on 2007-10-11
Tens raó:

```
felix@ordinador:~$ route
Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
link-local      *               255.255.0.0     U     0      0        0 eth0
default         *               0.0.0.0         U     1000   0        0 eth0
```

---

### Post by patrickfromspain on 2007-10-11
Un apunt.. 169.254 te tota la pinta de ser una direccio erronea.. He vist molts casos que, amb el DHCP no activat, o funcionant malament, o amb una tarja de red que no va, la tarja de red agafa direccions del tipus 169.254..

---

### Post by slink on 2007-10-12
> 169.254 te tota la pinta de ser una direccio erronea..

He fet:

> [FONT="Courier New"]felix@ordinador:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0B:6A:F2:1D:FC  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xb400 

eth0:avah Link encap:Ethernet  HWaddr 00:0B:6A:F2:1D:FC  
          inet addr:169.254.9.22  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0xb400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:221 errors:0 dropped:0 overruns:0 frame:0
          TX packets:221 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18648 (18.2 KiB)  TX bytes:18648 (18.2 KiB)[/FONT]


I he deduït que la meva adreça IP és 169.254.9.22. Per aixó he fet ping a 169.254.9.1

Però pots tenir raó: el meu proveidor insinúa que un llamp durant la tempesta pot haver fregit la tarja d'Ethernet... o potser és el Modem el que, tot i amb les llums enceses, no conecta amb la CPU.

Necessito esbrinar si és la tarja de xarxa (ethernet) la que no funciona.

---

