---
title: "Recuparació i reinstal·lació"
date: 2010-02-09
forum: Catalan Team
---

### Post by pepitto on 2010-02-09
Bona tarda. Intentaré explicar-me, sóc nou per tant espero que em perdoneu per allargar-me...

Vaig canviar l'ordinador fa poc i vaig deixar el disc dur vell (de 160GB) com a auxiliar per portar les dades a la nova màquina on hi ha un disc de 320GB (no he tirat la casa per la finestra).

Al disc dur nou hi van quedar les següents particions:

- sdb1 de 30GB en NTFS pel sistema WinXP
- sdb2 de 70GB en NTFS per dades Win
- sdb3 de 30 GB en ext3 pel sistema d'ubuntu 9.04 (/.)
- sdb4 de 180GB en ext3 de partició estesa per dades i swap que va quedar:
- sdb5 de 1GB en memòria d'intercanvi per swap
- sdb6 de 180 GB per dades linux (/home)

El disc dur vell, com que s'arrossegava d'abans (tenia distema i /home a la mateixa partició) li van quedar particions de quan era disc dur principal i estava així:

- sda1 de 154GB en ext3 sense sistema (el vull només de suport)
- sda2 de 1GB de partició estesa per dades i swap que està:
- sda3 de 1GB en memòria d'intercanvi per swap

El nou sistema em funcionava de PM fins que per aquelles coses que passen es va esconyar el WinXP, el grub seguia bé i podia iniciar l'ubuntu, en un moment d'excessiu ímpetu des d'ubuntu vaig formatar amb el gpartd en format NTFS la partició de 30GB on tenia el sistema WinXP. Ara la cosa es va enredar i ja no arrencava res, suposo que em devia carregar la taula de particions del disc però vaig conseguir instal·lar-hi el WinXP, aquest però no reconeixia cap partició de la resta del disc (si que podia accedir al disc vell de 160GB). Des del LiveDC d'ubuntu tampoc no accedia a les particions (si al disc vell de 160GB). Amb el LiveCD d'ubuntu i el Testdisk (deepsearch) he refet el directori i quan arrencant des del LiveCD accedeixo a les antigues particions amb totes les dades amb la qual cosa he copiat al disc de 160GB totes les dades que volia conservar, ressenyo el que em surt amb fdisk -l:

---------------------------------------------------------------------------
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xca8a71d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19269   154778211   83  Linux
/dev/sda2           19270       19457     1510110    5  Extended
/dev/sda5           19270       19457     1510078+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f738f73

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sdb2            3825       12748    71682030    7  HPFS/NTFS
/dev/sdb3           12749       16395    29294527+  83  Linux
/dev/sdb4           16396       38913   180875835    f  W95 Ext'd (LBA)
/dev/sdb5           16396       16517      979933+  82  Linux swap / Solaris
/dev/sdb6           16518       38913   179895838+  83  Linux
------------------------------------------------------------------------------------

El cas és que quan utilitzo el disc d'instal·lació de WinXP no reconeix la partició que li tinc reservat al sistema (i que l'ubuntu troba) amb la qual cosa no sé com seguir, és clar que el fàcil és reformatar tot el disc de 320GB però em sembla que pot haver una millor solució fins i tot per no haver de reinstal·lar l'ubuntu.

Per cert com ho faig per eliminar la partició d'intercavi del disc vell on, crec, ja no hi pinta res?

Gràcies

---

### Post by kukat on 2010-02-09
Jo una vegada vaig tindre que llevar un dels dos discs durs per poder instal.lar el Windows.....

És així de babau el Sistema Operatiu. 

Crec que si lleves l'altre disc dur (el vell, el que et marca com a "/dev/sda") probablement ja pugues instal.lar-ho.

---

### Post by pepitto on 2010-02-10
Nova informació, he descobert que el que hem van vendre l'ordinata nou, que m'hi van instal·lar el disc dur de l'orinador vell (per una qüestió de preservar la garantia) me'ls van deixar els dos com a màsters! Visca la professionalitat. Ho canviaré i ja informaré de què passa.

---

### Post by papapep on 2010-02-10
> m'hi van instal·lar el disc dur de l'[COLOR="Red"]**orinador**[/COLOR] vell

Ostres tu, com avança la tècnica: orinadors computeritzats i amb disc dur...:D

(sí, ho sé, però no m'he pogut reprimir :oops:)

---

### Post by pepitto on 2010-02-11
Obriu pas a l'home ciberbiònic!

La màquina porta un processador Intel Pentium dual-core E5300 2.60 Hz amb 2GiB DIMM de RAM i una tarja gràfica ATI Radeon HD 4350
Tenia (i encara hi són però no s'engega) instal·lat l'XP SP3 i l'ubuntu 9.04 posat al dia.

He posat el disc petit com a esclau i des de la cònsola de recuperació del disc d'instal·lació de l'XP he fet el fixmbr però la cosa segueix sense rutllar no arrenca solet i si provo de instal·lar el sistema no em reconeix les dues particions NTFS que hi han fetes (instal·laria a la partició de 30GiB). Em fot perquè des del LiveCD de l'ubuntu, des que vaig reconstruir el directori del disc gran amb el testdisk, veig i accedeixo a totes les particions win i linux. Sé que només em falta un detall per poder tenir la màquina OK sense haver de reinstal·lar-ho tot! Ha de ser una qüestió del sector inicial del disc... He provat també fer fixboot a la cònsola de recuperació de l'XP però em diu que no troba res (evidentment) En fí...

Gràcies

---

### Post by pepitto on 2010-02-16
Tal com estaven les coses he usat un CD de SuperGrub (Per grub1) i torno a poder arrencar des del sistema que tenia al principi!!! Des d'aquest accedeixo a totes les particions Linux i Win. Amb la intenció de instal·lar de nou el WinXP he formatat amb el GParted la partició de 30 GiB a VFat32 per veure si el disc d'instal·lació em reconeix la partició on vull col·locar-lo però res! Quan arrenco des del disc d'instal·lació del WinXP només troba una partició de 131 GiB (?) i la resta és terreny desconegut per a ell, el mateix que m'indicava fins ara.

Agrairé suggeriments.

Master: potser hauria d'obrir un nou tema perquè ara el problema és només reinstal·lar el Win? S'ha tractat aquest tema en posts anteriors?

---

### Post by SiscoGarcia on 2010-02-17
> **pepitto said:**
> [...] potser hauria d'obrir un nou tema perquè ara el problema és només reinstal·lar el Win?

Això no cal ni que ho preguntis: 1 tema, 1 fil (per cert, el que hauries d'obrir és un nou fil, no un nou tema). D'altra banda, potser trobaràs llocs més adients que un fòrum d'ubuntu on sabran explicar-te com reinstal·ar el Win ;)

> **pepitto said:**
> S'ha tractat aquest tema en posts anteriors?

Per comprovar-ho només cal que vagis a l'arrel del fòrum en català i despleguis l'apartat "Search this forum", a la caixa que se t'obrirà posa-hi allò que vols saber (cal encertar les paraules) i sabràs si s'ha tractat prèviament o què.

---

### Post by pepitto on 2010-02-22
SOLUCIONAT:

L'estructura del disc es va recuperar amb el TestDisk però no podia arrencar des del disc tot i que des del LiveCD ho veia tot perfecte llavors... Màgia, vaig usar un disc d'arrencada del SuperGrub per restaurar el grub: PERFECTE. Ja apareixia el grub amb accés a la instal·lació d'ubuntu 9.04 que tenia anteriorment i que arrenca perfectament.

Per enllestir la història he fet un disc d'instal·lació de WinXP amb els drivers per discs SATA integrats (amb l'nlite) que ha reconegut perfectament les particions del disc i he instal·lat el sistema on li toca. Com que fent això he matxacat el grub he fet una nova sessió de SuperGrub que l'ha recuperat perfectament, només un problema: quan al grub selecciono l'arrencada de windows no troba el sistema, ho he solucionat editant el document menu.lst de la carpeta boot/grub i canviant el lloc on ha de trobar el windows de hd0,2 que hi posava a hd0,0 (després de diverses provatures...)

Ja tinc l'ordinador operatiu i sense perdre cap dada! I això que als serveis tècnics de Beep em van dir que no podien recuperar res. TestDisk i LiveCD d'ubuntu us estimoooo!

---

