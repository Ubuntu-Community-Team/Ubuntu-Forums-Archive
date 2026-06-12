---
title: "Problemes navegació"
date: 2007-05-19
forum: Catalan Team
---

### Post by Miquel Ubuntero on 2007-05-19
Hola a tots.
El problema que ara comento, també l'he comentat anteriorment a la llista de correu, per si algú li sona.
Els navegadors d'internet s'hem tancan sobtadament, Firefox, Konqueror, Epiphany, ect.
Abans amb Ubuntu 6.06 navegaba be, ara amb ubuntu 7.04 fatal :(
Amb sessió Live CD puc navegar perfectament, lo qual hem diu que el servidor internet tira be i en principi el hardware be.
Abans també ocasionalment es tencaba synaptic, però ara ja no, després de haber fet
des de terminal: sudo apt-get -f intall, sudo aptitude update, sudo aptitude dist-upgrade.

Hi ha algú que li passi també?
Gracies.

---

### Post by lluisanunez on 2007-05-20
Curiós! A mi m'ha estat passant darrerament, amb les DUES instal·lacions d'Ubuntu 6.10

He passat a Feisty Fawn aquest matí, i de moment no se m'ha penjat cap navegador, ni una vegada! 
:confused:

PS: el que vaig fer quan se'm penjava és instal·lar un altre navegador: Opera, Seamonkey

---

### Post by Miquel Ubuntero on 2007-05-20
Be, no soc l'unic!
Dons amb Opera també hem falla. Si tinc temps, provaré amb un altre HD i ja explicaré com va.
Pero con m'emprenyi gaire hem torno a Ubuntu 6.06 que anava perfecte :)

---

### Post by lluisanunez on 2007-05-20
Una manera de saber què està passant és engegar el navegador des del terminal, així es veu el missatge que envia quan es penja (jo no vaig pensar a fer-ho perquè se'm penjava totalment random)

---

### Post by Miquel Ubuntero on 2007-05-20
Ok. Ja he fet correr firefox des de terminal. 
Aquest es el missatge desprès de tancar-se de cop: Segmentation fault (core dumped)

LLàstima que no ho entenc??

Un colega m'ha comentat que pot ser tinc un problema amb la memo swap, que pot ser no està activada. Amb terminal he fet "free -m" i hem diu:


             total       used       free     shared    buffers     cached
Mem:           757        688         69          0         20        489
-/+ buffers/cache:        178        579
Swap:            0          0          0

Algú ho sap interpretar?
Moltes gracies.

---

### Post by lluisanunez on 2007-05-20
Bé, no és que en sàpiga gaire però ho diu ben clar: de swap no en tens ni mica!

---

### Post by Ferri on 2007-05-21
Sembla que no tens partició swap o el teu sistema no te la detecta.
Potser ho podries arreglar amb el gparted.

---

### Post by lluisanunez on 2007-05-21
Pots arrencar des del CD d'instal·lació, i fer servir el gparted per afegir una partició SWAP, més o menys el doble de la RAM que tens

---

### Post by orestesmas on 2007-05-21
Efectivament, no tens swap. No sé si aquest és l'origen del problema, però en qualsevol cas s'ha d'arreglar.

Abans d'això, el problema també pot ser del plugin de flash. Et peta aleatòriament o només quan entres en una pàgina que usa flash?

Per arreglar el swap s'ha d'usar l'ordre "swapon". Probablement en instal·lar ja et va crear una partició de swap, però ara la tens desactivada per algun motiu.

1) mira't el fitxer /etc/fstab i busca una línia que tingui la paraula "swap". Aquella línia correspon a la partició de swap creada durant la instal·lació, si és que es va crear.

2) Mira d'activar-la:
sudo swapon -a -v  (això activa totes les particions de swap definides a /etc/fstab)

3) Comprova que la sortida no sigui cap missatge d'error

4) Prova altra vegada els navegadors.

---

### Post by CarlesOriol on 2007-05-22
Una altra cosa que pots provar és reanomenar la carpeta /home/elteunom/.mozilla a /home/elteunom/.mozilla_vell per regenerar la configuració del navegador i veure si el problema et ve per aquí.

---

### Post by Miquel Ubuntero on 2007-05-23
hola de nou.
Be, cert era que la mem swap no era activa. Amb Gparted aquest matí l'he activat i tot a funcionat be. Ara he engegat de nou el pc i amb un "free -m" he vist que novament estaba desactivada.
Amb Gparted he activat de nou la swap.
Sembla que al reiniciar s'hem desactiva la mem swap. Algú sap com solucionar-ho?
Gracies a tots pel vostre suport:)

---

### Post by orestesmas on 2007-05-23
Per casualitat el PC és portàtil? i per casualitat també no estaràs hivernant enlloc d'apagar-lo? hi havia un bug conegut respecte la hivernació, que en certs casos es carregava la swap...

---

### Post by Miquel Ubuntero on 2007-05-23
Tal com ha comentat orestesmas he fet de de terminal: sudo swapon - a -v i el resultat a estat        
aquest:
swapon en /dev/disk/by-uuid/e751c6eb-9ea8-4591-8db2-9949e71e05e3
swapon: cannot stat /dev/disk/by-uuid/e751c6eb-9ea8-4591-8db2-9949e71e05e3: No such file or directory

A les hores, amb Gparted, he vist que la swap estava inactiva. De fet, no se perque, pero tenia 2 memorias swap. Les he esborrat i he creat una, el doble de ram. Tot i deixar-la activa, en reiniciar pc està inactiva de nou.
Com podria fer perque no "es desactivi sola"?
Moltes gracies.

P.D. Evidentment, amb la swap activa, el rendiment del pc millora notablement.

---

### Post by Miquel Ubuntero on 2007-05-23
Ep, abans no he vist les preguntes de orestesmas; no, no es portatil i tampoc hiberno mai.

---

### Post by orestesmas on 2007-05-23
> **Miquel Ubuntero said:**
> Ep, abans no he vist les preguntes de orestesmas; no, no es portatil i tampoc hiberno mai.

Aleshores no veig què pot passar. Per si et serveix de guia, el "bug" de la hivernació que comentava abans anava més o menys així: La partició de swap no és una partició buida, sinó que té una certa estructura (podríem dir-ne format) que la identifica. Quan s'hiverna el pc, el contingut de la RAM es salva a la partició de swap, carregant-se aquesta estructura. Això és normal i està dissenyat així. Quan el PC reinicia, mira si el contingut de la swap és un bolcat de memòria i, si és així, el carrega i restaura el format de la swap.

El bug era que el pc que arrencava després d'una hivernació no restaurava el format de la swap, i quan el sistema pretenia activar-la es trobava amb una partició de swap amb format desconegut, i en aquest cas no usa la partició de swap per no carregar-se dades potencialment útils.

No sé si et serà útil, això...

---

### Post by Miquel Ubuntero on 2007-05-23
Be, el tema va per aquí. 
Al iniciar-se el pc, no activa la swap. Provablement pel que tu dius o altres motius.
Segons he vist a la guia de ubuntu-es cal editar l'arxiu /etc/fstab afegin unes ordres. Ho he fet però no m'ha funcionat. Poso aquí el meu arxiu fstab per si algú pot veure on està l'error pel qual no activa la swap al iniciar. De moment per anar tirant, l'activo cada cop que engego pc amb gparted.
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc1 -- converted during upgrade to edgy
UUID=f835e763-5731-4be9-87ef-d530fbb94235 / ext3 defaults,errors=remount-ro 0 1
/swap/swap none swap sw 0 0

/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

Gracies.

---

### Post by orestesmas on 2007-05-23
Això de /swap/swap em sona molt malament. Algun merder deus tenir amb les particions.

Si et plau, quin és el resultat de les ordres següents?:

cat /proc/partitions
ls -l /dev/disk/by-uuid

Quina partició és la que realment tu estàs destinant a swap?

---

### Post by Miquel Ubuntero on 2007-05-25
Aquí poso l'ultima petició de orestesmas:

miquel@miquel-desktop:~$ cat /proc/partitions
major minor  #blocks  name

  22     0   39082680 hdc
  22     1   21792141 hdc1
  22     3   14996677 hdc3
  22     5    2289231 hdc5
 254     0   21792141 dm-0
 254     1   14996677 dm-1
 254     2    2289231 dm-2

miquel@miquel-desktop:~$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2007-05-26 01:12 4e6bf533-9282-43d8-920d-558cc8191d86 -> ../../hdc5
lrwxrwxrwx 1 root root 10 2007-05-26 01:12 9b4cb1cb-f285-4d96-919b-b2edd36d8656 -> ../../hdc3
lrwxrwxrwx 1 root root 17 2007-05-26 01:11 f835e763-5731-4be9-87ef-d530fbb94235 -> ../../mapper/hdc1

---

### Post by Miquel Ubuntero on 2007-05-25
He oblidat de dir hdc5 es la swap.

Encara que la activi, en reiniciar pc es desactiva.

Gracies.

---

### Post by Miquel Ubuntero on 2007-05-26
Hola companys.
Avui he instal.lat 1 HD nou amb Ubuntu 7.04
En intentar usar Synaptic he tingut 1 error "http has died unexpectedly" i més tard s'ha penjat amb firefox. No se si al meu pc no li agrada Feisty Fawn? (faig broma)
Be, he formatat de nou i m'he instal.lat Dapper Drake; de moment tira be, navego i ja he instal.lat algunes coses amb Synaptic.
Moltes gracies a tots els que meu ajudat. De moment ja estic content amb ubuntu 6.06 :)
Salut

---

