---
title: "Problemes per configurar la pantalla en un Fujitusu Siemens Esprimo Mobile v5535"
date: 2010-05-12
forum: Catalan Team
---

### Post by giorgiograppa on 2010-05-12
Salutacions, companys.

Estic barallant-me amb el portàtil del departament, on vaig instal·lar fa uns dies la Lucid (versió Gnome).

M'ho ha detectat tot, tret de la targeta gràfica, una Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10), de tal manera que m'ofereix només un parell de resolucions molt baixes (800x600 i 640x480). La resolució màxima (que funciona en Güindous XP sense problemes; bé, GXP **és** el problema) seria de 1280x800.

He provat a instal·lar el controlador recomanat ([sisimedia]("http://www.richedmonds.co.uk/files/sis-671-drivers/xorg-driver-sisimedia_0.9-1_i386.deb")), però es queda igual.

He modificat el fitxer /etc/X11/xorg.conf, afegint les següent línies:

[INDENT][FONT="Courier New"]Section "Monitor"
HorizSync 28-72
VertRefresh 43-60
[/FONT][/INDENT]

tal i com diu [aquí]("http://ubuntuforums.org/showthread.php?t=870176"), i he aconseguit una resolució màxima de 1280x768, gairebé la màxima possible. Em preocupa, però, que em surt una freqüència de refresc de 0 MHz, i no sé si això pot fer malbé el monitor.

Algú s'hi ha trobat i sap com afinar una mica més la configuració?


Gràcies per l'atenció, companys.

PS: Com a últim recurs, he trobat [comentaris]("http://linuseria.es/2008/04/24/fujitsu-siemens-esprimo-mobile-el-dilema-de-linux/#comment-152") que afirmen que la Mandriva 2009 ONE ho reconeix tot a la primera, i potser l'acabaré provant, per si de cas.

---

### Post by papapep on 2010-05-12
T'has mirat això?

[http://estebanordano.com.ar/dual-monitors-setup-xorg-conf-para-la-tarjeta-sis-m672-en-linux-debian/](http://estebanordano.com.ar/dual-monitors-setup-xorg-conf-para-la-tarjeta-sis-m672-en-linux-debian/)

[http://estebanordano.com.ar/sis-m671m672-driver-for-xorg-xserver-7-5-on-debian-sidux/](http://estebanordano.com.ar/sis-m671m672-driver-for-xorg-xserver-7-5-on-debian-sidux/)

El més interessant que hi tens és un xorg.conf sencer per jugar: [http://estebanordano.com.ar/wp-content/uploads/2009/12/xorg.conf_.zip](http://estebanordano.com.ar/wp-content/uploads/2009/12/xorg.conf_.zip)

---

### Post by giorgiograppa on 2010-05-12
Gràcies, Papapep!

Demà m'ho miro amb calma; sembla interessant.

---

### Post by giorgiograppa on 2010-05-13
Ja està solucionat! Per millorar les probabilitats de trobar-ne el resum, he titulat aquesta entrada amb en nom de la targeta, i no amb el de la màquina, com havia fet en obrir el fil.


Després d'una bona googlejada (i d'una serie d'intents on el problema era sempre la impossibilitat de trobar el fitxer sisimedia_drv.so que, tanmateix, es trobava al lloc), ha resultat que el controlador sisimedia que estava emprant no funcionava. [Aquest article]("http://curitec.blogspot.com/2010/05/sis-671-e-ubuntu-1004-lucid-32bit.html") (en portuguès) ho explica molt clarament i en dóna una solució que funciona al cent per cent (tret dels efectes 3D, que continuen sense estar recollits pel nou controlador). Els passos que he seguit han estat els següents:

[LIST=1]
[*]he descarregat la versió alternativa del [controlador]("http://www.4shared.com/file/r_wcgeN9/x11-driver-video-sisimedia_091.html");
[*]he descarregat la versió nova del [xorg.conf]("http://www.4shared.com/file/1ZfAFd9Z/xorg.html");
[*]he eliminat la versió anterior del paquet: [FONT="Courier New"]sudo aptitude remove xorg-driver-sisimedia[/FONT];
[*]he instal·lat la nova versió del controlador: [FONT="Courier New"]sudo aptitude install xorg-driver-sisimedia[/FONT];
[*]he copiat el fitxer de configuració a [FONT="Courier New"]/etc/X11/xorg.conf[/FONT];
[*]he reiniciat el sistema;
[*]he triat la resolució correcta (ara sí!) des de Sistema / Preferències / Monitors, i
[*]he gaudit dels resultats!
[/LIST]

Recordo que quan vaig instal·lar la Jaunty en aquesta màquina, aquest tema també em va costar molt. Apa, ara, ja està.

---

### Post by narcisgarcia on 2010-12-15
Hola, també tinc dificultats amb els gràfics d'aquest mateix equip (Fujitsu-Siemens Esprimo mobile v5535), però amb la Ubuntu 10.10

**lshw -short**
> H/W path          Device      Class       Description
=====================================================
                              system      ESPRIMO Mobile V5535
/0                            bus         Z17M2.0
/0/1                          memory      100KiB BIOS
/0/4                          processor   Intel(R) Core(TM)2 Duo CPU     T5250  @ 1.50GHz
/0/4/5                        memory      16KiB L1 cache
/0/4/6                        memory      2MiB L2 cache
/0/4/0.1                      processor   Logical CPU
/0/4/0.2                      processor   Logical CPU
/0/7                          memory      2MiB L3 cache
/0/e                          memory      1GiB System Memory
/0/e/0                        memory      1GiB DIMM DRAM Synchronous
/0/e/1                        memory      DIMM DRAM [empty]
/0/2                          memory      1MiB BIOS
/0/3                          memory      1MiB BIOS
/0/5                          memory      1MiB BIOS
/0/6                          memory      1MiB BIOS
/0/8                          memory      1MiB BIOS
/0/9                          memory      1MiB BIOS
/0/a                          memory      895KiB BIOS
/0/0                          memory      895KiB BIOS
/0/2020                       memory      1023KiB BIOS
/0/b                          processor   
/0/b/0.1                      processor   Logical CPU
/0/b/0.2                      processor   Logical CPU
/0/100                        bridge      671MX
/0/100/1                      bridge      SiS AGP Port (virtual PCI-to-PCI bridge)
/0/100/1/0                    display     771/671 PCIE VGA Display Adapter
/0/100/2                      bridge      SiS968 [MuTIOL Media IO]
/0/100/2.5        scsi0       storage     5513 [IDE]
/0/100/2.5/0.0.0  /dev/cdrom  disk        DVDRAM GSA-T20N
/0/100/3                      bus         USB 1.1 Controller
/0/100/3.1                    bus         USB 1.1 Controller
/0/100/3.3                    bus         USB 2.0 Controller
/0/100/4          eth0        network     191 Gigabit Ethernet Adapter
/0/100/5          scsi2       storage     SATA Controller / IDE mode
/0/100/5/0.0.0    /dev/sda    disk        120GB WDC WD1200BEVS-2
/0/100/5/0.0.0/1  /dev/sda1   volume      1952MiB Linux swap volume
/0/100/5/0.0.0/2  /dev/sda2   volume      19GiB EXT4 volume
/0/100/5/0.0.0/3  /dev/sda3   volume      90GiB EXT4 volume
/0/100/6                      bridge      PCI-to-PCI bridge
/0/100/6/0        wlan0       network     AR5001 Wireless Network Adapter
/0/100/7                      bridge      PCI-to-PCI bridge
/0/100/f                      multimedia  Azalia Audio Controller
/0/100/1f                     bridge      PCI-to-PCI bridge
/0/c              scsi4       storage     
/0/c/0.0.0        /dev/sdb    disk        32GB SCSI Disk
/0/c/0.0.0/1      /dev/sdb1   volume      29GiB EXT3 volume
/1                            power       Lithium Ion Battery
/2                            system      

**lspci**
> 00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
00:1f.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

Primer de tot he optat per crear un fitxer "/etc/X11/xorg.conf" amb aquest contingut:
```
Section "Monitor"
    Identifier     "Monitor0"
    ModelName      "CRT-0"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "vesa"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

i amb això ja he obtingut la resolució correcta, tot i que sense acceleració gràfica. Un altre problema és que a la sortida de monitor extern (endoll VGA) en connectar-ho a un televisor queden els laterals de la imatge tallats.

**D'on surt el controlador "sisimedia" de 4shared? Alguna web oficial? Codi font?**

En aquesta pàgina algú explica que es pot convertir el paquet de sisimedia .rpm proveit per Mandriva, i aplicar una configuració genèrica a xorg.conf :
[http://curitec.blogspot.com/2010/05/sis-671-e-ubuntu-1004-lucid-32bit.html](http://curitec.blogspot.com/2010/05/sis-671-e-ubuntu-1004-lucid-32bit.html)
És el que provaré.

---

### Post by narcisgarcia on 2010-12-15
Ara he trobat una font de controladors empaquetats:
[http://ncc-1701a.homelinux.net/~linux-sis/index.php?page=Downloads](http://ncc-1701a.homelinux.net/~linux-sis/index.php?page=Downloads)

---

### Post by narcisgarcia on 2010-12-16
L'he instal·lat i no m'ha funcionat. He hagut de tornar a "vesa".

Al fitxer "Xorg.*.log" hi veig la fallada:
> /usr/lib/xorg/modules/drivers/sisimedia_drv.so: undefined symbol: resVgaIoShared

El problema que tinc amb Ubuntu 10.10 també és que sense fer ús de /etc/X11/xorg.conf , el sistema em sembla que carrega el controlador "sis" predeterminat, i de vegades mostra la resolució correcta i de vegades la limita a 800x600.
Allò dels 0Hz de refresc ho he vist amb diversos monitors i targes gràfiques, i em sembla que significa quelcom com "no especificat" perquè no passa res.

Per cert, els enllaços que va donar papapep ja no funcionen, i no he entès d'on heu tret el paquet sisimedia versió 0.9.1-2

---

### Post by narcisgarcia on 2010-12-16
Em sembla que anava errat: no s'utilitza "sis" de forma predeterminada sinó vesa. També he intentar especificar la resolució amb Modes "1280x800" a la SubSection "Display", però no me l'admet. Admet com a màxim 1280x768; vols dir que el Windows no estava equivocat?

També haig d'esbrinar com configurar el mode gràfic del segon monitor (endoll VGA), perquè en totes les proves es veu la imatge desplaçada i tallada en un televisor d'aquests panoràmics.

---

