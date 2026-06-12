---
title: "problemes de arranc"
date: 2013-05-09
forum: Catalan Team
---

### Post by llea on 2013-05-09
Hola soc nou usuari de Lubuntu i ara he de utilitzar un programa que utilitzaba en windows, el problema es que no apareix el grub al engegar el ordinador, he seguit els passos que diu la guia per a actualizar el grub  ( [COLOR=#000000][FONT=monospace]$ sudo update-grub2 ) i segueix igual, h fget la segona opcio ([/FONT][/COLOR][COLOR=#000000][FONT=monospace]$ sudo aptitude install grub2) i respon ([/FONT][/COLOR]sudo: aptitude: orden no encontrada )  suposo que no caldra recuperar el grub perque el grub ja esta instal.lat.

Agrairia que algu pugués ajudar-me

---

### Post by wgarcia on 2013-05-09
Suposo que quan dius que no apareix el grub vols dir que no es mostra en arrencar, que el sistema se'n va directament al Lubuntu sense mostrar el menú del grub. O és una altra cosa? Perquè si no hi ha el grub el sisetma s'aniria directament al sistema operatiu que pugui o quedaria totalment sense arrencar si el grub està danyat. Però penso que és el primer perquè estàs explicant que estàs fent servir "apt-get" etc i per tant vol dir que sí que arribes al Lubuntu a l'arrencada.

Ara bé, si el que dius doncs és això de què no es mostra el menú, perquè es mostri simplement has de prémer la tecla "majúscules" quan l'ordinador està arrrencant (la de la flexeta cap a dalt del costat del teclat, o "shift") i es mostrarà. 

Tot i que si se'n va directament al Lubuntu això vol dir que no veu més que Lubuntu com a sistema operatiu, i llavors s'haurà d'esbrinar perquè no es veu cap altre sistema operatiu, si tens més d'un instal·lat.

Això de l' "aptitude" passa perquè has d'instal·lar primer aquest programa (sudo apt-get install aptitude) però no és potser necessari, amb l'apt-get ja pots instal·lar tot el que vulguis. Aptitude és més complet i avançat però sols fa falta per situacions molt particulars, en el 99% dels casos amb apt-get ja n'hi ha prou.

---

### Post by llea on 2013-05-10
gracies, pero com has dit he polsat la tecla de majuscules pero tot ha seguit igual, llavor he instal.lat el aptitude com has explicat  per si de cas i he  instal.lat el grub des de aptitude pero continua igual i si hi ha un windows xp instal.lat avans de haver instal.lat lubuntu

---

### Post by tsanchez on 2013-05-10
Bon dia,

Sembla com si només existis l'ubuntu, pots fer en una shell fdisk -l i possar que surt? aixií podriem esbrinar si hi han particions de windows (ntfs, fat32...)

---

### Post by wgarcia on 2013-05-10
En quin moment prems la tecla majúscula? L'has de prémer tot just que passi la verificació de memòria. Si continua sense aparèixer el menú del grub, mira si pots seguir les instruccions d'aquest comentari:

[http://ubuntuforums.org/showthread.php?t=1811334&p=11083289#post11083289](http://ubuntuforums.org/showthread.php?t=1811334&p=11083289#post11083289)

Amb això tindràs informació de si el grub està instal·lat, on, quines particions hi ha, etc.

---

### Post by llea on 2013-05-10
el sistema de les majuscules no funciona, us pose la informacio que dona el fdisk

llea@llea-desktop:~$ sudo fdisk -l 
[sudo] password for llea: 


Disco /dev/sda: 500.1 GB, 500107862016 bytes
255 cabezas, 63 sectores/pista, 60801 cilindros, 976773168 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador del disco: 0x26c726c6


Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *          63   672381708   336190823    7  HPFS/NTFS/exFAT
/dev/sda2       672382974   976771071   152194049    5  Extendida
/dev/sda5       974942208   976771071      914432   82  Linux swap / Solaris
/dev/sda6       672382976   974942207   151279616   83  Linux


Las entradas de la tabla de particiones no están en el orden del disco
llea@llea-desktop:~$ 

pot ser aixo us done mes informacio per poder-me ajudar

---

### Post by Miquel Ubuntero on 2013-05-10
Ho veus, t'ho vaig comentar.
Aquí al fórum hi ha gent que en sap molt més que jo.
Ànims que s'ha d'arreglar.
Salutacions,
Miquel.
Ou llea!

---

### Post by kimet on 2013-05-11
El grub es configura a /etc/default/grub. Pots mirar a aquest fitxer si hi ha alguna cosa com GRUB_HIDE=1 o GRUB_TIMEOUT=0...
També es possible que no estigui en la resolució correcta, prova a descomentar la línia que diu: GRUB_GFXMODE...
Per últim comprova que estigui instal.lat el paquet os-prober.

Salut.

---

### Post by llea on 2013-05-12
Kimet moltes gracies, el que surt a la configuracio del grub es el següent

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console


# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"


No se si es correcte o no, podrieu guiar-me??

---

