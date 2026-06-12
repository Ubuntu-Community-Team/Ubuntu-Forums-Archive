---
title: "ubuntu-mate: discos"
date: 2016-02-04
forum: Catalan Team
---

### Post by josep-maria on 2016-02-04
Tinc l'ubuntu-mate 15.10. No puc llegir cap disc CD. Quan hi fiques qualsevol disc, la disquetera fa voltes però no surt res a la pantalla. He provat a tres pc, tots amb l'ubuntu-mate, i amb processadors diferents, i passa igual a tots. Els discos estan bé, perquè els he provat a un altre pc que no té l'ubuntu. Cal configurar res?

---

### Post by wgarcia on 2016-02-05
Has mirat si al navegador de fitxers (el caja) es veu la unitat de CD?

---

### Post by josep-maria on 2016-02-05
Com es pot veure? Perquè he mirat a aplicacions > eines del sistema > caja, i em surt la meva carpeta d'usuari.

---

### Post by astarothvg on 2016-02-05
Bones a tothom, anem a pams, ens pots donar una mica més d'informació?, els discs que vols llegir que son, de dades, o àudio?. 
El "caja" és el navegador d'arxius del pc (l'ubuntu porta el nautilus) i a l'arbre de directoris que hi ha a la esquerra hi hauria de dir "ordinador" si cliques allà hi hauria de sortir la unitat de cd, si no hi surt malament.

---

### Post by josep-maria on 2016-02-06
Són de dades, ara mateix, un CD-RW.
He fet clic a llocs > computer, i hi ha una icona que es diu: HL-DT-ST DVDRAM GH22NS40, que suposo que és el lector de discos.
També es veu una altra icona que es diu ST3160815AS, i una altra que es diu "sistema de fitxers".

---

### Post by wgarcia on 2016-02-07
Quan cliques la icona que diu  HL-DT-ST DVDRAM GH22NS40 què passa?

---

### Post by josep-maria on 2016-02-09
No res.

---

### Post by wgarcia on 2016-02-10
Però s'obre i no mostra res, o no fa res?

---

### Post by josep-maria on 2016-02-10
No s'obre pas res. Ni cap finestra ni cap quadre, ni fa pampallugues. Com si no hi fessis clic.

---

### Post by wgarcia on 2016-02-10
Prova de fer el següent, a veure si el sistema està veient la unitat. Obre una terminal, posa algun CD a la unitat, entra l'ordre "dmesg" a la terminal (mostra els missatges del sistema), sortiran moltes línies, però enganxa les últimes 15 línies del que ha sortit.

---

### Post by josep-maria on 2016-02-10
Són aquestes:


[  529.477774] IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready
[  530.170349] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 330)
[  530.170362] ata1.01: SATA link down (SStatus 0 SControl 0)
[  530.194571] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20150619/psargs-359)
[  530.194576] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.CHN0.DRV0._GTF] (Node f2ca20d8), AE_NOT_FOUND (20150619/psparse-536)
[  530.299355] ata1.00: configured for UDMA/133
[  789.253144] sr 2:0:0:0: [sr0] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  789.253158] sr 2:0:0:0: [sr0] tag#0 Sense Key : Illegal Request [current] 
[  789.253161] sr 2:0:0:0: [sr0] tag#0 Add. Sense: Illegal mode for this track
[  789.253164] sr 2:0:0:0: [sr0] tag#0 CDB: Read(10) 28 00 00 02 a3 24 00 00 02 00
[  789.253167] blk_update_request: I/O error, dev sr0, sector 691344
[  789.289125] sr 2:0:0:0: [sr0] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  789.289139] sr 2:0:0:0: [sr0] tag#0 Sense Key : Illegal Request [current] 
[  789.289142] sr 2:0:0:0: [sr0] tag#0 Add. Sense: Illegal mode for this track
[  789.289144] sr 2:0:0:0: [sr0] tag#0 CDB: Read(10) 28 00 00 02 a3 24 00 00 02 00
[  789.289146] blk_update_request: I/O error, dev sr0, sector 691344
[  789.289149] Buffer I/O error on dev sr0, logical block 86418, async page read
pep@pep-System-Product-Name:~$ dmesg

---

### Post by wgarcia on 2016-02-10
A les línies finals es veu que el sistema no està muntant el CD correctament. Suposo que has provat amb diversos CD, no sempre amb el mateix. Quin tipus de CD són? Són de música? DVD?

---

### Post by josep-maria on 2016-02-11
He provat amb uns quants CD i amb alguns DVD, a quatre PC, tots amb l'ubuntu-mate.

---

### Post by wgarcia on 2016-02-14
És molt estrany, he mirat una mica per Internet i no he trobat altres usuaris que diguin que els falla allò, sent una cosa tan bàsica com muntar un CD, si estigués fallant estaria ple de comentaris al respecte. 

Pots mirar a una terminal quin nucli de Linux tens, amb l'ordre:

```
uname -a
```

---

### Post by josep-maria on 2016-02-14
Diu això:

pep@pep-System-Product-Name:~$ uname -a
Linux pep-System-Product-Name 4.2.0-27-generic #32-Ubuntu SMP Fri Jan 22 04:48:15 UTC 2016 i686 i686 i686 GNU/Linux

He mirat a: eines del sistema > monitor del sistema, i diu:
Nucli Linux 4.2.0-27-generic i686

---

### Post by wgarcia on 2016-02-15
És l'última versió del nucli a les versions estables d'Ubuntu, en principi no hauria d'haver-hi cap problema amb els CD/DVD. 

Has provat de posar un CD de música i intentar escoltar-lo amb alguna aplicació de música?, no sé quina porta l'Ubuntu Mate, a l'Ubuntu normal hi ha el "Videos", el Rhythmbox, i d'altres. Potser els discos no s'estiguin muntant, però tot i així les aplicacions per reproduir música i vídeos puguin accedir-hi.

---

### Post by josep-maria on 2016-02-17
Hi he ficat un disc de música i ha sonat bé. Només a un dels pc. Ara tornaré a provar als altres.

He provat el disc de música a un altre pc, i també ha funcionat bé.

---

### Post by wgarcia on 2016-02-18
Doncs sembla que el problema és que l'Ubuntu Mate no munta els CD/DVD automàticament, deu haver-hi algun paràmetre de configuració que faci que els CD/DVD es muntin automàticament. Per exemple a l'Ubuntu estàndard (Ubuntu Unity) està a Paràmetres de Sistema -> Maquinari -> Detalls -> Dispositius removibles.

---

### Post by josep-maria on 2016-02-18
El mate té un centre de control en comptes dels "paràmetres del sistema", però no hi diu res de discos hi de removibles.
He mirat i remirat tots els menús i no he pogut trobar res de semblant. Com puc saber on trobar-ho?

---

### Post by wgarcia on 2016-02-19
Pots provar això. Les instruccions següents són per donar en una terminal. Primer mira si tens dconf-editor instal·lat:

```
dpkg -l dconf-editor
```

Si surt una línia que comença amb "ii" i posa "dconf-editor", està instal·lat. Si en canvi surt amb "u" endavant:

```
sudo apt-get install dconf-editor
```

I un cop s'instal·li:

```
gsettings set org.mate.media-handling automount true
```

A veure si hi ha sort.

---

### Post by josep-maria on 2016-02-19
Ho he fet, i no ha fet res, tot i que hi ha la línia que comença per ii:

pep@pep-System-Product-Name:~$ dpkg -l dconf-editor
Desitjat=desconegUt/Insta&#320;la/supRimeix/Purga/retín(H)
| Estat=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Estat,Err: majúsc.=dolent)
||/ Nom            Versió       Arquitectura Descripció
+++-==============-============-============-=================================
ii  dconf-editor   3.16.1-1     i386         simple configuration storage syst
pep@pep-System-Product-Name:~$ 
pep@pep-System-Product-Name:~$ 
pep@pep-System-Product-Name:~$ gsettings set org.mate.media-handling automount true
pep@pep-System-Product-Name:~$ gsettings set org.mate.media-handling automount true
pep@pep-System-Product-Name:~$

---

### Post by wgarcia on 2016-02-19
Suposo que has reiniciat l'ordinador, oi?

---

### Post by josep-maria on 2016-02-19
Sí, l'he reengegat i ha tornat a sortir la mateixa línia:

pep@pep-System-Product-Name:~$ dpkg -l dconf-editor
Desitjat=desconegUt/Insta&#320;la/supRimeix/Purga/retín(H)
| Estat=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Estat,Err: majúsc.=dolent)
||/ Nom            Versió       Arquitectura Descripció
+++-==============-============-============-=================================
ii  dconf-editor   3.16.1-1     i386         simple configuration storage syst
pep@pep-System-Product-Name:~$ gsettings set org.mate.media-handling automount true
pep@pep-System-Product-Name:~$ gsettings set org.mate.media-handling automount true
pep@pep-System-Product-Name:~$

---

### Post by wgarcia on 2016-02-20
Prova d'obrir "dconf-editor", ho podrás fer des de la terminal entrant sols això, o de d'algun menú (possiblement estarà a "sistema"). 

Un cop obert veuràs que hi ha a l'esquerra una columna on podràs desplegar diverses opcions. Prova de desplegar org -> mate -> media-handling. 

Si pots fer una captura de pantalla del que surt un cop desplegat això potser podem veure si hi ha alguna opció que s'hauria de variar. En tot cas m'estranya que no tingui el Mate una configuració de sistema als menús per fer que s'automuntin els discos.

---

### Post by josep-maria on 2016-02-24
Surt això:

lloll@lloll-HP-Compaq-dc7800-Small-Form-Factor:~$ dconf-editor
** (dconf-editor:1506): WARNING **: dconf-schema.vala:330: Unknown property on <schema>, extends
** (dconf-editor:1506): WARNING **: dconf-schema.vala:330: Unknown property on <schema>, extends

Llavors surt una finestra de títol "editor del dconf". Que té una columna a l'esquerra que diu:

apps
ca
com
desktop
org
system

A la dreta hi ha un espai en blanc que té de títol "Nom  Valor".

Si faig clic a "org", no passa res. Com si no hi toquès. Ni fent-hi un clic ni fent-ne dos ni tocant la tecla intro.

---

### Post by wgarcia on 2016-02-25
No té com un trianglet al costat? Tipus "> Org". Si és així, clica sobre el trianglet.

---

### Post by josep-maria on 2016-02-26
Ja l'he trobat. Però no és a "mate" sinó a org > gnome > desktop.
[IMG]captura.png[/IMG]

He ficat la captura de pantalla però no ha sortit res. Torno a provar:

[IMG]http://blocs.tinet.cat/tokra/files/2016/02/Captura.png[/IMG]

---

### Post by wgarcia on 2016-02-26
Sota org no hi ha una entrada que diu "mate"? Sota l'entrada "desktop" del nivell superior, que hi ha?

---

### Post by josep-maria on 2016-02-27
A sota de org aí que hi ha un mate, però a sota de mate no hi ha cap media-handling.
El media-handling és a sota de org > gnome > desktop.

Aquí es veu el contingut de desktop, de org, de mate, i de media-handling:

[IMG]http://blocs.tinet.cat/tokra/files/2016/02/Captura1.png[/IMG]

---

### Post by wgarcia on 2016-02-29
Jo el veig sota org -> mate -> desktop -> media-handling, però en tot cas sembla com si tot estigués marcat correctament perquè els CD i DVD s'automuntin. 

Una altra cosa que es pot fer és mirar si el teu usuari està inclòs al grup "cdrom", per si un cas. Primer has de mirar si tens instal·lat l'eina de gestió de grups:

```
 sudo apt-get install gnome-system-tools
```

Després buscar als menús, segurament sota sistema, algun menú que digui "Usuaris i grups". Un cop obres l'eina, clica sobre el teu usuari, i mira una opció que diu "Gestiona els grups". Un cop s'obri la finestra dels grups busca un que es diu "cdrom", clica sobre "Propietats", i mira si el teu usuari està marcat a aquesta grup.

---

### Post by josep-maria on 2016-03-03
Perdoneu que hagi trigat tant, no he pogut fer-ho abans.
Aquí estan totes les pantalles. A mi em sembla que sí que està marcat l'usuari:


[IMG]http://blocs.tinet.cat/tokra/files/2016/03/Captura.png[/IMG]

---

### Post by wgarcia on 2016-03-04
Sí, el teu usuari està al grup "cdrom" i per tant aquesta no és la causa de què no es muntin els CD/DVD.

Pots provar l'ordre "wodim" per veure com veu el teu sistema a la unitat de CD/DVD. L'ordre és:

```
wodim --devices
```

Per cert, pots eliminar tots els nuclis antics que t'indica el teu sistema que ja no s'estan fent servir, amb:

```
sudo apt-get autoremove
```

---

### Post by josep-maria on 2016-03-05
Diu això:

pep@pep-System-Product-Name:~$ wodim --devices
wodim: Overview of accessible drives (1 found) :
-------------------------------------------------------------------------
 0  dev='/dev/sg1'	rwrw-- : 'HL-DT-ST' 'DVDRAM GH22NS40'
-------------------------------------------------------------------------
pep@pep-System-Product-Name:~$

I això és per l'autoremove:

pep@pep-System-Product-Name:~$ wodim --devices
wodim: Overview of accessible drives (1 found) :
-------------------------------------------------------------------------
 0  dev='/dev/sg1'	rwrw-- : 'HL-DT-ST' 'DVDRAM GH22NS40'
-------------------------------------------------------------------------
```
pep@pep-System-Product-Name:~$ sudo apt-get autoremove
[sudo] password for pep: 
S'està llegint la llista de paquets… Fet 
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat… Fet
Es SUPRIMIRAN els paquets següents:
  linux-headers-4.2.0-16 linux-headers-4.2.0-16-generic linux-headers-4.2.0-25
  linux-headers-4.2.0-25-generic linux-image-4.2.0-16-generic
  linux-image-4.2.0-25-generic linux-image-extra-4.2.0-16-generic
  linux-image-extra-4.2.0-25-generic
0 actualitzats, 0 nous a insta&#320;lar, 8 a suprimir i 17 no actualitzats.
Després d'aquesta operació s'alliberaran 469 MB d'espai en disc.
Voleu continuar? [S/n] s
(S'està llegint la base de dades… hi ha 266822 fitxers i directoris insta&#320;lats actualment.)
S'està desinsta&#320;lant linux-headers-4.2.0-16-generic (4.2.0-16.19)…
S'està desinsta&#320;lant linux-headers-4.2.0-16 (4.2.0-16.19)…
S'està desinsta&#320;lant linux-headers-4.2.0-25-generic (4.2.0-25.30)…
S'està desinsta&#320;lant linux-headers-4.2.0-25 (4.2.0-25.30)…
S'està desinsta&#320;lant linux-image-extra-4.2.0-16-generic (4.2.0-16.19)…
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.2.0-16-generic /boot/vmlinuz-4.2.0-16-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.2.0-16-generic /boot/vmlinuz-4.2.0-16-generic
update-initramfs: Generating /boot/initrd.img-4.2.0-16-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.2.0-16-generic /boot/vmlinuz-4.2.0-16-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.2.0-16-generic /boot/vmlinuz-4.2.0-16-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.2.0-16-generic /boot/vmlinuz-4.2.0-16-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.2.0-16-generic /boot/vmlinuz-4.2.0-16-generic
Generating grub configuration file ...
Avís: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
S'ha trobat una imatge de linux: /boot/vmlinuz-4.2.0-30-generic
s'ha trobat una imatge de initrd: /boot/initrd.img-4.2.0-30-generic
S'ha trobat una imatge de linux: /boot/vmlinuz-4.2.0-27-generic
s'ha trobat una imatge de initrd: /boot/initrd.img-4.2.0-27-generic
S'ha trobat una imatge de linux: /boot/vmlinuz-4.2.0-25-generic
s'ha trobat una imatge de initrd: /boot/initrd.img-4.2.0-25-generic
S'ha trobat una imatge de linux: /boot/vmlinuz-4.2.0-16-generic
s'ha trobat una imatge de initrd: /boot/initrd.img-4.2.0-16-generic
S'ha trobat una imatge de linux: /boot/vmlinuz-3.13.0-24-generic
s'ha trobat una imatge de initrd: /boot/initrd.img-3.13.0-24-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
fet
S'està desinsta&#320;lant linux-image-4.2.0-16-generic (4.2.0-16.19)…
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.2.0-16-generic /boot/vmlinuz-4.2.0-16-generic
update-initramfs: Deleting /boot/initrd.img-4.2.0-16-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.2.0-16-generic /boot/vmlinuz-4.2.0-16-generic
Generating grub configuration file ...
Avís: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
S'ha trobat una imatge de linux: /boot/vmlinuz-4.2.0-30-generic
s'ha trobat una imatge de initrd: /boot/initrd.img-4.2.0-30-generic
S'ha trobat una imatge de linux: /boot/vmlinuz-4.2.0-27-generic
s'ha trobat una imatge de initrd: /boot/initrd.img-4.2.0-27-generic
S'ha trobat una imatge de linux: /boot/vmlinuz-4.2.0-25-generic
s'ha trobat una imatge de initrd: /boot/initrd.img-4.2.0-25-generic
S'ha trobat una imatge de linux: /boot/vmlinuz-3.13.0-24-generic
s'ha trobat una imatge de initrd: /boot/initrd.img-3.13.0-24-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
fet
S'està desinsta&#320;lant linux-image-extra-4.2.0-25-generic (4.2.0-25.30)…
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.2.0-25-generic /boot/vmlinuz-4.2.0-25-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.2.0-25-generic /boot/vmlinuz-4.2.0-25-generic
update-initramfs: Generating /boot/initrd.img-4.2.0-25-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.2.0-25-generic /boot/vmlinuz-4.2.0-25-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.2.0-25-generic /boot/vmlinuz-4.2.0-25-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.2.0-25-generic /boot/vmlinuz-4.2.0-25-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.2.0-25-generic /boot/vmlinuz-4.2.0-25-generic
Generating grub configuration file ...
Avís: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
S'ha trobat una imatge de linux: /boot/vmlinuz-4.2.0-30-generic
s'ha trobat una imatge de initrd: /boot/initrd.img-4.2.0-30-generic
S'ha trobat una imatge de linux: /boot/vmlinuz-4.2.0-27-generic
s'ha trobat una imatge de initrd: /boot/initrd.img-4.2.0-27-generic
S'ha trobat una imatge de linux: /boot/vmlinuz-4.2.0-25-generic
s'ha trobat una imatge de initrd: /boot/initrd.img-4.2.0-25-generic
S'ha trobat una imatge de linux: /boot/vmlinuz-3.13.0-24-generic
s'ha trobat una imatge de initrd: /boot/initrd.img-3.13.0-24-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
fet
S'està desinsta&#320;lant linux-image-4.2.0-25-generic (4.2.0-25.30)…
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.2.0-25-generic /boot/vmlinuz-4.2.0-25-generic
update-initramfs: Deleting /boot/initrd.img-4.2.0-25-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.2.0-25-generic /boot/vmlinuz-4.2.0-25-generic
Generating grub configuration file ...
Avís: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
S'ha trobat una imatge de linux: /boot/vmlinuz-4.2.0-30-generic
s'ha trobat una imatge de initrd: /boot/initrd.img-4.2.0-30-generic
S'ha trobat una imatge de linux: /boot/vmlinuz-4.2.0-27-generic
s'ha trobat una imatge de initrd: /boot/initrd.img-4.2.0-27-generic
S'ha trobat una imatge de linux: /boot/vmlinuz-3.13.0-24-generic
s'ha trobat una imatge de initrd: /boot/initrd.img-3.13.0-24-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
fet
pep@pep-System-Product-Name:~$ ~
```

---

### Post by wgarcia on 2016-03-07
Doncs el "wodim" té està dient que el dispositiu associat amb el CD/DVD és "/dev/sg1", per tant pots muntar el disc "manualment", tot i que encara no entenc perquè no es munta automàticament, perquè d'acord amb els resultats anteriors sembla estar tot configurat correctament perquè els CD es muntin automàticament.

Per muntar-lo manualment, primer s'ha de crear una carpeta on es muntarà el dispositiu:

```
mkdir /media/cdrom 
```

Si et diu que aquest directori ja existeix, és perquè potser ja s'està muntant aquí el CD. En aquest cas salta el pas següent i navega amb Caja cap a aquesta carpeta.

En cas que es creï el directori, ara pots muntar el CD:

```
mount -t iso9660 /dev/sg1 /media/cdrom
```

I ara s'hauria de muntar, hauries de poder navegar amb el navegador de fitxers Caja a aquesta carpeta i veure els fitxers que tens al CD.

---

### Post by josep-maria on 2016-03-12
Diu això:

pep@pep-System-Product-Name:~$ mkdir /media/cdrom
mkdir: no s&#8217;ha pogut crear el directori «/media/cdrom»: S&#8217;ha denegat el permís


També he mirat a ordinador > sistema de fitxers > media. Hi ha una carpeta "pep" i una altra "user", però no n'hi ha cap "cdrom". L'he volgut crear però no m'ha deixat.

A més, he fet això:
pep@pep-System-Product-Name:~$ mount -t iso9660 /dev/sg1 /media/cdrom
mount: only root can use "--types" option
Però no m'ha deixat.

---

### Post by wgarcia on 2016-03-13
Encara em queda el dubte si no s'estan muntant els CD/DVD de dades a la carpeta "/media". Per tant paga la pena posar un CD o DVD de dades a la unitat, i després donar les instruccions següents:

```
ls /media
```

i 

```
ls /media/pep
```

a veure si apareix alguna cosa aquí.

---

### Post by josep-maria on 2016-03-15
Diu això:

lloll@lloll-HP-Compaq-dc7800-Small-Form-Factor:~$ ls /media
lloll

lloll@lloll-HP-Compaq-dc7800-Small-Form-Factor:~$ ls /media/lloll
lloll@lloll-HP-Compaq-dc7800-Small-Form-Factor:~$

---

### Post by wgarcia on 2016-03-15
Tenies un disc de dades ficat a la unitat, oi? 

És estrany perquè a un missatge anterior deies que es veia una carpeta amb nom "/media/pep" i ara no hi és. No sé si en aquell moment tenies endollat algun dispositiu USB o tenies algun disc de dades a la unitat de CD/DVD.

---

### Post by josep-maria on 2016-03-15
Sí que hi havia un disc cd ficat. 
El nom canviat de lloll és perquè ho he fet a un pc diferent del d'abans (el que es deia pep).
Demà tornaré a provar al pc que es diu pep.

Ja us deia que no llegeix els discos a cap dels quatre pc on hi he ficat el mate.

---

### Post by wgarcia on 2016-03-16
Sí que els llegeix, com mostra el fet que pugui reproduir els CD de música. El que passa és que no munta els discos automàticament, tot i que està configurat perquè ho faci.

Per muntar-los manualment:

1) Crea una carpeta on es muntarà:

```
sudo mkdir /mnt/cdrom
```

2) Munta el disc de dades a la carpeta que has creat:

```
sudo mount -t iso9660 /dev/sg1 /mnt/cdrom
```

Ara hauries de ser capaç de navegar des del navegador de fitxers (Caja) a aquesta carpeta i veure les teves dades.

---

### Post by josep-maria on 2016-03-16
Diu això:

pep@pep-System-Product-Name:~$ ls /media
pep  user
pep@pep-System-Product-Name:~$ ls /media/pep


pep@pep-System-Product-Name:~$ sudo mkdir /mnt/cdrom
[sudo] password for pep: 
pep@pep-System-Product-Name:~$ sudo mkdir /mnt/cdrom
mkdir: no s&#8217;ha pogut crear el directori «/mnt/cdrom»: El fitxer ja existeix
pep@pep-System-Product-Name:~$ sudo mount -t iso9660 /dev/sg1 /mnt/cdrom
mount: /dev/sg1 is write-protected, mounting read-only
mount:  /dev/sg1 is not a block device

---

### Post by wgarcia on 2016-03-17
Sembla que el disc està muntat a "/mnt/cdrom". Posa un disc de dades i mira què diu l'ordre:

```
ls /mnt/cdrom
```

---

### Post by wgarcia on 2016-03-17
Una altra cosa: després de l'ordre "sudo mount -t iso9660 /dev/sg1 /mnt/cdrom" és normal el missatge "mount: block device /dev/sg1 is write-protected, mounting read-only". Vas mirar si s'havia muntat?, és a dir, navegar a /mnt/cdrom amb el Caja o fer "ls /mnt/cdrom" des de la terminal?

---

### Post by josep-maria on 2016-03-17
Hi he ficat un disc de dades, 
he fet: ls /mnt/cdrom, al terminal, 
i contesta com si no hagués fet res:

pep@pep-System-Product-Name:~$ ls /mnt/cdrom
pep@pep-System-Product-Name:~$ 

He mirat a: ordinador > sistema de fitxers > cdrom, i no hi ha res a dins.

---

### Post by wgarcia on 2016-03-18
Has tornat a fer el que deia en el comentari #45 per muntar el disc un cop posat el CD?

---

### Post by josep-maria on 2016-03-19
Sí, i contesta això:

pep@pep-System-Product-Name:~$ sudo mkdir /mnt/cdrom
[sudo] password for pep: 
mkdir: no s&#8217;ha pogut crear el directori «/mnt/cdrom»: El fitxer ja existeix
pep@pep-System-Product-Name:~$ sudo mount -t iso9660 /dev/sg1 /mnt/cdrom
mount: /dev/sg1 is write-protected, mounting read-only
mount:  /dev/sg1 is not a block device
pep@pep-System-Product-Name:~$

---

### Post by wgarcia on 2016-03-20
Com deia, això és normal, els missatges que surten són els que han de sortir. Ara: si quan has fet tot això tenies un CD o DVD de dades a la unitat, i després de fer "ls /mnt/cdrom" continua sense mostrar res, llavors no està funcionant el muntatge del disc.

---

### Post by josep-maria on 2016-03-20
El mate és a quatre pc, i cap no admet discos. Vull dir que l'error és al sistema operatiu. Sembla que li ha de passar a molta més gent. Com ho podem saber?

---

### Post by wgarcia on 2016-03-23
Resumint el que s'ha esbrinat fins ara:

1) els teus sistemes sí que admeten els discos, perquè poden reproduir discos de música

2) els teus sistemes no estan "muntant" els discos. Muntar el disc vol dir que el sistema crea un punt d'accés (un punt de muntatge) de manera que el teu disc de dades es veu com una carpeta del sistema. Això és el que s'ha estat intentant fer "manualment", ja que el sistema no ho fa automàticament, però encara no ens hem sortit. 

Sobre el punt 2) sí que hi ha algunes referències si es fa una cerca a internet.

Una altra cosa que es pot provar és el següent. Posa un disc de dades a la unitat. Obre el programa "brasero", si et diu que no està instal·lat, instal·la'l. Mira si el disc de dades es veu des del programa "brasero". Aquest és un programa per gestionar discos de dades, és a dir crear-los, copiar-los, etc.

---

### Post by josep-maria on 2016-03-23
Hi he ficat un disc de dades, he obert el brasero i hi he ficat uns quants arxius per gravar-los.
Diu que l'està gravant, fins que arriba a una finestra que diu "s'està creant la suma de verificació de la imatge", llavors es queda així i ja no avança més. Si faig clic a "cancela", em diu que el disc s'ha gravat correctament, i l'expulsa.

He ficat el disc a un pc que té el windows. Puc veure els noms de les carpetes, però quan en vull veure el contingut, em diu que el disc està malmès.

---

### Post by wgarcia on 2016-03-24
I si és un disc ja gravat amb dades, el brasero pot veure el seu contingut?

---

### Post by josep-maria on 2016-03-24
Jo no l'he pogut veure.
He fet clic a brasero > projecte de dades, i l'espai per afegir arxius està en blanc.
He fet clic a brasero > projecte > obre, i veig la carpeta meva, la de baixades, de l'escriptori, etc. però no hi ha cap disc cd.

---

### Post by wgarcia on 2016-03-27
I si 1) poses un disc que tinguis gravat amb dades a la unitat, 2) obres el brasero i esculls "Copia un disc", a la finestra que s'obre, a sota de "Seleciona el disc a copiar", et diu "No hi ha cap disc disponible"?

---

### Post by josep-maria on 2016-03-30
Diu això:

[http://blocs.tinet.cat/tokra/files/2016/03/Captura1.png](http://blocs.tinet.cat/tokra/files/2016/03/Captura1.png)

---

### Post by wgarcia on 2016-03-30
D'acord, com veus el brasero està reconeixent perfectament que tens un disc de dades (amb 322.4 MB de dades) a la unitat. 

El problema que tenim és que no hem sigut capaços de muntar aquest disc perquè puguis accedir al disc des de l'escriptori, sense utilitzar aplicacions com brasero o semblants. És a dir que el disc es munti i puguis accedir com si fos una carpeta més del teu sistema. 

Per tant hauríem d'insistir per aquí. Torna a provar de

1) Tenir posat aquest disc de dades a la unitat

2) Fer:

```
sudo mount -t iso9660 /dev/sg1 /mnt/cdrom
```

3) Obrir el Caja, i intentar navegar a la carpeta "/mnt/cdrom", cosa que hauries de poder fer des de Ordinador -> mnt  -> cdrom. 

Si es veuen els fitxers del CD a aquesta carpeta, voldrà dir que el disc s'ha muntat.

---

### Post by josep-maria on 2016-03-30
Diu això:
pep@pep-System-Product-Name:~$ sudo mount -t iso9660 /dev/sg1 /mnt/cdrom
[sudo] password for pep: 
mount: /dev/sg1 is write-protected, mounting read-only
mount:  /dev/sg1 is not a block device
pep@pep-System-Product-Name:~$

Si entro a llocs > computer, veig una finestra de títol "ordinador", amb tres icones: DVDRAM, ST3160815AS, i "sistema de fitxers". No he vist "mnt".
Si faig doble clic a DVDRAM, em diu: "no s'ha pogut muntar la ubicació".

Hi he ficat un disc fet per un banc que té uns arxius pdf, en comptes del disc gravat per mi amb carpetes de textos.
Puc veure el contingut del disc sense fer clic enlloc, i també veig el contingut dels pdf.
Si fagi doble clic a llocs > computer > dvdram, ja no em diu "no s'ha pogut muntar", ara veig el mateix contingut del disc. 
Per què ara veig els pdf i no els meus arxius?

---

### Post by wgarcia on 2016-03-31
1) Per veure "mnt" a "ordinador", has de clicar sobre ordinador i t'hauria de sortir un llistat de carpetes a la finestra de la dreta, entre elles "mnt".

2) Bona notícia que puguis veure el segon CD, vol dir que no hi ha problema per al muntatge dels discos. Quant a que no puguis veure l'altre CD, potser és un problema del CD. No sé si tens oportunitat de provar-ho amb alguna altra versió d'Ubuntu o Linux. o algun altre sistema operatiu, per assegurar-te que està bé. En tot cas el "brasero" sembla veure'l.

---

### Post by josep-maria on 2016-03-31
He trobat la carpeta mnt a: sistema de fitxers > mnt
conté la carpeta cdrom, però la cdrom no hi té res a dins, malgrat que el disc està ficat.

He gravat un altre disc, que era verge, amb els meus arxius, però tampoc no l'he pogut llegir al meu pc.
L'he ficat a un altre pc que té el windows. Puc veure'n bé el contingut, però ha canviat algunes extensions del nom, per exemple als txt.

És a dir, que el disc està gairebé ben gravat, i que es pot veure amb un windows, però no amb el mate.
He ficat el disc a un altre pc que té el mate, i tampoc no funciona. A més, tampoc no hi ha la carpeta cdrom dins de la mnt.

---

### Post by wgarcia on 2016-04-01
Quan has mirat això del "mnt" has tornat a fer els passos per muntar el disc ("sudo mount etc. ")?

---

### Post by josep-maria on 2016-04-02
Sí, he fet "sudo mount -t iso9660 /dev/sg1 /mnt/cdrom", al segon pc.
No diu res, torna a sortir la línia d'ordres (:-$)
He mirat a sistema de fitxers > mnt, i està buit.

He escrit :-$, i ha sortit una emoticona.

Vegem ara:     -$

---

### Post by wgarcia on 2016-04-04
Per això de l'emoticona, per això està això de CODE i /CODE (envoltat per [ , ] ), perquè sinó l'editor del fòrum interpreta alguna combinació de caràcters. 

Tornant al tema del muntatge del discos, no sé ben bé com continuar. Sembla que 1) els discos de música els poden veure les aplicacions, i per tant el sistema els munta automàticament. 2) els discos de dades no els munta automàticament, i "manualment" no hem sigut capaços de muntar-los. Tot i així, programes com el brasero, els veuen. 

Hi ha un disc de dades que sí que s'ha muntat automàticament. 

No serà que hi ha algun problema per veure discos "RW", és a dir els reescrivibles? Perquè em sembla que aquest és el tipus de disc amb el qual has estat fent proves. Has provat amb diversos discos de dades o sempre amb el mateix (el "RW")?

---

### Post by josep-maria on 2016-04-04
Cal afegir-hi que sí que podia veure el disc dels pdf del banc.
He provat amb uns quants discos dels CD-R, i CD-RW.
Hi he ficat un DVD: el reproductor VLC s'engega, però no puc veure res del disc.

---

### Post by wgarcia on 2016-04-05
Bé, continuem. Prova si amb l'ordre entrada a una terminal:

```
eject
```

s'obre la unitat del CD.

Si s'obre, torna-la a tancar. I entra l'ordre següent:

```
udevadm monitor
```

ara inserta un dels discos que no es munta, copia els missatges que surten, i enganxa'ls aquí. Per acabar fes "Control C" a la terminal on has entrat l'última ordre.

---

### Post by josep-maria on 2016-04-06
pep@pep-System-Product-Name:~$ eject
s'ha obert

ara fico el disc i faig:
pep@pep-System-Product-Name:~$ udevadm monitor
monitor will print the received events for:
UDEV - the event which udev sends out after rule processing
KERNEL - the kernel uevent

KERNEL[869.297856] change   /devices/pci0000:00/0000:00:1f.5/ata3/host2/target2:0:0/2:0:0:0/block/sr0 (block)
UDEV  [879.629472] change   /devices/pci0000:00/0000:00:1f.5/ata3/host2/target2:0:0/2:0:0:0/block/sr0 (block)

---

### Post by wgarcia on 2016-04-07
Sembla tot correcte. Però al missatge #36, quan vam esbrinar quin dispositiu estava associat amb el cdrom, sortia "/dev/sg1", i ara està mostrant "/dev/sr0". Crec que això deu ser degut a que estàs fent proves a diversos ordinadors, hauries de fer-les sempre al mateix, sinó surten resultats diferents. 

En tot cas, sense canviar d'ordinador, ara mira si en aquest hi ha la carpeta "/mnt/cdrom", tot i que estigui buida, i si existeix, un cop has posat un disc de dades a la unitat, fes:

```
mount -t iso9660 /dev/sr0 /mnt/cdrom
```

---

### Post by josep-maria on 2016-04-08
És el mateix pc del comentari 36, perquè la línia d'ordres diu "pep@pep-System-Product-Name".
Vull dir que el nom d'usuari del pc és el mateix, "pep".

Diu això:
pep@pep-System-Product-Name:~$ mount -t iso9660 /dev/sr0 /mnt/cdrom
mount: only root can use "--types" option

---

### Post by wgarcia on 2016-04-08
Doncs és estrany perquè al #36 es veia un resultat diferent. A veure si funciona amb:

```
sudo mount -t iso9660 /dev/sr0 /mnt/cdrom
```

és a dir amb "sudo" endavant, perquè sembla que s'està queixant que no tens permisos d'administració a l'usuari normal.

---

### Post by josep-maria on 2016-04-09
Diu:

pep@pep-System-Product-Name:~$ sudo mount -t iso9660 /dev/sr0 /mnt/cdrom
[sudo] password for pep: 
mount: /dev/sr0 is write-protected, mounting read-only
pep@pep-System-Product-Name:~$

---

### Post by wgarcia on 2016-04-09
Es veu alguna cosa a la carpeta?

```
ls /mnt/cdrom
```

---

### Post by josep-maria on 2016-04-10
Si hi fico ls /mnt/cdrom, no fa res:

pep@pep-System-Product-Name:~$ ls /mnt/cdrom
pep@pep-System-Product-Name:~$ ls /mnt/cdrom
pep@pep-System-Product-Name:~$ ls /mnt/cdrom

Ara he fet sudo mount -t iso9660 /dev/sr0 /mnt/cdrom
Ha dit: mount: /dev/sr0 is write-protected, mounting read-only

Però si faig clic a llocs > computer > sistema de fitxers > mnt > cdrom,
ja surt la carpeta cdrom
i puc veure el contingut del disc

Però a "llocs" no veig cap disc dvd, i si faig llocs > computer > dvdram, diu que "no s'ha pogut muntar la ubicació"

---

### Post by wgarcia on 2016-04-11
Doncs ara es poden muntar els CD de dades, però no els DVD? És un DVD de dades també, o un DVD amb vídeo?

---

### Post by josep-maria on 2016-04-13
Volia dir:
Però a "llocs" no veig cap disc, i si faig llocs > computer > dvdram, diu que "no s'ha pogut muntar la ubicació" .

---

### Post by wgarcia on 2016-04-13
D'acord, però la meva pregunta era: Suposo que has posat un DVD a la unitat (sinó no hi ha res a muntar), aquest DVD que has posat, és un DVD on hi ha dades gravades o és un DVD de vídeo?

---

### Post by josep-maria on 2016-04-13
Hi he ficat un CD, de dades.

---

### Post by wgarcia on 2016-04-14
Això de llocs > computer > dvdram deu ser una altra casa, suposo que alguna cosa que pot muntar en la memòria Ram. 

Però ara almenys pots muntar les dades a /mnt/cdrom , oi?

---

### Post by josep-maria on 2016-04-14
Sí, però haig de fer això cada cop que engego el pc:

-hi fico un CD
-faig: sudo mount -t iso9660 /dev/sr0 /mnt/cdrom
-faig clic a: llocs > computer > sistema de fitxers > mnt > cdrom
i puc veure els arxius del disc

---

### Post by wgarcia on 2016-04-15
D'acord, ara que sabem que funciona es pot fer permanent. Tot i que s'ha de tocar un fitxer d'arrencada del sistema, i per tant queda tot sota la teva responsabilitat, com diuen els advertiments (vegeu [http://ubuntuforums.org/showthread.php?t=599965](http://ubuntuforums.org/showthread.php?t=599965)). En tot cas convé tindre a mà un USB o CD d'arrencada que sàpiques que funciona i que et permet entrar en el sistema en mode de prova arrencant des d'aquest mitjà, perquè des d'aquí es pot arreglar l'arrencada si s'espatlla amb aquest canvi que s'introduirà. En tot cas com sempre (i no sols per a aquestes coses) convé tenir una còpia de seguretat recent de les dades més importants que tinguis a l'ordinador, per poder recuperar-les si tot va malament.

La idea és doncs posar una línia en un fitxer d'arrencada que muntarà el disc per tu, així no ho has de fer cada cop que poses un CD. Per això s'ha d'editar el fitxer d'arrencada "fstab", cosa que és una mica perillosa perquè és el fitxer que li diu al sistema com es munten els discos, i si no pot muntar el disc del sistema, malament. Però no hauria de passar res, especialment si poses la línia addicional al final del fitxer, perquè tot i que t'equivoquis les línies inicials no es veuran afectades i el sistema arrencarà correctament. 

Per editar aquest fitxer, des d'una terminal 

```
sudo nano /etc/fstab
```

Amb la fletxa cap avall has d'anar al final del fitxer i escriure la línia següent:

```
/dev/sr0        /mnt/cdrom   iso9660 ro,user,noauto  0       0 
```

Després prova de reiniciar el sistema, posar un CD i mirar si es veuen els continguts a /mnt/cdrom.

Si tot funciona bé pots afegir una drecera a /mnt/cdrom a la barra esquerra del CAJA, perquè així sempre tindràs un accés directe.

Torno a recordar per si un cas que aquests canvis es fan sota la teva responsabilitat, per si vols provar de tenir una manera permanent de muntar els CD/DVD de dades.

---

### Post by josep-maria on 2016-04-17
He volgut fer el canvi que dius a un altre pc, per si de cas no anés bé, però no m'ha deixat. He fet això de:

-hi fico un CD
-faig: sudo mount -t iso9660 /dev/sr0 /mnt/cdrom
-faig clic a: llocs > computer > sistema de fitxers > mnt > cdrom

Suposo que cal ficar alguna ordre més abans, però ja no puc saber quina és. Potser era allò de sr0 o sg1?

Això que dius de l'accés directe, a la barra esquera, com es fa?

---

### Post by wgarcia on 2016-04-17
Sí, primer has d'esbrinar quin és el dispositiu associat amb el cd al sistema on el vols implementar. Una possibilitat és la comanda "wodim" que comentava al missatge #36. 

Quant a afegir la ubicació com a drecera directa al navegador de fitxers, no sé com es farà al Caja, però suposo que serà semblant al Nautilus. Un cop que navegues a la carpeta per la qual vols crear la drecera directa, a sota de la barra esquerra al Nautilus hi un "+" i si el cliques es crea una entrada a la barra esquerra que és una drecera a la carpeta en qüestió.

---

### Post by josep-maria on 2016-04-28
Perdoneu que hagi trigat a contestar, no he pogut fer res abans. He intentat fer-ho tot a un altre pc, per si de cas no anés bé. He fet:

Hi he ficat un disc de dades,

wodim -- devices   
em diu:  0  dev='/dev/sg1'	rwrw-- : 'ATAPI' 'DVD D  DH16D5S'

Llavors he fet:
sudo apt-get autoremove

I després:
sudo mount -t iso9660/dev/sg1/mnt/cdrom

He anat a llocs > computer > sistema de fitxers > mnt 
però no hi ha res, no hi ha cap carpeta cdrom

No goso fer el canvi a l'arxiu d'engegada al meu pc, per si de cas.

---

### Post by wgarcia on 2016-04-28
Això de " sudo apt-get autoremove" no cal, va ser una altra pregunta que vas fer en aquest fil.

Prova dues coses:

1) primer fer "sudo mkdir /mnt/cdrom" i després allò de "sudo mount..."

2) Si encara no funciona, prova amb:

```
sudo mount -t iso9660 /dev/sr0 /mnt/cdrom
```

potser el "wodim" estigui donant una informació incorrecta.

---

### Post by josep-maria on 2016-04-30
hi fico un disc de dades
faig:        sudo mkdir /mnt/cdrom

Ara ja veig la carpeta mnt/cdrom, però està buida

faig:         sudo mount -t iso9660/dev/sg1/mnt/cdrom
No res

i també:   sudo mount -t iso9660 /dev/sr0/mnt/cdrom
No res, segueix buida

---

### Post by wgarcia on 2016-05-01
En les comandes anteriors deixes un espai abans de "/mnt", oi? És a dir:

```
sudo mount -t iso9660/dev/sg1 /mnt/cdrom
```

per exemple.

---

### Post by josep-maria on 2016-05-07
Perdoneu el retard, no he pogut fer-ho abans.

Si ho faig sense l'espai, torna a sortir la línia d'esperar ordres, que acaba amb  :-$. La carpeta cdrom segueix buida.

Si hi fico l'espai, diu això:     can't find mnt/cdrom in /etc/fstab

que acaba amb : - $

---

### Post by wgarcia on 2016-05-09
Doncs resumint: els CD no es munten automàticament a Ubuntu MATE en tres ordinadors diferents. En un d'ells els pots muntar "manualment", però no als altres dos.  És així?

---

### Post by josep-maria on 2016-05-13
Hi ha quatre pc amb el mate que no llegeixen discos. Les darreres proves només les ha fet a dos dels pc. 
A un es pot muntar manualment i a l'altre, no. Al que sí que es munta, encara no he arribat a fer la solució permanent.

---

### Post by wgarcia on 2016-05-13
Al sistema que no et funciona, prova 
```
sudo mount -t iso9660 /dev/cdrom /mnt/cdrom
```

Per muntar un dvd seria:
```
sudo mount -t iso9660 /dev/dvd /mnt/dvd
```

després que hagis creat la carpeta "/mnt/dvd" amb 
```
sudo mkdir /mnt/dvd
```

Al meu sistema fins i tot es munten sense posar allò de "-t iso9660" (tampoc es munten automàticament però).

---

### Post by josep-maria on 2016-05-14
He fet "sudo mount -t iso9660 /dev/cdrom /mnt/cdrom"
contesta: mount /dev/sr0 is write-protected, mounting read-only

Si vaig a sistema de fitxers > mnt > cdrom: veig la carpeta on tinc tots els meus arxius (abans no hi era)
Però: si esborro la carpeta dels meus arxius que veig a cdrom, esborrarà també la carpeta original?
Vull dir: l'ha copiada o és la mateixa?

---

### Post by wgarcia on 2016-05-15
És la mateixa, però si són fitxers gravats en un CD ROM, no es podran esborrar. Però sembla que has pogut muntar el CD, oi?, que és el que s'estava buscant...

---

### Post by josep-maria on 2016-05-20
Perdoneu que hagi trigat a contestat. Em sap greu però tinc un embolic immens. Serà millor que em concentri a només el primer dels pc.
Si puc llegir els discos manualment, ja em conformo. Però no puc:

-hi fico un disc de dades
-faig wodim --devices:........................................................ diu dev='/dev/sg1'
-faig sudo mkdir /mnt/cdrom:...............................................diu que el fitxer ja existeix
-faig sudo mount -t iso9660/dev/sg1 /mnt/cdrom:..................diu mount: can't find /mnt/cdrom in /etc/fstab

Ara no funciona. Potser no he ficat bé les ordres.

---

### Post by wgarcia on 2016-05-20
Estàs deixant un espai entre iso9660 y /dev/sg1? 
```
sudo mount -t iso9660 /dev/sg1 /mnt/cdrom
```

---

### Post by josep-maria on 2016-05-20
Ja he ficat l'espai. Ara diu:
mount: /dev/sg1 is write-protected, mounting read-only
mount:  /dev/sg1 is not a block device

Però la carpeta cdrom segueix en blanc.

He provat fent:      sudo mount -t iso9660 /dev/sg1 /mnt/cdrom (amb espais després del zero i de l'u)
Ara he pogut veure el contingut de la carpeta cdrom. Però he canviat el disc i ja no funciona. 
Sembla que només es pot fer un cop. Ho tornaré a fer quan torni a engegar el pc.

Perdó, abans m'he confós copiant. He fet això:

sudo mount -t iso9660 /dev/cdrom /mnt/cdrom

cdrom. No sg1

He tornat a començar. De moment va bé. A dos dels pc he fet això:

-engego el pc
-hi fico un disc de dades
-sudo   mount   -t   iso9660   /dev/cdrom   /mnt/cdrom 
-llocs > computer > sist.fitxers > mnt > cdrom
-i ja puc veure el contingut del disc

Cal fer mount... cada cop que hi fiques un disc.
Cal anar molt amb compte amb els espais en blanc.

Sabent que haig de fer això de mount... ja em conformo. Potser algun dia s'arregli el mate amb alguna actualització.

Moltes gràcies.

M'ha esborrat els espais. Era:

-sudo    mount    -t    iso9660      /dev/cdrom      /mnt/cdrom

Caram, ho ha tornat a fer. Vegem ara:

-sudo .... mount ..... -t ..... iso9660 .....  /dev/cdrom ...... /mnt/cdrom

---

