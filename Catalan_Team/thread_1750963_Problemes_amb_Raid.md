---
title: "Problemes amb Raid"
date: 2011-05-06
forum: Catalan Team
---

### Post by saturno200 on 2011-05-06
Tenia instal·lat a l’Ubuntu Server 10.04 un Raid 1 que m’anava bastant be, el problema es l’Ubuntu arrancava des de un Pen Drive i no m’agradaba.
  La qüestió es que vaig voler començar de zero i instal·lar l’Ubuntu 11 i no vaig tindre la precaució de desendollar els discos raid.
  Ara he tornat al Ubuntu Server 10.10 i el problema es que ara no puc muntar el raid dons no se que li ha fet que mels ha posat com a discos d’arrencada i al muntar-lo hem surt això:
   
  **root@P5K:/home# mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sdc1 missing**
  **mdadm: /dev/sdc1 appears to contain an ext2fs file system**
  **    size=976760000K  mtime=Tue May  3 17:54:06 2011**
  **mdadm: Note: this array has metadata at the start and**
  **    may not be suitable as a boot device.  If you plan to**
  **    store '/boot' on this device please ensure that**
  **    your boot-loader understands md/v1.x metadata, or use**
  **    --metadata=0.90**
   
  Si segueixo els discos hem queden en blanc com si no tinguessin informació i tinc que recuperar-los amb el GParted.
  No se si una solució es esborrar el MBR, perquè no li veig un altre.

---

### Post by wgarcia on 2011-05-06
Penso que fent un "grub-install" donant com a opció el disc on vols posar l'arrencada al MBR, et deixarà establir l'arrencada que tenies. Per exemple grub-install /dev/sda si aquest fos el disc on s'ha d'instal·lar el grub.

---

### Post by saturno200 on 2011-05-06
[FONT=Calibri]Hem sembla que no me he explicat.[/FONT]
  [FONT=Calibri]Jo ja tinc un disc (10Gb) amb el qual tinc l’Ubuntu 10.10.[/FONT]
  [FONT=Calibri]El problema son els dos discos que faig servir de Raid-1 (de 1Tb) i que a l’hora de muntar el raid hem dona aquest error.[/FONT]

---

### Post by kimet on 2011-05-06
```
root@P5K:/home# mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sdc1 
``` Aquí no falta un disc?, si li indiques devices=2, hi d'haver dos dispositius.
Has provat a passar-li el paràmetre --metadata=0.90?
 ```
#mdadm --create /dev/md0 --level=1 --raid-devices=2 --metadata=0.90 /dev/sdc1 /dev/sde1

```

---

### Post by wgarcia on 2011-05-06
Jo suggeria el tema de reinstal·lar el grub perquè segons expliques al principi sembla que el s'ha instal·lat en algun dels discos que tens al RAID, o això em sembla entendre.

---

### Post by saturno200 on 2011-05-07
Primera: he reinstal·lat Grub i com si res.
  Segona: he posat el –metadata i ja no hem surt l’error.
  Però segueixo igual, ara puc muntar el raid però un cop acabat el GParted diu que el raid no esta formatat i es veu buit.
  Si miro l’estat hem diu:
   
  [COLOR=Red]root@P5K:/home/# mdadm --detail /dev/md65[/COLOR]
  [COLOR=Red]/dev/md65:[/COLOR]
  [COLOR=Red]        Version : 0.90[/COLOR]
  [COLOR=Red]  Creation Time : Sat May  7 13:57:52 2011[/COLOR]
  [COLOR=Red]     Raid Level : raid1[/COLOR]
  [COLOR=Red]     Array Size : 976759936 (931.51 GiB 1000.20 GB)[/COLOR]
  [COLOR=Red]  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)[/COLOR]
  [COLOR=Red]   Raid Devices : 2[/COLOR]
  [COLOR=Red]  Total Devices : 2[/COLOR]
  [COLOR=Red]Preferred Minor : 65[/COLOR]
  [COLOR=Red]    Persistence : Superblock is persistent[/COLOR]
  [COLOR=Red] [/COLOR]
  [COLOR=Red]    Update Time : Sat May  7 13:58:25 2011[/COLOR]
  [COLOR=Red]          State : active, resyncing[/COLOR]
  [COLOR=Red] Active Devices : 2[/COLOR]
  [COLOR=Red]Working Devices : 2[/COLOR]
  [COLOR=Red] Failed Devices : 0[/COLOR]
  [COLOR=Red]  Spare Devices : 0[/COLOR]
  [COLOR=Red] [/COLOR]
  [COLOR=Red] Rebuild Status : 0% complete[/COLOR]
  [COLOR=Red] [/COLOR]
  [COLOR=Red]           UUID : 7fd99ec2:cfd0dd4e:782d8831:5d458ab1 (local to host P5K)[/COLOR]
  [COLOR=Red]         Events : 0.2[/COLOR]
  [COLOR=Red] [/COLOR]
  [COLOR=Red]    Number   Major   Minor   RaidDevice State[/COLOR]
  [COLOR=Red]       0       8       33        0      active sync   /dev/sdc1[/COLOR]
  [COLOR=Red]       1       8       49        1      active sync   /dev/sdd1[/COLOR]
   
  I un cop que faig reinici diu que no esta muntat i hem genera un altre raid que també esta buit i no funciona.

---

### Post by kimet on 2011-05-07
Es que el procediment habitual es formatar el raid després de crearlo. En el teu cas els discs ja tindrien format md. Has provat a afegir els discs amb **--add**?, I si no, fes una ullada al manual sobre **--zero superblock**. (No en tinc experiencia).

---

### Post by saturno200 on 2011-05-08
De moment tiro la tovallola dons mo m’en surto.
  Ara l’arrencada hem surt que tinc els superblocks malament i li he de passar el **fsck** i ni hem això o arreglo sempre queda el raid buit sense formatar.
  Deixaré passar un temps i ja buscaré un altre solució.
  Gracies.

---

### Post by wgarcia on 2011-05-08
Per si vols provar un parell de cosetes més, i si pot ser d'utilitat que no ho sé.

No sé si et funcionarà amb els discos del RAID, però hi ha un programeta que dóna moltíssima informació sobre com tens els discos i les arrencades:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Si vols forçar un fsck del disc principal en arrencar per si ha quedat amb blocs malament, si pots entrar al sistema i fas 

sudo touch /forcefsck

et forçarà la verificació del disc d'arrencada al pròxim reinici.

---

### Post by saturno200 on 2011-05-09
Ja el tinc solucionat.
No ho volia fer, peró al final ha tingut que eser aixi.
He recolocat tota l'informació que tenia hon he pogut i he particionat els dos dicos de nou.
Es el sistema infalible perque funcioni.
Gracies de totes maneres.

---

