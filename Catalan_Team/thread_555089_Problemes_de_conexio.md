---
title: "Problemes de conexio"
date: 2007-09-19
forum: Catalan Team
---

### Post by blopnotdid on 2007-09-19
m'he comprat un pc nou (un core 2 quad) i li he posat l'ubuntu (versio amd64) mentre que al vell (pentium 4) li he instalat la versio de 32 bit.
Tot sembla funcionar, ara bé: mentre que el pentium 4 es conecta sense problemes a interne, en el nou em falla la conexio. detecta el cable RJ-45 però l'internet no funciona. Tant en l'ordinador nou com el vell la conexió RJ-45 la porta la placa base.
Tinc una conexió ADSL am router Thompson Speedtouch 530 V5
Algú em sabria dir com solucionar-ho?
Gràcies

---

### Post by papapep on 2007-09-20
Pots fer pings al router i a l'altre ordinador?
Pots fer pings a internet ([www.google.com](www.google.com), p. ex.)?
Pots fer pings a IP's externes (64.233.183.103, p. ex)?
Tens la xarxa configurada per DHCP o per IP fixa?
Has provat a intercanviar els cables ethernet entre els dos pc's?

Explica'ns més coses. :-)

---

### Post by blopnotdid on 2007-09-20
tinc DHCP i no es problema de cables. aixo del ping no ho he probat. com es fa?

---

### Post by papapep on 2007-09-20
Dius que no és problema de cables per que ho has verificat? o perquè no va per cable?
Per a fer ping, obres un terminal i poses, per exemple:

```
ping www.google.com
```

Per a provar que arribes bé fins el router:

```
ping ip_del_router
```

Al terminal veuràs si els paquets arriben correctament i quant temps triguen.
Si no funciona correctament ja veuràs que et diu 100% d'error.

---

### Post by blopnotdid on 2007-09-20
be abans de posar les respostes del ping, tambe he accedit amb el firefox a la ip del router i alla surt totes les dades. el pc vell i el portatil del meu pare (ell te windows vista) surt estado activo, mentre ke el nou posa inactivo, pero el detecta almenys.
les respostes del ping son:
al google:
Message from syslogd@pc-joan at (la data)
pc-joan kernel: [1070.312203] Oops: 0002 [5] SMP

Message from syslogd@pc-joan at (la data)
pc-joan kernel: [1070.312391] CR2: 0000000000003889

al router:
PING 192.168.1.254 (192.168.1.254) 56(84) bytes of data
64 bytes from 192.168.1.254: icmp_seq=1 ttl=64 time=0.500 ms

la 2a linia es va repetint constantment. la icmp:seq=1 a cada linia va pujan un numero (2, 3, 4, etc) i el time es variable sempre entre 0.400 i pico i 0.500 i pico)

---

### Post by CarlesOriol on 2007-09-20
Si ets nou en el mon gnu/linux i vols insta&#320;lar-lo com a pc d'escriptori et recomano que usis la versió de 32 bits. La de 64 no t'ajudarà gens, et farà perdre el temps les ganes i no et divertiras.

Si el que vols és muntar un servidor sql o de correu de web d'arxius o de groupware per una empresa o organització llavors el de 64 és la teva elecció.

---

### Post by blopnotdid on 2007-09-20
vaig probar dinstalar la versio de 32 bit pro es quedava penjat llavors vaig buscar a internet i vaig llegir a un forum que els core 2 duo i quad anaven amb la versio de 64 encara que posi amd64, pero aixo vaig instalar aquesta.
probare de tornar a posar la de 32 bit a veure si me l'instala, suposu que si va be ja es conectara, pq el pentiu 4 am la de 32 bit va de fabula.

gracies

---

### Post by papapep on 2007-09-20
He mogut la teva última pregunta a un fil nou, donat que era totalment diferent al tema inicial.

Aquí el trobaràs:
[http://ubuntuforums.org/showthread.php?t=555744](http://ubuntuforums.org/showthread.php?t=555744)

---

### Post by blopnotdid on 2007-09-20
be pro em referia si la solucio de la conexio pasava per tornar als 64 bits i continuar on estava o intentar fer funcionar els 32

---

