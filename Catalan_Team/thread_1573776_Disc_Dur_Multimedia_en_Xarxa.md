---
title: "Disc Dur Multimedia en Xarxa"
date: 2010-09-13
forum: Catalan Team
---

### Post by tanreb20 on 2010-09-13
Hola!

Fa pocs dies hem canviat el router i ara els ordinadors amb W2 ja poden veure el disc dur multimedia que tenim en xarxa.

El problema és que jo desde l'Ubuntu no aconsegueixo veure'l, algu sap com ho hauria de fer?

Sé la IP que té, xq és fixe, posada per mi en el router.

---

### Post by akyra on 2010-09-14
Hola
Preguntes tontes, però tens instalat "samba" no?

Quan fas un ping a l'adreça del disc dur que et surt?
Tens el mateix Workgroup posat al disc dur i a l'ubuntu?

Ja diràs.

---

### Post by tanreb20 on 2010-09-14
```
ping 192.168.1.38
PING 192.168.1.38 (192.168.1.38) 56(84) bytes of data.
64 bytes from 192.168.1.38: icmp_seq=1 ttl=64 time=1.75 ms
64 bytes from 192.168.1.38: icmp_seq=2 ttl=64 time=1.62 ms
64 bytes from 192.168.1.38: icmp_seq=3 ttl=64 time=2.03 ms
^C
--- 192.168.1.38 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 1.620/1.803/2.036/0.176 ms

```

Juraria que el Disc Dur no té posat el WorkGroup, pero vaja els altres ordinadors poden veure el disc...

PD: Com s'afegeix el workgroup a ubuntu? :S

---

### Post by tanreb20 on 2010-09-14
Ara ja el veu!

Pero no m'hi deixa accedir em diu:

```
No s'ha pogut muntar l'ubicació.

No s'ha pogut recuperar la llista de compartits del servidor.
```

---

### Post by akyra on 2010-09-14
Perfecte,
El problema que tens és un problema que succeix força subint amb aquests discs (no tindràs un Storex?), a mí em pasa quan instal·lo de nou l'ubuntu o quan el disc s'ha quedat com penjat, al cap d'un parell de dies sense fer res ni a l'ubuntu ni al disc dur (només veure una peli) torna a trobar el disc. A mi la diferencia era que ja no em sortia el ping.
Sobre aquest problema es pot trobar uns quants links que a mi no m'han solucionat res, però si vols probar tu mateix, aquí et deixo un link.
[http://ubuntuforums.org/archive/index.php/t-1166093.html]("http://ubuntuforums.org/archive/index.php/t-1166093.html")

Normalment els ordinadors per windows tenen per defecte el grup de treball com a "WORKGROUP" o si esta en castellà com a "GRUPO_TRABAJO", podries mirar-ho per veure quin és el grup que tenen posat, i tu pasar el mateix a Ubuntu.

Per posar-ho a Ubuntu hauries d'editar l'arxiu de configuració de samba: (/etc/samba/smb.conf) i bucar la linea que posa:
workgroup = [COLOR="YellowGreen"]WORKGROUP[/COLOR]
i aquí cambiar-ho pel nom que tinguis del teu grup de treball.

També es pot anar a Sistema>Administracio>Xarxa i si no recordo malament està aquí (no tinc l'ordinador davant ara mateix).

Ja diràs que tal,
Adeu

---

### Post by tanreb20 on 2010-09-14
Val ja está, entrant a través del WORKGROUP ho aconsegueixo!

Ara ja només em queda trobar com conectar la impresora a la xarxa, que me vaig carregar el servidor d'impressio.... :(

---

### Post by akyra on 2010-09-15
La impressora depent una mica del model però també es pot fer, jo la tinc en xarxa i wifi per liarla més.
Jo vaig seguir les instruccions de Brother, i em varen anar molt bé.

Si ja va el disc dur multimedia, posa el "Solved"

Salutacions,

---

### Post by tanreb20 on 2010-09-15
Si el problema no és q la impressora no funcioni, es que em vaig carregar el Servidor D'impressio i n'he d trobar un barato.

---

### Post by marteljorge on 2010-09-15
No cal un servidor nou. Pots afegir funcionalitats a un altre servidor. Un que tinga Ubuntu o Debian aniria bé.

---

### Post by tanreb20 on 2010-09-16
per servidor d'impressio em refereixo a un petit aparell que es conecta, pero ara que ho dius... posar un pc senzill serviria no? Tot i que hauria d'estar sempre engegat...

---

### Post by SiscoGarcia on 2010-09-16
> **tanreb20 said:**
> per servidor d'impressio [...]

Si us plau, enceteu un nou fil per tractar un nou tema, això de la impressió no té res a veure amb cap disc dur multimèdia en xarxa :twisted:

Recordeu les [normes d'or del fòrum]("http://ubuntuforums.org/showthread.php?t=599965") ;)

---

