---
title: "No consegueixo arrencar correctament"
date: 2009-12-10
forum: Catalan Team
---

### Post by knuss on 2009-12-10
Hola a tothom!!
 

 Em sap greu però una vegada mes us he de demanar ajuda,,,
 El meu fill petit em va parar el Pc per la cara i desde aleshores no hi ha hagut manera  
 de engegarlo bé.
 Al engegar em surt  error num15. I em diu que no troba el fitxer.
 

Aleshores vaig probar d'arrencar amb el SGD i practicament amb totes les opcions llevat d'una no em deixa.Nomes em deixa en “arrencar linux directament” i en aquest menu li he de dir que el disc es scassi (?¿) per que engegi.
 De totes les altres opcions crec que ho he probat tot , arreglar el grub , borrarlo , tornar-lo a instalar
 pero no hi ha manera.
 

 Aleshores com ja us he dit nomes arrenco amb arrencada directament .  
 Com que vaig pensar que s'havia carregat el grub i vaig seguir uns manuals per arreglar-lo
 i en teoria ara hauría d'estar be.Pero quan reinicio em torna al error 15 altre vegada.
 

 

 Si segueixo les altres opcions del SDG m'acaba sortint sempre el mateix:
 

 Warning. Boot device may be renamed . Try root :/dev/sda1
 Gave up waiting for root device. Common problems :
 

 -Boot args. (cat /proc/cmdline)
 -Check root delay : (did the system  wait for longh enough?)
 -Check root : (did the system wait for the right device)
 

 -Missing modules (cat /proc/modules; 1s /dev)
 

 Alert /dev/hda1 doesn't exist . Dropping to a shell.
 

 

 No se si tinc algun problema amb la bios ,,,
 

 Us poso una copia del menu.lst a veure si us pot donar alguna pista,,,
 

 

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=10918635-5877-427d-995a-3161f1c3556e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title        Ubuntu 9.04, kernel 2.6.28-15-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=10918635-5877-427d-995a-3161f1c3556e ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=10918635-5877-427d-995a-3161f1c3556e ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


 Ospes es que estic verdaderament aturat , ja no se que mes provar.
 Qualsevol ajuda es benvinguda,,,


 Gracies per endavat >> Cesc

---

### Post by knuss on 2009-12-13
Hola de nou!

Encara no m'en surto,,,:( 

Poso el resultat de arreglar al grub per si us serveix d'algo ,,,,
Crec que l'arreglo be però que al arrencar no el troba per aixo lo del error 15,,,


grub> find /boot/grub/stage1
 (hd0,0)

grub> root (hd0,0)

grub> setup (hd0,0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,0)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,0)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0,0) /boot/grub/stage2 p /boot/grub/menu
.lst "... succeeded
Done.

grub> quit



Ja estic desesperat,,,,,,,,,


Salutacions >>> Cesc

---

### Post by knuss on 2009-12-13
Hola a tothom de nou!!!!!

Be a la fi després d'una setmana ho he aconseguit !! 
Tot el problema estava en que el grub (tal com veieu a baix) em cridaba les versions
dels fitxers initrd.img , vmlinuz , i la del kernel mes antigues  (2.6.28-15) de les que ja tenia les 2.6.31-16.L'he editat i les he substituït i llestos a corra ,,,,

El que no entenc es perque m'ha passat i perque al restaurar el grub no ho feia correctament o sigui que si teniu una explicació si us plau a veure si me l'ha podeu dir.


title        Ubuntu 9.04, kernel 2.6.28-15-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=10918635-5877-427d-995a-3161f1c3556e ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=10918635-5877-427d-995a-3161f1c3556e ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

Potser algú es trobi igual que jo.
Ospes !! m'ha fet gruar de valent ,,,,:D però n'estic molt content ara ,,,

Salutacions >> Cesc

---

