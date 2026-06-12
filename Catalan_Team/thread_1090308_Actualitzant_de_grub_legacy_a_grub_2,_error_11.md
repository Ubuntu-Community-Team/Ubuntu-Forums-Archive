---
title: "Actualitzant de grub legacy a grub 2, error 11"
date: 2009-03-08
forum: Catalan Team
---

### Post by Haliotis on 2009-03-08
Hola, sóc molt novell en ubuntu.
Tinc la darrera versió de l'ubuntu en un dell inspiron 1545. Venia amb windows vista, i l'hi he instal·lat l'ubuntu fa 4 dies. Tot anava bé, fins que se'm va ocòrrer utilitzar el gestor de paquets syn aptics per actualitzar el grub. El gestor de paquets em va fer una proposta on m'instal·lava el grub 2 i algunes coses més (que no recordo) i em marcava per desinstal·lar el grub (que he descobert que el grub vell es diu grub legacy). Vaig acceptar. Em va demanar una línia de comanda, que vaig deixar sense escriure (suposo que aquí està l'error). i vaig tornar a acceptar.
Al reiniciar la pantalla on el grub et deixa triar sistema opertaiu m'hi trobo:
- una primera opció que és: chainload into GRUB2
- a sota una frase que diu: When you have verified GRUB2 works, you can use this command to complete the upgrade: upgrade-from-grub-legacy
- i a sota d'aixo em venen les opcions de sistema opertatiu, les 5 que emproposa des de l'ubuntu, i la del windows vista.

El problema ve quan trio qualsevol linia que no sigui la de windows vista em surt el següent error:
Error 11: unrecognized device string
Press any key to continue

i tornem a la pantalla anterior.

Les solucions que he provat fins al moment és utilitzant el CD del superGRUB, on se suposa que he reinstal·lat el grub, pèro tot segueix exactament igual, i utilitzant el CD d'ubuntu arrencant dels del CD (que crec que s'en diu en mode LIVE) obrint un terminal i posant unes quantes línies que he trobat googlejant que se suposa que m'han reinstal·lat el grub, pe`ro tot segueix igual encara.

L'alternativa a tot plegat és utilitzar el recovery de dell, tornar a instal·Lar windows vista de defecte, i després toranr a instal·lar ubuntu. Total, encara no hi he passat les dades, i només perdria els dues tardes configurant vista i ubuntu... Però em fa ràbia si puc trobar la manera de solucionar-ho.

En fi, espero que algú em pugui ajudar, recordo que sóc molt novell amb linux i el tema d'escriure en terminals si m'ho expliqueu ho necessito fil per randa.

Moltíssimes gràcies.
Max

---

### Post by papapep on 2009-03-08
Benvingut al fòrum, Max.
Gràcies per l'esforç explicant les teves aventures amb el grub2 :)

En aquest fil, diuen que ho han pogut arreglar (com estàs d'anglès?):
[http://ubuntuforums.org/showthread.php?t=1022594&page=3](http://ubuntuforums.org/showthread.php?t=1022594&page=3)

---

### Post by Haliotis on 2009-03-08
Gràcies Papapep!
El meu anglès.. més o menys tira, però el meu anglès tècnic en ubuntu és nefast...
he llegit el post, i sí m'hi veig que és el mateix que em va passar a mi, però la diferència és que jo després d'actualitzar ja no vaig obrir cap terminal, i ara ja no he pogut tornar a entrar a ubuntu.
Si em pots fer una traducció en català (o anglès) pe`ro amb termes senzills, seria genial ;)
moltíssimes gràcies

---

### Post by RainCT on 2009-03-08
Ostres, a mi em va passar exactament el mateix XD. I també crec que l'error va ser no escriure res al camp aquell que surt...

Sento no poder-te ajudar però no me'n recordo com vaig tornar a arreglar-lo (a part que va ser tornant al Grub 1 i passant-me una bona estona jugant amb els fitxers de configuració :P).

---

### Post by RainCT on 2009-03-08
En quant a com tornar a entrar a la terminal, ho pots fer entrant amb el Live CD de l'Ubuntu i allà fent en una terminal:

```

$ sudo mount /dev/sda1 /mnt
$ sudo mount -o bind /proc /mnt/proc
$ sudo mount -o bind /sys /mnt/sys
$ sudo chroot /mnt

```

El signe del dòlar vol dir que és una instrucció a la terminal escrita com a l'usuari normal (és a dir, no l'escriguis, si copies les ordres posa només a partir del "sudo"), i a "/dev/sda1" has de canviar l'"sda1" pel nom de la partició on tinguis insta&#320;lat l'Ubuntu.

Un cop fet això hauries d'acabar dins d'una terminal d'usuari "root" de l'Ubuntu que tens insta&#320;lat, i allà pots executar les ordres que vulguis. Si només amb editar els fitxers de configuració del GRUB en tens prou, no et cal fer això sinó que amb trobar la partició on estan (que des del Live CD **no** és "/boot") n'hi ha prou.

---

### Post by Haliotis on 2009-03-08
Gràcies RainCT!!
he aconseguit entrar al terminal com a root.
Des d'allà he fet
sudo update-grub2
com deia el link a un post en anglès d'algú que li havia passat el mateix... però no m'ha reconegut l'ordre.
Des de root he pogut veure tots els arxius que hi ha en la carpeta del grub. És a dir que els podria modificar manualment... però no sé què modificar ni com.. si algú que ho tingui tot normal em pot dir quins arxius hauria d'haver a la carpeta en qüestió (/boot/grub/) i com haurien de ser... potser puc fer alguna cosa...
no sé é snomé suna idea...
gràcies de totes maneres.
Max

---

### Post by papapep on 2009-03-08
Enganxa aquí el contingut de /boot/grub/menu.lst

---

### Post by Haliotis on 2009-03-08
Crec que l'estic liant me&#347; del compte...
He entrat pel terminal per poder veure que hi posa a l'arxiu menu.lst
L'ordre en el terminal és cat, oi?
weno em posa el següent:

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=d54ed0bb-5cf5-4a8e-af58-766efb7ef8f0 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d54ed0bb-5cf5-4a8e-af58-766efb7ef8f0

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(single-user) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Chainload into GRUB 2
root		d54ed0bb-5cf5-4a8e-af58-766efb7ef8f0
kernel		/boot/grub/core.img

title		&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
root
		
title		When you have verified GRUB 2 works, you can use this command to
root

title		complete the upgrade:  upgrade-from-grub-legacy
root

title		&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
root

title		Debian GNU/Linux, kernel 2.6.27-11-generic
root		d54ed0bb-5cf5-4a8e-af58-766efb7ef8f0
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=d54ed0bb-5cf5-4a8e-af58-766efb7ef8f0 ro quiet splash
initrd		/boot/initrd.img-2.6.27-11-generic

title		Debian GNU/Linux, kernel 2.6.27-11-generic (recovery mode)
root		d54ed0bb-5cf5-4a8e-af58-766efb7ef8f0
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=d54ed0bb-5cf5-4a8e-af58-766efb7ef8f0 ro single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Debian GNU/Linux, kernel 2.6.27-7-generic
root		d54ed0bb-5cf5-4a8e-af58-766efb7ef8f0
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d54ed0bb-5cf5-4a8e-af58-766efb7ef8f0 ro quiet splash
initrd		/boot/initrd.img-2.6.27-7-generic

title		Debian GNU/Linux, kernel 2.6.27-7-generic (recovery mode)
root		d54ed0bb-5cf5-4a8e-af58-766efb7ef8f0
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d54ed0bb-5cf5-4a8e-af58-766efb7ef8f0 ro single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Debian GNU/Linux, kernel memtest86+
root		d54ed0bb-5cf5-4a8e-af58-766efb7ef8f0
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1


Això és tot, no entenc res de res...
merci pels esforços!
Max

---

### Post by Haliotis on 2009-03-09
Val, he buscat que hi havia al menu.lst d'algú que ho tingués penjat en algun foro... com més avall, més canvia... però a la línia 56 escrita del meu menu.lst, és on he descobert la cosa rara (poso des de la línia 53 a la 57):

## e.g. kopt=root=/dev/hda1 ro
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=d54ed0bb-5cf5-4a8e-af58-766efb7ef8f0 ro

## default grub root device

aquesta barreja de números i lletres tb m'ha sortit algun cop, j ano recordo quan :S
potser era utilitzant el superGRUB...
algú pot verificar la meva teoria, i proposar-me una alternativa al que hi ha escrit?
em seria de gran ajuda, moltíssimes gràcies.
Max

---

### Post by papapep on 2009-03-09
Aquí hi ha alguna cosa que se m'escapa....tu tens instal·lat un Ubuntu o un Debian???

> title **[COLOR="Red"]Debian[/COLOR]** GNU/Linux, kernel 2.6.27-11-generic
root d54ed0bb-5cf5-4a8e-af58-766efb7ef8f0
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=d54ed0bb-5cf5-4a8e-af58-766efb7ef8f0 ro quiet splash
initrd /boot/initrd.img-2.6.27-11-generic

title **[COLOR="Red"]Debian[/COLOR]** GNU/Linux, kernel 2.6.27-11-generic (recovery mode)
root d54ed0bb-5cf5-4a8e-af58-766efb7ef8f0
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=d54ed0bb-5cf5-4a8e-af58-766efb7ef8f0 ro single
initrd /boot/initrd.img-2.6.27-11-generic


Enganxa el contingut de /etc/apt/sources.list

---

### Post by Haliotis on 2009-03-09
hola!
en principi és l'Ubuntu que em vaig baixar d'aquí [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) . Com no l'hagi liat fent servir el CD del superGRUB...
en el sources.list (també tinc un sources.list.d no sé si és important) hi posa això:

#deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse

(de pas... alguna senzilla guia d'ubuntu per entendre una miqueta això per sobre? :P)

Gràcies!

Max

---

### Post by papapep on 2009-03-09
Doncs ho tens bé això...no entenc per què al menu.lst fica Debian...deu ser tema del Supergrub aquest...
No sé en quin moment o actuació s'ha emmarranat el tema, no veig per on ajudar-te.

Pel que dius de "guies senzilles", aquí tens un grapat de coses per a consultar:

[https://wiki.ubuntu.com/CatalanTeam/Recursos](https://wiki.ubuntu.com/CatalanTeam/Recursos)

probablement per començar, t'anirà bé llegir:

El sistema de paquets de Debian (i derivats):
[http://acacha.dyndns.org/mediawiki/index.php/APT_i_DPKG#Repositoris_o_Fonts_de_programari](http://acacha.dyndns.org/mediawiki/index.php/APT_i_DPKG#Repositoris_o_Fonts_de_programari)

Les versions i variants d'Ubuntu:
[https://wiki.ubuntu.com/CatalanTeam/Recursos/Versions_Ubuntu](https://wiki.ubuntu.com/CatalanTeam/Recursos/Versions_Ubuntu)

Un tutorial d'ordres i interioritats de Gnu/Linux:
[https://wiki.ubuntu.com/CatalanTeam/Recursos/Int%C3%A8rpretComandes](https://wiki.ubuntu.com/CatalanTeam/Recursos/Int%C3%A8rpretComandes)

I a internet pots trobar autèntiques muntanyes de documentació. Tot es començar i anar acumulant conceptes ;)

---

### Post by Haliotis on 2009-03-09
gràcies papapep.
crec que reinstalaré l'ubuntu, he vist en un altre post com fer-ho sense liarla cacho...
i per lo de les guies, perfecte, sé que hi ha un munt d'informació... però encara no em veia amb criteri per començar per algún cantó.
Merci per tot
Algun dia seré jo qui posi els posts d'ajuda :P
Max

---

