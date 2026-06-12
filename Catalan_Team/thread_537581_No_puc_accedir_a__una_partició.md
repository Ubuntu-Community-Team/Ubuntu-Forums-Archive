---
title: "No puc accedir a  una partició"
date: 2007-08-29
forum: Catalan Team
---

### Post by Accidia on 2007-08-29
No sé com començar perquè és una mica llarg i voldria exposar-ho bé.

Tinc dos discs durs. Un IDE  (80gb) i un SATA (320gb). Ide disposo d'ell lliurement (puc particionar-lo com vulgui) 
Pero al SATA tinc una partició (sda1) NFTS amb un windows xp pro i (mil coses que m'agradaria recuperar) que ni windows (instalat temporalment en una particioneta) ni l'ubuntu em detecten.

Tot va començar perquè tenia problemes amb el grub (error 22) intentant-ho arreglar, mirant pels posts del món, la cosa va anar a pitjor o sigui que no m'arrencaba res. Vaig formatar la partició ubuntu i vaig tornar a instalar-lo (a veure si així ho arreglaba) aleshores el grub m'apareixia amb només l'opció de carregar ubuntu. I ja no podia accedir a la partició (he probat de montarla manualment pero no em funciona).

Altrament he pensat de formatarla i emprar algun tipus de programari de recuperació de dades, però no sé fins a quin punt podré recuperar les dades. Faig això? Quin programari em recomaneu en aquest cas?

També, encara que no és estrictament ubuntu, com em recomaneu la instalació dels o.s? un en cada disc? o tots dos al mateix amb dues particions? Ide esclau o master i ens quins casos? 

Finalment, per si em pot servir en un futur, com es gestionen els conflictes d'MBR d'ambdós discs?

Disculpeu per la pallissa; normalment no escric posts, sinó que busco les solucions, però essent tant complex i concret aquests cas no m'ha quedat més remei...

Gràcies per endavant.

---

### Post by papapep on 2007-08-29
Posa, si us plau, com has intentat montar la partició (la ordre exacta). T'ha respost alguna cosa? o simplement no es monta?

Has mirat amb l'fdisk o gparted si detecta la partició?

La resta de particions del disc SATA et funcionen i es monten correctament??

Veus, nosaltres també tenim preguntes :-D

> Disculpeu per la pallissa; normalment no escric posts, sinó que busco les solucions, però essent tant complex i concret aquests cas no m'ha quedat més remei...


Això no ho diguis home (o dona, no sé :-)) el fòrum existeix per a això!!!

---

### Post by Accidia on 2007-08-29
Ara matiex no sóc a casa i no t'ho puc posar exacte, però vaig seguir un tutorial que, a grans trets, creaba un dir (*crec que /media/sda1 o windows*) em feia editar el* /etc/fstab* i després *sudo mount -a*

El disc em funciona bé (les altres particions ok) i recordo que detectar-lo, el detecta, però no recordo haver provat *fdisk* o*gparted*.
El particionador del live cd em detecta la partició (tamany i tipus, nfts, correcte) (aquest és el gparted?)

Ja et dic que tot va començar "barruntant" el grub i amb els dos discs crec que el mbr es va fer "la tita un embolic" (la picha un lio):lolflag:

Segueixo pensant que allò més fàcil seria format i recuperar dades, però el més fácil no sol ésser la millor opció (p.ex. windobs)

---

### Post by papapep on 2007-08-29
> Segueixo pensant que allò més fàcil seria format i recuperar dades, però el més fácil no sol ésser la millor opció

Ostres, no, no....això complica molt el tema. Vaja, jo no ho faria pas.

Podries fer un fdisk i enganxar aquí les dades de les particions que detecta.

---

### Post by orestesmas on 2007-08-29
> **Accidia said:**
> 
Segueixo pensant que allò més fàcil seria format i recuperar dades, però el més fácil no sol ésser la millor opció (p.ex. windobs)

Bé jo diria que si l'objectiu és recuperar dades el que NO has de fer mai és formatar, perquè et pot engegar a fer punyetes informació del sistema de fitxers que pot ser útil per recuperar dades.

La idea seria emprar eines específiques de recuperació, però les més eficaces (és a dir, les manuals) acostumen a requerir de l'operador un coneixement del sistema de fitxers danyat (NTFS en aquest cas) que és difícil de tenir (vaja, almenys jo no el tinc).

Ara bé, si el dany no és gran, com sembla el teu cas, pots provar algun programa de recuperació automàtica de dades sota windows (n'hi deu haver un fotimer per la xarxa...) a veure què tal es comporta.

Sento no poder ajudar més.

---

### Post by Accidia on 2007-08-29
> Ara bé, si el dany no és gran, com sembla el teu cas, pots provar algun programa de recuperació automàtica de dades sota windows (n'hi deu haver un fotimer per la xarxa...) a veure què tal es comporta.


Per al sr. windows aquesta partició no existeix. Per tant, hi ha alternativa linux ? Però caldrà que la partició estigui muntada, no? Així doncs estem igual, crec.:confused:

---

### Post by Accidia on 2007-08-29
Be ja he reinstalat l'ubuntu (despres del windows esclar) i ja tinc  l'fdisk fet:

[SIZE="2"][FONT="Arial Narrow"][SIZE="1"]Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       32765   263184831    7  HPFS/NTFS
/dev/sda2           32766       38913    49383810   83  Linux

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        8511    68364576    7  HPFS/NTFS
/dev/hdb2            8512        8778     2144677+  82  Linux swap / Solaris
/dev/hdb3            8779        9729     7638907+  83  Linux
[/SIZE]
[/FONT][/SIZE]

Però m'ha sorgit un problema GRUB error 22 --> que temporalment tinc solucionat amb el live i l'opicó "boot from first hard disk" (iniciar des del primer disc dur) que em carrega el grub amb les opcions de ubuntu o windows i funciona tot perfectament (fins que reinicio que succeix el mateix).

Així s'aprén no?](*,)

---

### Post by papapep on 2007-08-29
Entenc que no calia reinstal·lar l'ubuntu, però vaja, ara ja ho tens fet.

Caldria veure què tens al fitxer **/boot/grub/menu.lst**

---

### Post by Accidia on 2007-08-29
> Caldria veure què tens al fitxer /boot/grub/menu.lst

[SIZE="2"][FONT="Arial Narrow"]Hi ha tot això:

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

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
# kopt=root=UUID=22866b55-f4dd-475c-9c81-71fe57e7fef1 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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
##      altoptions=(recovery) single
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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=22866b55-f4dd-475c-9c81-71fe57e7fef1 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=22866b55-f4dd-475c-9c81-71fe57e7fef1 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=22866b55-f4dd-475c-9c81-71fe57e7fef1 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=22866b55-f4dd-475c-9c81-71fe57e7fef1 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
[/FONT][/SIZE]

---

### Post by Accidia on 2007-08-30
Alguna ideai? :?

---

