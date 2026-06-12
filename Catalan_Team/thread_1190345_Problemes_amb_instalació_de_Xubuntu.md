---
title: "Problemes amb instalació de Xubuntu"
date: 2009-06-17
forum: Catalan Team
---

### Post by Frealof on 2009-06-17
Hola!

Fa poc m'ha arribat a les mans un Pentium 3 a 800 MHz i 256 de Ram. La meva intenció es posar-hi xubuntu, així la pobra bèstia anirà més descansada.

El problema es que vaig cremar una iso en un CD, que amb el meu altre ordinador s'autoarrenca de meravalla, però amb el P3, no hi ha manera... He provat de fer un USB d'arrencada, mitjançant l'aplicació d'Ubuntu... però el P3 sembla que passi de l'USB...

A algú se li acud alguna cosa?

---

### Post by papapep on 2009-06-17
Jo provaria amb [la versió alternate]("http://se.archive.ubuntu.com/mirror/cdimage.ubuntu.com/xubuntu/releases/9.04/release/xubuntu-9.04-alternate-i386.iso") de Xubuntu, que és menys exigent a l'hora d'instal·lar.

---

### Post by Frealof on 2009-06-18
Bones!

Però les "alternate" no s'utilitzaven si ja hi tenies una versió anterior?

Bé, de fet en sabeu bastant més que jo sobre tot això... per tant d'acord, la descarrego, la cremo i ja us diré el què.

Salut!

---

### Post by kukat on 2009-06-18
El alternate s'utilitza per a insta&#320;lar lo més bàsic, i no arrenca un "livecd" així que gasta pocs recursos (de l'altra forma, arranca com si fos un livecd que es carrega en la RAM i pot ocasionar problemes). Resumit: la insta&#320;lació es fa en un entorn gràfic bàsic (com abans!;))


Jo vaig insta&#320;lar fa poc un Xubuntu (el Karmic Koala, que per cert, no m'ha donat cap problema per ara!), però vaig tindre després que insta&#320;lar el Fluxbox per que anava lent fins i tot amb Xcfe. 

Si veus que (una vegada insta&#320;lat el Xubuntu), va lent, pots provar amb Fluxbox insta&#320;lant-ho així:

sudo aptitude install fluxbox 

i Després, en la finestra de "login" (la d'usuari i contrasenya), fas clic a "Sessió", i canviese Xcfe per Fluxbox....i ja està! 

Salut!

---

### Post by Frealof on 2009-06-21
Bones!

Ja el tinc instal·lat!

De moment l'entorn gràfic em tira prou bé, per tant no canviaré al Fluxbox, de totes maneres ho tindré en compte, per si, en un futur necessito que la màquina rendeixi més.

Ara el problema que em trobo es que no em troba el disc dur esclau de 20 Gb. Alguna recomanació? He buscat per Internet i he trobat [això]("http://www.ubuntu-es.org/?q=node/97792") però dec fer algun pas malament perquè no me'n surto. En fi, si a algú se li acudeix alguna cosa serà benvinguda.

Salut!

---

### Post by papapep on 2009-06-21
Fes un

```
sudo fdisk -l
```

enganxa'ns el resultat, i explican's quins discs i quines particions tens a l'ordinador.

---

### Post by Miquel Ubuntero on 2009-06-22
Si serveix d'algo puc dir que entre Ubuntu i Xubuntu si vaig notar gran diferencia de velocitat en gestionar finestres. Entre Xubuntu i fluxbuntu no vaig notar gran diferèncie de velocitat, però si algunes mancances per par de fluxbuntu, com per exemple que no muntaba automàticament les claus usb. Finalment hem vaig decidir per Xubuntu.
Salut!

---

### Post by Frealof on 2009-06-22
Hola de nou!

He entrat a terminal i he escrit el què m'ha suggerit en Papapep. el resultat és el que veieu a sota.

Disc /dev/sda: 20.4 GB, 20404101120 octets
255 heads, 63 sectors/track, 2480 cylinders
Units = cilindres of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9bd59bd5

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sda1   *           1        2479    19912536    7  HPFS/NTFS

Disc /dev/sdb: 4311 MB, 4311982080 octets
255 heads, 63 sectors/track, 524 cylinders
Units = cilindres of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94119411

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sdb1               1         494     3968023+  83  Linux
/dev/sdb2             495         524      240975    5  Estesa
/dev/sdb5             495         524      240943+  82  Intercanvi Linux / Solaris

Bé, he vist que m'equivocava i enlloc de muntar /dev/sda1, muntava /dev/sdb1 (craso error). Ara ja puc muntar el disc dur mitjançant 
$sudo mount /dev/sda1 /media/secundari/

Sobre com ho tinc particionat tot... Bé, la intenció era tenir el sistema al disc dur petit (4Gb) i al disc dur esclau (el de 20Gb) tota la informació, bàsicament jocs, ja que voldríem fer servir aquesta màquina com a servidor per jugar en LAN (màxim 8 jugadors).

salut!


Edito:

Si us sembla bé dono el fil per tancat, ja que el tema d'instal·lació el considero resolt (tinc xubuntu a la màquina). En tot cas obriré un fil nou pel tema dels discs durs.

Edito 2:

Com es marca que un tema esta resolt? Abans anaves a Thread tools i ja sortia allà...

---

### Post by SiscoGarcia on 2009-06-23
> **Frealof said:**
> Com es marca que un tema esta resolt? Abans anaves a Thread tools i ja sortia allà...

Tu ho has dit... abans :(

Fa un temps que ho han tret i de moment no es pot marcar.

---

