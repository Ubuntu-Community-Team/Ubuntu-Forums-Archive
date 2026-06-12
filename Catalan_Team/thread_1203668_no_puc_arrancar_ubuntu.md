---
title: "no puc arrancar ubuntu"
date: 2009-07-03
forum: Catalan Team
---

### Post by anikuni_69 on 2009-07-03
Hola tinc un problema amb l'ubuntu: ahir va actualitzar el sistema, les actualitzacions automàtiques, i des d'aleshores va deixar d'identificar la targeta de so de l'ordinador.
A l'intentar solucionar aquest problema sincerament no sé dir-vos què vaig fer (no recordo haver fet cap cosa estranya) però el cas és que al reiniciar l'equip, en el moment que hauria de sortir la pantalla d'inici de sessió, surt una pantalla de color gris igual que una tele sense sintonitzar. Al cap d'una estona s'apaga l'ordinador. Puc entrar al mode recovery files, però no sé si hi puc fer alguna cosa o si encara m'ho carregaré més.

Sé que potser no dono prou informació, però no sé més. Si a algú li ha passat alguna cosa similar, sisplau necessito ajuda!


Gràcies

---

### Post by quitus on 2009-07-04
sembla que el que et passa es el que en diuen "les X petades" (no es cap peli porno)

Pots provar a escriure "dpkg-reconfigure xserver-xorg" en la línia d'ordres. També tens l'opció de recuperar un arxiu /etc/X11/xorg.conf antic (quan degut a una actualització es genera un arxiu xorg.conf es guarda l'antic en el mateix lloc però renombrat, segurament en deus tenir uns quants d'antics) 
     
salut

---

### Post by anikuni_69 on 2009-07-05
Gràcies quitus, reconfigurar el xserver-xorg ho vaig intentar però no va servir per res. He provat de fer això altre que has dit, escriure  /etc/X11/xorg.conf antic però em surt permís denegat, he provat d'escriure sudo al davant i em diu "command not found".
Què més puc fer?
A part, quan engega el recovery mode, no troba la targeta de so de l'ordinador.

---

### Post by papapep on 2009-07-05
> He provat de fer això altre que has dit, escriure /etc/X11/xorg.conf antic però em surt permís denegat, he provat d'escriure sudo al davant i em diu "command not found".

Si no ens poses **exactament** les ordres que has escrit, i el missatge exacte que t'ha donat (el millor és que copiis i enganxis aquí tot plegat, no que ho "repiquis") ens podem perdre pistes per poder-te ajudar.

---

### Post by anikuni_69 on 2009-07-05
Bé, l'ordinador se m'apagava cada dos per tres i no podia copiar res...
Tenia una partició lliure, i he tornat a instal·lar ubuntu en aquesta partició.
Ara puc accedir a ubuntu perfectament, el problema és el següent:
Des d'ubuntu puc accedir a la partició on hi ha windows sense problema. Puc visualitzar la partició on tenia instal·lat ubuntu i no funcionava, però no hi puc accedir perquè surt el següent error:

No es pot muntar el volum.
mount:wrong fs type, bad option, bad superblock on / dev/sda3, missing codepage or helper program, or other error  In some cases useful info is found in  syslog - try    dmesg | tail or so

A part d'això segueixo sense tenir so a ubuntu, però ara mateix és el que menys em preocupa... a la partició a la qual no puc accedir és on hi ha tots els documents. Alguna solució? Espero haver donat la informació correctamnet aquesta vegada.

---

### Post by oriolsbd on 2009-07-05
Hola,

pel missatge d'error, sembla que no li agrada el tipus de partició que li has indicat. Envia'ns la comanda completa que has escrit per a muntar-la.

Salut!

---

### Post by anikuni_69 on 2009-07-05
No sé si el que em preguntes és això, però per a intentar obrir la partició el que he fet és des del menú inicial: Llocs/Suport 107 GB (sobre d'aquerst hi ha el suport 88 Gb, on hi ha el windows i el puc obrir sense problemes). La partició és de format ext3, ja que és on vaig instal·lar ubuntu per primera vegada.
No sé si us estic donant la informaciuó correcta, perdoneu però és la primera vegada que escric en un foro d'informàtica i vaig perduda.

potser també us serveix això:

chiara@chiara-laptop:~$ sudo fdisk -l
[sudo] password for chiara: 

Disc /dev/sda: 250.0 GB, 250059350016 octets
255 heads, 63 sectors/track, 30401 cylinders
Units = cilindres of 16065 * 512 = 8225280 bytes
Disk identifier: 0xae50b7e1

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sda1   *           1       10697    85922628+   7  HPFS/NTFS
/dev/sda2           10698       12074    11060752+   7  HPFS/NTFS
[COLOR=Red]/dev/sda3           12075       25093   104575117+  83  Linux[/COLOR]
/dev/sda4           25094       30402    42639061   83  Linux
chiara@chiara-laptop:~$ 


La que està en vermell és la que no puc obrir. Pot ser simplement que la partició estigui malmesa? Aleshores hi hauria alguna manera de recuperar els arxius?

---

### Post by papapep on 2009-07-05
Anikuni, ara el tema del fil ja no és el del principi. Si no trobes una solució al teu nou problema al fòrum, hauries d'obrir un fil nou específic. Una de les regles del fòrum és: un tema, un fil :)

---

