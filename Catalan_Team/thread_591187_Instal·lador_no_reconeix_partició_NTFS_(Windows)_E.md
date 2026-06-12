---
title: "Instal·lador no reconeix partició NTFS (Windows) Era:Partir... o no partir..."
date: 2007-10-25
forum: Catalan Team
---

### Post by slink on 2007-10-25
Hola, 

necessito una mica d'ajut. Estic intentant instal.lar el Gutsy en un disc en que ja hi ha el XP i no m'el vull cargar... (si, si, ja ho se... ja ho se...). Provo el LiveCD, tot be. Començo a instalar i llavors:

[imatge1]("http://bp1.blogger.com/_80ytoCMo2uc/RyCzbXkGJDI/AAAAAAAACtc/ohHUiRB0a6g/s1600-h/1prepara.jpg")

i després:

[imatge2]("http://bp0.blogger.com/_80ytoCMo2uc/RyCz3HkGJEI/AAAAAAAACtk/mhayCrxQG0g/s1600-h/2guiat_no.jpg")

Sembla que el métode guiat no reconeixi el XP, no?

Doncs provo el mètode manual i em trobo:

[imatge3]("http://bp3.blogger.com/_80ytoCMo2uc/RyC073kGJHI/AAAAAAAACt8/SiG1OQENjd8/s1600-h/4manual.jpg")

He de continuar creant una taula de particions?

O el partidor hauria d'haver detectat ja que hi ha un altra sistema operatiu i actuar en consequència per no matxacar-lo?

Com veieu, estic una mica peix en tema particions. He fet [FONT="Courier New"]sudo gparted[/FONT] desde el LiveCD però no veig les particions. 


Qué em recomaneu que faci?

---

### Post by papapep on 2007-10-25
És molt important posar títols als fils que indiquin de què van, sinó la feina que es fa no és accessible als que venen darreral, i un dels objectius importants dels fòrums se'n va en orris.
T'afegeixo al títol una mica de descripció del problema.

---

### Post by jodufi on 2007-10-26
Pots enviar una captura amb el gnome parted?

Hi tens instal·lades més coses al disc dur, a part del Windows XP?

---

### Post by slink on 2007-10-26
> Pots enviar una captura amb el gnome parted?

Com que amb el gparted no apareixía res, no el vaig capturar.Dilluns ho faré.


> Hi tens instal·lades més coses al disc dur, a part del Windows XP?

Hi tinc el XP i el Feisty en una partició. Hi puc accedir desde el LiveCD sense problemes ja que apareixen com disk i disk-1 al costat del filesystem a LLOCS, però sembla com si l'instal.lador no els reconegui :confused:


El que em proposo és instal.lar el Gutsy sobre el Feisty o en l'espai lliure. Dilluns penjo captures.

---

### Post by slink on 2007-10-29
Aquesta és una captura del gparted:

[GPARTED.JPG]("http://bp3.blogger.com/_80ytoCMo2uc/RyXx1nkGJKI/AAAAAAAACvA/RJeKB01bCd4/s1600-h/gp1.jpg")

i aquesta és una captura de la partició XP a llocs:

[XP.JPG]("http://bp2.blogger.com/_80ytoCMo2uc/RyXx6XkGJLI/AAAAAAAACvI/b-pjlDQ479c/s1600-h/xp.jpg")

I aixó és lo que em diu el fdisk i el fstab:

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdc97dc97

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5943    47737116    7  HPFS/NTFS
/dev/hda2            5944        9779    30812670   83  Linux
/dev/hda3            9780        9964     1486012+   5  Extended
/dev/hda4            9873        9964      738958+  82  Linux swap / Solaris
/dev/hda5            9780        9872      746959+  82  Linux swap / Solaris



ubuntu@ubuntu:~$ sudo cat /etc/fstab 
unionfs   /    unionfs rw           0 0
tmpfs     /tmp tmpfs   nosuid,nodev 0 0
/dev/hda4 swap swap    defaults     0 0
/dev/hda5 swap swap    defaults     0 0
```


Entenc que les particions hi són, però l'instal.lador no les reconeix. Hauré d'usar l'alternate-cd ?

---

### Post by slink on 2007-10-29
```
ubuntu@ubuntu:~$ sudo parted
GNU Parted 1.7.1
Using /dev/hda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print                                                            
Error: Can't have overlapping partitions.                                 
(parted) quit                                                             
Information: Don't forget to update /etc/fstab, if necessary.             




ubuntu@ubuntu:~$ sudo gparted
======================
libparted : 1.7.1
======================
Can't have overlapping partitions.
Unable to open /dev/hdc read-write (Read-only file system).  /dev/hdc has been opened read-only.
Unable to open /dev/hdc - unrecognised disk label.
Can't have overlapping partitions.
Unable to open /dev/hdc read-write (Read-only file system).  /dev/hdc has been opened read-only.
Unable to open /dev/hdc - unrecognised disk label.

glibmm-ERROR **: 
unhandled exception (type std::exception) in signal handler:
what: basic_string::_S_create

aborting...
Aborted (core dumped)
```

---

### Post by slink on 2007-10-30
Em sembla que el problema està a la taula de particions, que és un merder. Vaig a borrarles totes menys l'XP a veure qué passa...

---

### Post by Ferri on 2007-10-30
En [aquest fil]("http://ubuntuforums.org/showthread.php?t=413745&highlight=overlapping+partitions") expliquen un problema igual o molt semblant al teu i sembla que fent servir el [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") se'ls arregla. Ho he mirat, i pots instal·lar el TestDisk tan a Windows com a Linux (i està a les fonts de programari d'Ubuntu).

---

### Post by slink on 2007-10-30
[RESOLT]


L'instal.lador no te cap problema.

El problema era que jo tenia un desgavell de particions que ni el parted entenia. Ho he arreglat amb el fdisk.

[FONT="Courier New"]   Device Boot      Start         End      Blocks   Id  System
/dev/hda1       *           1        5943    47737116    7  HPFS/NTFS
/dev/hda2            5944        9779    30812670   83  Linux
/dev/hda3            9780        9964     1486012+   5  Extended
/dev/hda4            9873        9964      738958+  82  Linux swap / Solaris
/dev/hda5            9780        9872      746959+  82  Linux swap / Solaris[/FONT]

Gràcies per l'ajut. Ja sóc usuari de Gutsy!\\:D/

---

### Post by Ferri on 2007-10-30
Una pregunta i una recomanació:
[INDENT]Perquè t'has fet dues particions d'intercanvi?
En lloc d'una sola partició linux, considero molt recomanable fer-ne almenys dues, una muntada com partició arrel (punt de muntatge /) i l'altra com a home. Per a la primera amb dos gigas n'hi ha de sobres i la resta ho deixes per a la home.[/INDENT]
Fer una partició /home separada et permet instal·lar tot el sistema linux tants cops com vulguis sense perdre els teus documents, fitxers de configuració i, fins i tot, preferéncies de l'escriptori.

---

### Post by slink on 2007-10-31
> Perquè t'has fet dues particions d'intercanvi?
No, aquest era l'esquema dolent, hi havia particions juxtaposades. La culpa és que vaig re-instal.lar l'XP després del Ubuntu i vaig re-re-instal.lar l'Ubuntu... un follón. A partir d'aquí vaig agafar el fdisk i vaig netejar-ho tot, [[COLOR="Blue"]és molt fàcil[/COLOR]]("http://www.cyberciti.biz/faq/linux-how-to-delete-a-partition-with-fdisk-command/"). 


Vaig llegir al web de psychocats que es aconsellable aixó de deixar /home en una partició. Entenc que ara que ja he instal.lat el Gutsy ja no hi sóc a temps, suposo que s'ha de fer durant la instal.lació... ho provaré la propera vegada. :)

---

