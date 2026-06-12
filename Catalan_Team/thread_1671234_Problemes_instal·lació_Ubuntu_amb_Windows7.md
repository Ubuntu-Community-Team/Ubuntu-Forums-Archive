---
title: "Problemes instal·lació Ubuntu amb Windows7"
date: 2011-01-19
forum: Catalan Team
---

### Post by DrSaLaT on 2011-01-19
Bona nit a tothom, he tingut un problema amb l'ubuntu i suposo que algú me'l podrà resoldre fàcilment. 
Jo abans tenia el Windows Vista i em vaig instal·lar l'Ubuntu 9.10, de manera que a l'engegar el portàtil podia escollir entre el Vista i l'Ubuntu. No tenia cap problema, tot m'anava perfecte. Però ara m'he instal·lat el Windows7 en el lloc del Vista i resulta que ara l'Ubuntu no em funciona. Quan engego el portàtil tinc les dues opcions per escollir, i si trio Ubuntu m'apareix el següent: 

[COLOR=Red]Try (hd0,0): FAT32: No WUBILDR
Try (hd0,1): NTFS5: No wubildr
Try (hd0,2): Extended:
Try (hd0,3): invalid or null
Try (hd0,4): NTFS5: No wubildr
Try (hd0,5): Extended:
Try (hd0,6): EXT2:[/COLOR]

He provat de tornar a instal·lar Ubuntu 9.10 i també Ubuntu 10.04 LTS. Però quan creo el CD d'arrencada a l'últim moment em surt una finestreta amb el següent error: 

[COLOR=Red]Invalid argument
Per a obrenir-ne més informació, vegeu-ne el fitxer de registre: 
c:\users\nom\appdata\local\temp\wubi-10.04.1-rev190.log[/COLOR]

Què puc fer?

---

### Post by wgarcia on 2011-01-20
Si has instal·lat Windows 7 sobre Ubuntu el que ha passat és que el sistema operatiu de Microsoft sobreescriu l'arrencada del disc ignorant que pugui haver-hi altres sistemes operatius, a contrari de Linux que respecta que hi hagi altres sistemes operatius. 

Per recuperar-lo, s'ha de tornar a escriure el MBR (Master Boot Record) del disc amb el "Grub", que dóna el menú d'arrencada amb diverses opcions que et permet triar en començar. 

Però primer s'han de determinar algunes coses:

1) Tens Grub 2 o Grub legacy? El més probable és que tinguis Grub 2, i així serà el cas si has intal·lat l'Ubuntu després de la versió Jaunty, però si has anat actualitzant des de versions antigues és possible que encara tinguis Grub Legacy. Si no ho saps es pot mirar després.

2) On tens instal·lat l'Ubuntu? EL més probable és que sigui al dispostiu /dev/sda, però també s'ha de mirar primer abans de començar. Es pot mirar entrant al sistema amb un Live CD (t'has de baixar una imatge d'Ubuntu i cremar un CD per arrencar el sistema en mode live), obrir una terminal i entrar

sudo fdisk -l

Això et mostrarà els teus discos i es podrà veure en quin dispositiu (disc) està instal·lat i quines particions hi ha. 

A partir d'aquí, sabent aquestes dues coses, el procediment consistirà en entrar amb el Live CD, muntar la teva partició ubuntu, entrar com si fos aquest el teu sistema arrel, i córrer un programeta que reinstal·la el grub al lloc adequat. A partir d'aquí tornaràs a veure tant Ubuntu com els altres sistemes operatius. 

Però primer s'han d'esbrinar aquestes dues coses que et deia, i una cosa que em mosqueja és que surten coses referint "Wubi" en el que has mostrat, suposo que Ubuntu està totalment instal·lat i no s'està corrent des de Wubi, oi?

---

### Post by DrSaLaT on 2011-01-22
He aconseguit obrir amb Ubuntu, no m'ha fet falta crear un cd perquè crec que m'ha instal·lat Ubuntu en una part d'un dels discos durs. Suposo que servirà igual... Lo del grub no sé quin tinc. El cas és que he fet ***$ sudo fdisk -l  *** i m'ha donat:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0ab90a2c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         893     7168000   1c  Hidden W95 FAT32 (LBA)
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         893        8190    58609664    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3            8190       14593    51438561    f  W95 Ext'd (LBA)
/dev/sda5            8190       11425    25984558    7  HPFS/NTFS
/dev/sda6           11426       14456    24346476   83  Linux
/dev/sda7           14457       14593     1100421   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x09ce95f3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    c  W95 FAT32 (LBA)

---

### Post by wgarcia on 2011-01-22
Ara m'has confós, dius que ara sí pots entrar a Ubuntu, i segons el que surt amb l'instrucció "fdisk -l" sols tens una partició amb Ubuntu. Llavors ja estaria solucionat, oi? O és que tenies dades en una altra instal·lació d'Ubuntu i ja no les veus?

---

### Post by DrSaLaT on 2011-01-22
No ho tenia solucionat, però ara ja sí!
He anat a [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) he seguit els passos i ara ja he pogut accedir a l'ubuntu antic que tenia! En aquesta pàgina s'entén força i m'ha anat bé. 

Ja he aconseguit el que volia... però ara m'han quedat alguns dubtes. Quan he fet 
  	 	 	 	p { margin-bottom: 0.21cm; }  [COLOR=Red]**root@ubuntu:/home/sala# ls /media/9037f5dc-e2ad-44bc-b0f1-ce0f1abeced0/boot  **[/COLOR]
 M'ha retornat:



[COLOR=Blue]abi-2.6.31-14-generic     config-2.6.31-16-generic      initrd.img-2.6.31-17-generic  System.map-2.6.31-19-generic  vmcoreinfo-2.6.31-21-generic  [/COLOR]
 [COLOR=Blue]abi-2.6.31-15-generic     config-2.6.31-17-generic      initrd.img-2.6.31-19-generic  System.map-2.6.31-20-generic  vmcoreinfo-2.6.31-22-generic  [/COLOR]
 [COLOR=Blue]abi-2.6.31-16-generic     config-2.6.31-19-generic      initrd.img-2.6.31-20-generic  System.map-2.6.31-21-generic  vmlinuz-2.6.31-14-generic  [/COLOR]
 [COLOR=Blue]abi-2.6.31-17-generic     config-2.6.31-20-generic      initrd.img-2.6.31-21-generic  System.map-2.6.31-22-generic  vmlinuz-2.6.31-15-generic  [/COLOR]
 [COLOR=Blue]abi-2.6.31-19-generic     config-2.6.31-21-generic      initrd.img-2.6.31-22-generic  vmcoreinfo-2.6.31-14-generic  vmlinuz-2.6.31-16-generic  [/COLOR]
 [COLOR=Blue]abi-2.6.31-20-generic     config-2.6.31-22-generic      memtest86+.bin                vmcoreinfo-2.6.31-15-generic  vmlinuz-2.6.31-17-generic  [/COLOR]
 [COLOR=Blue]abi-2.6.31-21-generic     grub                          System.map-2.6.31-14-generic  vmcoreinfo-2.6.31-16-generic  vmlinuz-2.6.31-19-generic  [/COLOR]
 [COLOR=Blue]abi-2.6.31-22-generic     initrd.img-2.6.31-14-generic  System.map-2.6.31-15-generic  vmcoreinfo-2.6.31-17-generic  vmlinuz-2.6.31-20-generic  [/COLOR]
 [COLOR=Blue]config-2.6.31-14-generic  initrd.img-2.6.31-15-generic  System.map-2.6.31-16-generic  vmcoreinfo-2.6.31-19-generic  vmlinuz-2.6.31-21-generic  [/COLOR]
 [COLOR=Blue]config-2.6.31-15-generic  initrd.img-2.6.31-16-generic  System.map-2.6.31-17-generic  vmcoreinfo-2.6.31-20-generic  vmlinuz-2.6.31-22-generic  [/COLOR]
 

I quan inicio l'ubuntu també em dóna diferens opcions a triar amb el mateix nom que aquests que surten aquí. Però això ja ho tenia abans. No sembla gaire normal no?

---

### Post by wgarcia on 2011-01-22
No entenc del tot la pregunta, però aquests són els nuclis de linux que es poden arrencar des del grub, és a dir els nuclis que tens instal·lat al teu sistema.

---

### Post by DrSaLaT on 2011-01-22
És normal tenir tants nuclis d'arrencada?? Per a què serveix tenir-ne tants?

---

### Post by wgarcia on 2011-01-22
Quan es van actualitzant els nuclis, si no desinstal·les els anteriors encara hi són. És recomanable en el meu parer mantenir almenys un nucli anterior a l'última actualització, potser dos, però els altres es poden desinstal·lar des del Gestor de paquets Synaptic (buscant per "linux"). 

Quan s'actualitza a una nova versió també s'eliminen. Tens una versió que ha sortit ja fa un temps i s'han produït moltes actualitzacions de nucli, és per això que tens tants.

---

### Post by DrSaLaT on 2011-01-26
Ara resulta que quan he borrat l'ubuntu que havia creat ja no puc accedir a l'ubuntu antic que tenia. 
No vaig poder carregar l'ubuntu amb un live cd i vaig instalar un ubuntu  a un dels discs durs que tinc. Al reiniciar ja podia accedir a aquest  nou ubuntu i vaig fer les modificacions que em van permetre accedir a  l'antic. Tenia 3 opcions: win7, ubuntu(antic) i ubuntu(nou). Podia obrir tan l'antic com el nou  ubuntu. Ara he borrat el nou perquè ja no el necessitava per res i he perdut l'accés a l'antic...

---

### Post by wgarcia on 2011-01-27
És possible que s'hagi esborrat el programa d'arrencada grub, o hagi quedat desconfigurat, quan vas eliminar aquest instal·lació d'ubuntu que menciones. 

Deies en una intervenció anterior que no havies pogut entrar amb el Live CD. Suposo que ara no tens cap instal·lació d'Ubuntu operativa, oi? Per tant necessitaràs un Live CD per fer les comprovacions i reparacions si fa falta. 

Per tant el primer és entrar amb un Live CD, o també es pot fer amb una memòria USB si el teu ordinador pot arrencar des d'aquest tipus de dispositius, mira-ho si pots al menú de BIOS que pots obrir en arrencar l'ordinador, dins d'aquest menú deu haver-hi una opció per configurar l'ordre d'arrencada dels dispositius, i es necessita que l'arrencada des del CD i des de l'USB estiguin abans del disc dur. 

Un cop entris amb el LIVE CD obre una terminal i entra la instrucció:

sudo fdisk -l

Això ens mostrarà com han quedat les particions del disc un cop eliminada la instal·lació d'Ubuntu que menciones.

---

