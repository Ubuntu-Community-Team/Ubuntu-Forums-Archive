---
title: "No me troba el disc dur extraible"
date: 2007-10-23
forum: Catalan Team
---

### Post by nickpage on 2007-10-23
Hola companys,

he instal·lat el Gutsy fa poc amb una instal·lació neta, tinc un disc dur extraible el qual connecto amb USB. Aquest disc dur me'l trobava amb el Feisty, però amb el Gutsy no hi ha manera.

Sabeu d'alguna utilitat que pugui fer servir per a que el pugui connectar.

Gràcies

---

### Post by Kosimo on 2007-10-23
Has probat connectant-lo a un altre port USB diferent?

Si tot i així no te'l detecta, mira d'anar al directori arrel del filesystem 

/media/  a veure si pots veure'l allà.

---

### Post by nickpage on 2007-10-24
Avui matí me l'ha trobat, després d'anar canviant una i un altre vegada de port USB... sembla que ho fa quan li dona la gana, igual que el meu pendrive que he de endollar i desendollar varies vegades per a que funcioni. Realment aquestes coses fan que un es desesperi molt i molt.

---

### Post by jerec on 2007-10-24
Primer de tot hauries de fer uns dmesg o un tail -f /var/log/messages i endollar el  dispositiu a veure que et diu el registre de missatges.

Prova de reinstal·lar "hal"que no tingui algun problema.

---

### Post by CarlesOriol on 2007-10-24
i un lsusb per veure que hi ha connectat.

Però jo diria que el teu ordinador físicament no funciona bé i quan això passa qualsevol sistema del mon es torna boig i ho arregla tant bé com pot.

---

### Post by nickpage on 2007-10-25
Es possible que sigui algun tema de hardware, de tota manera ara que ho tinc connectat passo de desconnecta'l. Potser el que faré es canviar de cable usb, no sigui que sigui la causa de que no me'l trobi.

---

### Post by nickpage on 2007-11-14
Be, després de dos setmanes continuo amb el mateix problema,

si faig un tail -f /var/log/messages

i connecto el disc dur m'apareix el següent missatge

Nov 14 23:03:45 nicolas-desktop kernel: [  266.910259] usb 8-2: new high speed USB device using ehci_hcd and address 5

però no m'apareix cap icone a l'escritori ni res per a poder navegar.

Hi ha alguna manera de poder fer-ho... això me passa des de que he passat a Gutsy, amb el Feisty no tenia cap problema

---

### Post by papapep on 2007-11-14
I els altres discs durs si que els veus a l'escriptori?

Connecta el disc i enganxa el que mostra l'ordre:

```
ls -la /media
```

---

### Post by nickpage on 2007-11-15
Hola papapep,

doncs només tinc aquest disc dur USB, però me passa el mateix amb qualsevol llapis de memòria.

La instrucció que m'has comentat dona el següent, amb el disc connectat:

nicolas@nicolas-desktop:~$ ls -la /media
total 20
drwxr-xr-x  5 root root 4096 2007-11-14 22:59 .
drwxr-xr-x 21 root root 4096 2007-10-21 13:04 ..
lrwxrwxrwx  1 root root    6 2007-10-21 12:52 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2007-10-21 12:52 cdrom0
drwxr-xr-x  2 root root 4096 2007-10-21 12:52 cdrom1
lrwxrwxrwx  1 root root    7 2007-10-21 12:52 floppy -> floppy0
drwxr-xr-x  2 root root 4096 2007-10-21 12:52 floppy0
-rw-r--r--  1 root root    0 2007-11-14 22:59 .hal-mtab

---

### Post by nickpage on 2007-11-16
Intentaré donar més informació a veure si me pot ajudar algú:

Avui he portat aquest disc a la feina, on tinc un Windows XP, i m'ha funcionat perfecte. Està formatejat a FAT32.

Ara l'he tornat a provar a casa amb l'Ubuntu i no hi ha manera.

He agafat un altre disc dur i me l'agafa a la primera....

Alguna idea?

---

### Post by nickpage on 2007-11-17
Investigant per la web he vist que hi ha una aplicació que me podria solucionar el tema, que es diu disk manager, però sembla que per Gutsy no hi es.

Sabeu d'algun paquet o alguna forma per poder-ho instalar?. Gràcies

---

### Post by papapep on 2007-11-17
Quants lectors de dvd o cdrom tens? Per que veig que el lsusb et mostre cdrom i cdrom1. Si només en tens un és que t'interpreta el disc dur com a cdrom.  No seria el primer cop que ho veig.

---

### Post by nickpage on 2007-11-17
Tinc 2 lectors de DVD, un es gravador i l'altre no, per això surten dos.

---

