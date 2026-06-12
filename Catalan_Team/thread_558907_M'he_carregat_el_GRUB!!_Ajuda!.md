---
title: "M'he carregat el GRUB!! Ajuda!"
date: 2007-09-24
forum: Catalan Team
---

### Post by kukat on 2007-09-24
Açò de que t'ensenyes coses a classe es un problema. Estava intentant posar un fons al GRUB, i ara no m'arranca l'instalació de Guindows. Hem donaria igual, però necessite gastar-lo per a clase. :(

I el problema no acaba ahí, per que misteriosament, al meu Ubuntu Studio hem surten 9 opcions (4 low latency (amb recovery), 4 generic (amb el seu recovery), el memtest, i el de Windows. Això es un problema que ja duc arrastrant des de fa temps... Per què hem surten repetides les d'Ubuntu????? Sols tinc un Ubuntu Instalat!! 

Però bé, vos deixe el resultat de:  sudo gedit /boot/grub/menu.lst

splashimage (hd1,0)/boot/imagenes/fondo.xpm.gz

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
timeout		30

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
# kopt=root=UUID=64c85bb2-4512-4e8d-8de5-9db93a836194 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

## ## End Default Options ##

title		Debian GNU/Linux, kernel 2.6.20-16-lowlatency
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-lowlatency root=UUID=64c85bb2-4512-4e8d-8de5-9db93a836194 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-lowlatency
boot

title		Debian GNU/Linux, kernel 2.6.20-16-lowlatency (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-lowlatency root=UUID=64c85bb2-4512-4e8d-8de5-9db93a836194 ro single
initrd		/boot/initrd.img-2.6.20-16-lowlatency
boot

title		Debian GNU/Linux, kernel 2.6.20-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=64c85bb2-4512-4e8d-8de5-9db93a836194 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
boot

title		Debian GNU/Linux, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=64c85bb2-4512-4e8d-8de5-9db93a836194 ro single
initrd		/boot/initrd.img-2.6.20-16-generic
boot

title		Debian GNU/Linux, kernel 2.6.20-15-lowlatency
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-lowlatency root=UUID=64c85bb2-4512-4e8d-8de5-9db93a836194 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-lowlatency
boot

title		Debian GNU/Linux, kernel 2.6.20-15-lowlatency (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-lowlatency root=UUID=64c85bb2-4512-4e8d-8de5-9db93a836194 ro single
initrd		/boot/initrd.img-2.6.20-15-lowlatency
boot

title		Debian GNU/Linux, kernel 2.6.20-15-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=64c85bb2-4512-4e8d-8de5-9db93a836194 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
boot

title		Debian GNU/Linux, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=64c85bb2-4512-4e8d-8de5-9db93a836194 ro single
initrd		/boot/initrd.img-2.6.20-15-generic
boot

title		Debian GNU/Linux, kernel memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Altres Sistemes Operatius:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


Ja se que es molt llarg, però crec que es l'única solució per ajudarme... si ho veieu excesiu lleveu-me el post i indiqueume que puc fer!! 

Gràcies, però segur que es alguna xorrada...espere...:oops:

---

### Post by kukat on 2007-09-24
Ah!!! Oblidaba que igual teniu que saber quins discs durs i etcètera tinc instalats...

kukat@kukat:~$ sudo fdisk -l

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               2        2611    20964825    f  W95 Ext'd (LBA)
/dev/hda2   *        2612       15359   102398310    c  W95 FAT32 (LBA)
/dev/hda3           15360       30401   120824865    7  HPFS/NTFS
/dev/hda5               2        2611    20964793+   7  HPFS/NTFS

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9352    75119908+  83  Linux
/dev/hdb2            9353        9729     3028252+   f  W95 Ext'd (LBA)
/dev/hdb5            9353        9729     3028221   82  Linux swap / Solaris
kukat@kukat:~$

---

### Post by papapep on 2007-09-24
I perquè no ens expliques què has fet abans de que et deixès de funcionar? Ens ho posaràs molt més fàcil.

Per cert, suposo que ja has après que hi ha coses amb les que NO s'ha de "jugar" quan l'ordinador és un productiu (o sigui, que et fa falta per treballar) :-)

---

### Post by sianeu on 2007-09-24
Jo quan em carrego el grub al reinstalar windows faig servir un programa, el SuperGrub, que me'l arregla amb un plisplas. El pots aconsegir d'aqui

[http://forjamari.linex.org/]("http://forjamari.linex.org/")

Salut

---

### Post by kukat on 2007-09-24
No tinc ni idea que he fet.

Pot ser:

He colocat lo de la imatge al damunt.

He cambiat els noms dels Ubuntu a "title", però al fer "sudo update-grub" els noms tornen a posarse com estaven (els 9 que he comentat abans...) , així que eixe no deu ser el problema. 

he cambiat el de: " title		Altres Sistemes Operatius:", que estava en anglés i l'he posat en català.

he cambiat el temps d'espera del GRUB a 30 segons. 

i per últim (ja voràs com serà açò) , he intentat fer el que diuen a aquesta web: [http://www.cesarius.net/como-cambiar-la-imagen-del-grub-en-ubuntu/](http://www.cesarius.net/como-cambiar-la-imagen-del-grub-en-ubuntu/), però m'he quedat per el pas "sudo grub-install /dev/hda", per que no hi havia manera, hem donava error... però no se, tampoc li veig lògica de per que funciona tot, però el windows no.

---

### Post by kukat on 2007-09-24
El Super Grub es una imatge de CD? Es que no sé el que he baixat, hi ha moltes coses i està en anglés...

---

### Post by pespin on 2007-09-24
Tinc un esborrany al blog per a refer el grub si casca (exemple, instal·lació de windows) que vaig fer fa algun temps. En principi amb un LiveCD de Ubuntu per exemple, ja en tens prou:
[URL="http://espeblog.no-ip.org/?p=11"]
http://espeblog.no-ip.org/?p=11[/URL]

---

### Post by marcoil on 2007-09-24
Has provat de fer

sudo update-grub

L'update-grub és el programa que gestiona el menu del grub. Per cert, si tens tantes entrades es perquè tens moltes versions del kernel instal·lades, ho pots comprovar al synaptic. Bona sort!

---

### Post by orestesmas on 2007-09-25
El "update-grub" refà el fitxer /boot/grub/menu.lst a partir dels nuclis que troba instal·lats, però ho fa seguint unes directrius que estan en el propi fitxer "menu.lst". Aquestes directrius poden despistar una mica, perquè si les mires semblen comentaris, però si llegeixes l'explicació en anglès es veu que les línies que comencen amb UN SOL caràcter "#" són comentaris per qualsevol programa excepte per l'update-grub, que les considera com a directrius de funcionament.

Per exemple, si no vols que t'inclogui les versions de "recovery" dels nuclis només has de canviar la línia:

# alternative=true

per:

# alternative=false

El nucli "alternative" és exactament el mateix que el normal, però al qual se li passen unes opcions d'arrencada diferents per tal de situar el sistema en mode monousuari i donar-te una consola de root en arrencar, per tal de solucionar problemes. Pots fer que no apareguin a la llista, però si tens problemes hauràs de passar les opcions a mà, o usar un CD-Autònom per arrencar el sistema.

---

### Post by Ferri on 2007-09-25
Si has editat manualment el "menu.lst" és probable que tinguis una còpia de seguretat que probablement es diu "menu~" a la mateixa carpeta. Pots intentar copiar la versió antiga sobre la nova i a veure si ho arregles (abans copia't les dues version per poder comparar-les i veure què ha fallat). Lògicament això és suposant que el problema estigui al "menu.lst".
Per cert, les versions "repetides" d'Ubuntu les tens perquè tens instal·lada més d'una kernel, concretament tens 2.6.20-16-generic, 2.6.20-16-lowlatency, 2.6.20-15-generic i 2.6.20-15-lowlatency.
Que tinguis la versió 2.6.20-15 i 2.6.20-16 és normal, perquè és el resultat d'una actualització de la kernel. Si et funciona bé la 2.6.20-16 pots desinstal·lar la 15 (busca al Synaptic 2.6.20-15 i desinstal·la el que toqui).
Que tinguis la versió "generic" i la "lowlatency" ja no és tan normal, segurament has fet instal·lar tu mateix la "lowlatency". Si fas anar la "generic" i et va vé, també pots treure la "lowlatency" (o a l'inrevés).
Si treus totes les kernel que no fas servir l'únic que guanyes és espai al disc dur i un menú més curt al grub, però la meva opinió és que no té sentit tenir instal·lat quelcom que no fas servir.

---

### Post by CarlesOriol on 2007-09-25
Eps. Em sembla que el company ha dit Ubuntu STUDIO i per fer-lo (els programes d'audio digital) correr cal el nucli lowlatency.

---

### Post by Ferri on 2007-09-25
D'acord. En aquest cas, pot passar de la generic i quedar-se amb la lowlatency (ja havia posat que ho podia fer a l'inrevés si era el cas).

---

### Post by prostata on 2007-09-25
Hola company:

Si, i només si, et dona igual partir de l'instalació de windows per desprès particionar i instal-lar novament ubuntu, jo t'aconsello que facis el següent:

A) arrenca l'equip amb el cd de Windows
B) quna hagi fet el que calgui i arribis a que et pregunti si vols recuperar   windows en modo consola, li dius que OK
C) i en aquesta situació escriu això:  fixmbr i reinicies el SO, però recorda treu-re el CD WXP, per no tornar a repetir el process.

Això el que farà serà recuperar el MBR i et permetrà arrencar el SO però des de Windows. Desprès...tu mateix.
Ànims!!!

---

### Post by kukat on 2007-09-26
He probat el SuperGrub Disc, i no fa res, simplement hem torna al menu que tenia abans on no es pot accedir a Windows.

He formatejat windows, i després he intentat restaurar el Grub, però clar, torna a fer servir el mateix menú, i tampoc hem deixa accedir a Windows.

He buscat una còpia de seguritat del menú, i no hi ha cap (mal fet, hauria de haver fet una còpia, però no m'esperava aquest problema...:().

I el que diuen de la "consola de recuperación" hem veuria obligat a instalar una altra vegada Ubuntu???? I clar, tendría que tornar a instalar tot el que tinc???
 
No esperava que posar una foto de fons, i cambiar el nom de l'Ubuntu pugera trencar-me la GRUB... Encara estic intrigat amb el que ha pogut passar...:sad:

Gràcies a tots per la vostra col.laboració !!! :popcorn:

---

### Post by papapep on 2007-09-26
> He formatejat windows, i després he intentat restaurar el Grub, 

...segons tu, què vol dir "formatejar windows"? te l'has carregat??

> però clar, torna a fer servir el mateix menú, i tampoc hem deixa accedir a Windows.

Si has fet el que dius abans, evidentment que no et deixa, no hi és...

---

### Post by kukat on 2007-09-26
No!! jejeje. 

Tinc Windows a una partició de 20 GB. Tots els fitxers: pelis,musica,programes, etc. No están en exia partició, així que he tornat a instalar Windows en els 20GB, per a veure si després, amb la posterior restauració del GRUB de linux (ja que el Windows l'estropeja) podría accedir a Windows... però no!!

Hem passa el mateix que en un principi. Puc accedir a Ubuntu, però al Windows hem dona error (error 12).

---

### Post by prostata on 2007-09-26
> **kukat said:**
> No!! jejeje. 

Tinc Windows a una partició de 20 GB. Tots els fitxers: pelis,musica,programes, etc. No están en exia partició, 

A veure company que o no t'entenc o no t'enetenc:
Dius que ten W2000 a una partició de 20 gb, Si?-No?
Però dius que tots el programes, pelis etc, etc no els tens en aquesta partició, Si?-No?

Aleshores vol dir que no tens més que el SO W2000 en aquesta partició Si?-No?

On tens a leshores els preogrames i demés??? a un altre partició?? a la partició Ubuntu que está espallada??....

així que he tornat a instalar Windows en els 20GB, per a veure si després, amb la posterior restauració del GRUB de linux (ja que el Windows l'estropeja) podría accedir a Windows... però no!!

Hem passa el mateix que en un principi. Puc accedir a Ubuntu, però al Windows hem dona error (error 12).


Company, tú fes el que vulguis, ok?, però si jo estigués en el teu cas idesprès de fer back-up del que jo considerès important, faria el següent, de fetho faig mab alguna frequència:

A) Instala el Geparted [google]
B) Posa el Geparted a la disketera de forma que arrenqui el programa  quan arrenqui l'equip, ja saps, ves a la bios i etc... etc..etc..
C) quan el Geparted el tinguis a la vista, agafa la primera opció que et mostri, fes intro, enter etc, etc.
D) Esborra, carregat la partició Ubuntu, la swap i la extesa del mateix SO, Ubuntu.
F) no t'oblidis de Aplicar en cada cas per que els canvis es portin a terme.
G) Mateixos processos per carregar-te W2000
H) Reinicia l'equip i treu el CD del Geparted i en el seu lloc posa el de W2000 o la versió que facis servir.

A partir d'aquesta situació, estás en condicions de fer unes noves instalacions netes tant de Windows com les següentes particions per Ubuntu, kubunut, UberUbuntu, etc....

Torno a dir, tú fes el que vulguis, però jo faria el que acabo de esriure, i desprès com que per aquí hi ha molta gent amb amplìssims coneixements de Linus-Ubuntu, els demanaria si us plau si em poden indicar quines han estat les causes per les quals m'ha passat el que m'ha passat....

Ape!!!!! ànims i endevant.....

---

### Post by kukat on 2007-09-26
Tinc una partició amb 20 GB, on està instalat WINDOWS XP.
Tinc un altra partició NTFS de 100 GB, on tinc pelis, musica, programes....etc.
Tinc una altra partició FAT32 de 90 GB on guarde també pelis, musica, programes, etc, per a que pugen llegir-ho els dos sistemes operatius (tant Windows com UBUNTU)
I finalment, tinc una altra partició de 90 GB on tinc l'Ubuntu Studio. 

El Grub funciona correctament, però hem dona un error 12: no device found o una cosa així, al voler entrar a Windows XP. 

Vaig instalar Windows XP altra vegada (als 20 GB), per a veure si s'arreglava, però res, torna a passar el mateix una vegada restaure el GRUB (que es trenca quan instales WXP) . 

Solament volia saber si hi ha alguna forma d'arreglar-ho sense tindre que instalar UBUNTU STUDIo altra vegada.......El Windows puc instalar-ho les voltes que faça falta, ja que els 20 GB on el tinc, no hi ha res de gran valor.... :(

Demane disculpes per les meves explicacions pèsimes.

---

### Post by Ferri on 2007-09-26
A veure...
Sospito que potser tens mal especificada la unitat des d'on se t'ha d'engegar el sistema del senyor Gates.
Pel que veig tens, com a mínim, dos discs durs, hda i hdb. En la notació del grub això correspon a hd0 i hd1. El segon número, correspon al número de partició, començant pel 0, és a dir, la 1a partició del primer disc dur seria (hd0,0) o, per agafar un altre exemple, la 2a partició del segon disc seria (hd1,1).
[Més informació aquí]("http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System").

---

### Post by kukat on 2007-09-26
**TINC AÇÓ:**

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 2 2611 20964825 f W95 Ext'd (LBA)
/dev/hda2 * 2612 15359 102398310 c W95 FAT32 (LBA)
/dev/hda3 15360 30401 120824865 7 HPFS/NTFS
/dev/hda5 2 2611 20964793+ 7 HPFS/NTFS

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hdb1 * 1 9352 75119908+ 83 Linux
/dev/hdb2 9353 9729 3028252+ f W95 Ext'd (LBA)
/dev/hdb5 9353 9729 3028221 82 Linux swap / Solaris

**I AÇÓ:**

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Altres Sistemes Operatius:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by Ferri on 2007-09-26
Sí, això ja ho vas posar.
Però saps a quina partició t'arrenca el windows?
Tens dues NTFS, una FAT32 i dues W95 Extended. Apostaria per una de les dues NTFS. Amb les particions esteses em perdo una mica, però potser podries intentar hd0,2 o hd0,4 en lloc del hd0,0 que tens al menu.lst. El pitjor que et pot passar és que et segueixi sense funcionar ;-)

---

### Post by papapep on 2007-09-26
próstata: evidentment, com tu bé dius, cadascú ho fa com li sembla, però si cada vegada que tenim un problema hem de fer-ho tot de cap i de nou tirem a l'aigua tota la feina feta i no aprenem res, només a reinstal·lar un i altre cop
. 
Apart, ja em diràs tu com li podem dir a algú què ha fet malament si no hi ha res per mirar, ja que ho ha esborrat tot i ha tornat a començar de 0.
Aquesta només és una solució quan no n'hi ha cap més, i això passa molt pocs cops.

Kukat: alguna cosa no quadra, ja que windows quan s'instal·la s'apropia (com no podria ser menys) del sistema i no té en consideració si n'hi ha d'altres o no. No acabo d'entendre com pot ser que l'instal·lis i et segueixi sortint el grub de linux.
Puc entendre que el windows l'instal·les a la partició de 20Gb de nom /dev/hda5??
Si no recordo malament, windows sempre volia ser a la primera partició... no sé si pot anar per aquí el teu problema.
Una altra possibilitat, com diu el Ferri, és que tinguis mal configurat el grub. 
Prova modificant el menu.lst de la següent manera, on fica:

> root (hd0,0)

fica-hi:

> root (hd0,4)

Ja que la hd0,0 que t'hi surt, segons els teus fitxers, correspon amb aquesta partició:

> /dev/hda1 2 2611 20964825 f W95 Ext'd (LBA)

la qual dubto que sigui el teu windows XP.

A veure què tal.

---

### Post by Ferri on 2007-09-26
Ep!
Perdona, m'acabo de mirar un altre cop el teu post, i pel que sembla la partició que està marcada com a arrencable del disc que tens la majoria de particions Windows és /dev/hda2 (per l'asterisc que ho indica). En aquest cas, el correcte al menu.lst crec que hauria de ser així:```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional
root (hd0,1)
savedefault
makeactive
chainloader +1
```
Si no funciona, proba amb les altres opcions que t'he dit. Potser el problema és que no tens posada com a arrencable la partició correcta. Si fos així ho pots arreglar amb el gparted.

---

### Post by papapep on 2007-09-26
Doncs segueix sense quadrar tot plegat, ja que ell diu que ho instal·la en una partició de 20 Gb, i hd2 en té 100 Gb....

kukat, no quadra rien de rien....

A veure, jo provaria a fer anar el qtparted, gparted o el que sigui, i marcar com a arrencable la partició hd5 (root, hd0,4) que és on dius que has posat el windows a veure si et va.

---

### Post by kukat on 2007-09-26
Escric aquestes paraules des de la brossa de Windows XP (perdoneu per el vocabulari), i amb el lleig i inútil Internet Explorer, per dir: 

**Ja està arreglat!! **Com tu has dit ara al final (la veritat es que he anat probant totes, primer amb les que m'has dit abans, i després amb tots els números...jejej), i per fi funciona!!!
La configuració correcta es (0,1). No sé el per qué, però així és...  

Moltes gràcies a tots, jo ja pensava que tendria que instalar-ho tot de nou!!!!

**Per mi es un honor dir que ja podeu posar [SOLVED] al davant d'aquest post!**!!:guitar:

---

### Post by prostata on 2007-09-27
Estimat company papapep

Tens molta raó en el que em dius, però si et fixes en els meus post podràs observar que li vaig oferir més d'una opció, i sempre en funció de l'info. que el company ens anava passant. No a estat fins als darres post que ell a plantajat correctament la seva arquitectura de discos i diferents SO que en te instal-lats en aquest i fins i tot quina partició era la responsble del inici del sistema.

Segurament no hauria d'haver respost res per l'incorrecte plantejament del problema, però això em passa a mi mateix a l'hora d'escriu-re....per tant.....fixat en tot el fil sobre tot en les dues primeres pàgines.
Salutacions

---

### Post by papapep on 2007-09-27
Próstata: La qüestió rau en que si als usuaris els donem la sensació de que reinstal·lar és LA SOLUCIÓ, s'hi agafen sense més plantejaments (no tots evidentment com has pogut veure) ni cap altra esforç per la seva, ni nostra, part. A mi també em seria més fàcil així, t'ho asseguro.

No et sàpiga greu el que et dic, no és cap atac ni res semblant, però hi ha certes coses que hem de tenir present tots plegats.

---

