---
title: "no es veu el menú d'instal·lació"
date: 2012-10-10
forum: Catalan Team
---

### Post by jinglada on 2012-10-10
Benvolguts ubunteros:

En un portàtil Easy Note TM86 de Packard Bell, Intel Core i3-330M, Intel HD Graphics, 4GB, 15,6" 16:9 HD LED LCD, Windows 7, he intentat instal·lar l'Ubuntu 12.04 LTS, he baixar la imatge, he construït el cd d'arrancament i quan engego, el menú es veu com una ombra il·legible.
Llavors ho he volgut fer amb el Wubi i un cop he reiniciat quan la instal·lació ho demana, en el reinici passa el mateix: el menú es veu en un fons obscur il·legible.

Què faig?

---

### Post by albandy on 2012-10-10
Fes servir l'alternate cd.

32 bit
[http://releases.ubuntu.com/12.04/ubuntu-12.04.1-alternate-i386.iso](http://releases.ubuntu.com/12.04/ubuntu-12.04.1-alternate-i386.iso)
64 bit
[http://releases.ubuntu.com/12.04/ubuntu-12.04.1-alternate-amd64.iso](http://releases.ubuntu.com/12.04/ubuntu-12.04.1-alternate-amd64.iso)

---

### Post by jinglada on 2012-10-10
> **albandy said:**
> Fes servir l'alternate cd.

32 bit
[http://releases.ubuntu.com/12.04/ubuntu-12.04.1-alternate-i386.iso](http://releases.ubuntu.com/12.04/ubuntu-12.04.1-alternate-i386.iso)
64 bit
[http://releases.ubuntu.com/12.04/ubuntu-12.04.1-alternate-amd64.iso](http://releases.ubuntu.com/12.04/ubuntu-12.04.1-alternate-amd64.iso)

Gràcies, albandy,
ja em funciona l'ubuntu però ara m'he "carregat" el windows. El meu gendre i elmeu nét em maleiran ;-)

Em sembla que fent un disc de recovery des del meu portàtil potser ho puc arranjar. El problema és que jo tinc windows vista i a l'altre hi ha o havia el windows 7.

Si em podeu orientar us ho agrairé de tot cor.

---

### Post by albandy on 2012-10-11
> **jinglada said:**
> Gràcies, albandy,
ja em funciona l'ubuntu però ara m'he "carregat" el windows. El meu gendre i elmeu nét em maleiran ;-)

Em sembla que fent un disc de recovery des del meu portàtil potser ho puc arranjar. El problema és que jo tinc windows vista i a l'altre hi ha o havia el windows 7.

Si em podeu orientar us ho agrairé de tot cor.

Primer de tot comprovarem que les particions de windows encara existeixin. Potser amb una mica de sort es pot recuperar.

Obre una consola (Aplicacions --> Accessoris --> Terminal) i introdueix la comanda següent:

```

sudo fdisk -l 

```

i posa el resultat.

La consola permet copiar el text. Simplement selecciona'l amb el ratolí i al menú superior edita i selecciona copia.

---

### Post by jinglada on 2012-10-11
> **albandy said:**
> Primer de tot comprovarem que les particions de windows encara existeixin. Potser amb una mica de sort es pot recuperar.

Obre una consola (Aplicacions --> Accessoris --> Terminal) i introdueix la comanda següent:

```

sudo fdisk -l 

```

i posa el resultat.

La consola permet copiar el text. Simplement selecciona'l amb el ratolí i al menú superior edita i selecciona copia.

Hola albandy, he estat fora tot el dia i ara et contesto.

joan@ubuntu:~$ sudo fdisk -l
[sudo] password for joan: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb1da1eb9

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sda1              63    25173854    12586896   27  Hidden NTFS WinRE
/dev/sda2   *    25173855    25382699      104422+   7  HPFS/NTFS/exFAT
/dev/sda3        25382700   262939827   118778564    7  HPFS/NTFS/exFAT
/dev/sda4       262940670   361377791    49218561    5  Estesa
/dev/sda5       262940672   298876927    17968128   83  Linux
/dev/sda6       298878976   361377791    31249408   82  Intercanvi Linux / Solaris
joan@ubuntu:~$

---

### Post by albandy on 2012-10-12
Sembla que les particions de Windows encara hi són. 

No et surt un menu al arrencar per seleccionar el sistema operatiu?

En cas de que no surti, adjunta l'arxiu /boot/grub/grub.cfg

---

### Post by jinglada on 2012-10-12
> **albandy said:**
> Sembla que les particions de Windows encara hi són. 

No et surt un menu al arrencar per seleccionar el sistema operatiu?

En cas de que no surti, adjunta l'arxiu /boot/grub/grub.cfg

si que em surt i en seleccionar el 

> menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root FCCCB71CCCB6D05E
	chainloader +1
}

em surt el seg"uent missatge,

> No se puede iniciar windows. Es posible que un cambio de hardware o de sofware reciente sea la causa. para corregir el problema:

1.-inserte el disco de instalacion de windows y reinicie el equipo.
2.-elija la configuracion de idioma y despues haga clic en siguiente
3.-haga clic en reparar equipo

si no tiene este disco, pongase en contacto con el administrador del sistema o con el fabricante del equipo para obtener ayuda:

Estado: 0xc000000f
informacion: Error al seleccionar el arranque, no se puede tener acceso a un dispositivo requerido

No tinc el disc d-instalacio de windows perque no venia en aquest portatil (escric sense accents perque el teclat que m-ha sortit no es el catala) Edito: sol·lucionat lo dels accents: Instal·lant la versió 64 bit [http://releases.ubuntu.com/12.04/ubuntu-12.04.1-alternate-amd64.iso](http://releases.ubuntu.com/12.04/ubuntu-12.04.1-alternate-amd64.iso) et deixa la "Disposició de teclat" en "Català" que no funciona i et deixa l'Anglès i canviant a "Català(Espanya amb L amb punt volat)" ja funciona el teclat català.

---

### Post by albandy on 2012-10-14
Es possible que la primera partició sigui de restauració. Durant l'arrencada, abans de que carregui el grub, et surt alguna opció de recovery?

Si es el cas podràs deixar l'ordinador a l'estat original però perdràs l'ubuntu i l'hauràs de tornar a instal.lar

---

### Post by jinglada on 2012-10-14
> **albandy said:**
> Es possible que la primera partició sigui de restauració. Durant l'arrencada, abans de que carregui el grub, et surt alguna opció de recovery?

Si es el cas podràs deixar l'ordinador a l'estat original però perdràs l'ubuntu i l'hauràs de tornar a instal.lar
------------------------------------------
Gràcies albandy. Si que hi ha l'entrada de menú que dius

> menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
insmod part_msdos
insmod ntfs
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root DA8CB6C38CB69989
drivemap -s (hd0) ${root}
chainloader +1
}

 i de fet ja la vaig executar i em van sortir alguns misatges i el logo del Windows, dient que s'executava el Windows i al final es va quedar molta estona amb una pantalla que deia:
"Packard Bell Recovery Management"
"Please wait a moment"
i un petit cercle que rodava, fins que al cap de dues hores el vaig parar amb l'interruptor.
----------------------------------------------
He fet la consulta a la Packard Bell, sobre el tema del CD que el venedor no va subministrar i diuen que en 24 hores em contestaran.
----------------------------------------------
En el fòrum espanyol  em diuen que faci:

> sudo update-grub
i després
sudo grub-install /dev/sda

Et sembla correcte?

---

### Post by albandy on 2012-10-14
Es per actualitzar la configuració del grub i tornar-lo a instal.lar. No perds res per provar.

---

### Post by jinglada on 2012-10-14
> **albandy said:**
> Es per actualitzar la configuració del grub i tornar-lo a instal.lar. No perds res per provar.

Gràcies albandy!

Ho he fet i segueix igual:

> joan@ubuntu:~$ sudo update-grub
[sudo] password for joan: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-32-generic
Found initrd image: /boot/initrd.img-3.2.0-32-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Recovery Environment (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
done
joan@ubuntu:~$ 

joan@ubuntu:~$ sudo grub-install /dev/sda
Installation finished. No error reported.
joan@ubuntu:~$ 

He parat i he reiniciat amb el "Windows 7 (loader) (on /dev/sda2)" i m'ha donat el mateix missatge que anteriroment. He sortit i he executat el "Windows Recovery Environment (loader) (on /dev/sda1)" i el mateix resultat

> Windows is loading files
starting windows 
"Packard Bell Recovery Management"
"Please wait a moment"
i un petit cercle que roda

I si instal·lés una versió anterior de l'Ubuntu? Perquè ara el que he de fer és aconseguir el CD de Windows i instal·lar-lo, però si torno a instal·lar el mateix 12.04 "alternate" em tornaré a trobar amb el mateix problema, no? 

A més, una cosa que no habia dit encara, quan clico "reiniciar" tampoc no es veu el menú de reinici (realment apareix en un fons obscur il·legible) i he de parar amb l'interruptor i arrancar de nou.

---

### Post by albandy on 2012-10-15
Si vols podem intentar fer funcionat el cd normal. 

El problema exactament quin és: que no veus ni el menu d'arrencada on et deixa seleccionar l'idioma o que un cop seleccionat l'idioma i comença la carrega ja no es veu res?

---

### Post by jinglada on 2012-10-15
> **albandy said:**
> Si vols podem intentar fer funcionat el cd normal. 

El problema exactament quin és: que no veus ni el menu d'arrencada on et deixa seleccionar l'idioma o que un cop seleccionat l'idioma i comença la carrega ja no es veu res?

Gràcies pel teu ajut, albandy!

1) Amb el CD del 12.04 LTS no es veu "ni el menu d'arrencada on et deixa seleccionar l'idioma" (el menú dels idiomes es veu en un fons obscur il·legible)

-----> Llavors vaig provar de fer la instal.lació amb el WUBI <-----

2) Amb el Wubi, quan vaig reiniciar -perquè la instal·lació ho demanava-,  el menú es veia en un fons obscur il·legible.

----> Llavors va ser quan em vas dir que fes servir l'alternate <----

Vaig desinstal·lar l'Ubuntu des del "Panel de control" del Windows i ...

3) Amb el CD de l'ALTERNATE vaig aconseguir instal·lar l'Ubuntu 12.04 LTS pero quan he de reiniciar per una actualització de programari torna aquedar tot en un fons obscur il·legible. Llavors he d'apagar amb l'interruptor i arrancar de nou.

---

### Post by albandy on 2012-10-15
> **jinglada said:**
> Gràcies pel teu ajut, albandy!

1) Amb el CD del 12.04 LTS no es veu "ni el menu d'arrencada on et deixa seleccionar l'idioma" (el menú dels idiomes es veu en un fons obscur il·legible)

-----> Llavors vaig provar de fer la instal.lació amb el WUBI <-----

2) Amb el Wubi, quan vaig reiniciar -perquè la instal·lació ho demanava-,  el menú es veia en un fons obscur il·legible.

----> Llavors va ser quan em vas dir que fes servir l'alternate <----

Vaig desinstal·lar l'Ubuntu des del "Panel de control" del Windows i ...

3) Amb el CD de l'ALTERNATE vaig aconseguir instal·lar l'Ubuntu 12.04 LTS pero quan he de reiniciar per una actualització de programari torna aquedar tot en un fons obscur il·legible. Llavors he d'apagar amb l'interruptor i arrancar de nou.

Tinc un portatil HP que te un problema similar. Prova això:

Posa el cd normal de l'ubuntu.
Deixa'l arrencar automàticament, tardarà una estona (per anar sobre segur calcula 5 minuts).
A les hores, pulsa el botó per apujar la brillantor de la pantalla (normalment tecla fn+ el símbol d'una bombeta que brilla)

Si et funciona, solucionar que es vegi bé és bastant fàcil, un cop instal·lat s'han d'afegir un paràmetre al grub.

---

### Post by jinglada on 2012-10-15
> **albandy said:**
> Tinc un portatil HP que te un problema similar. Prova això:

Posa el cd normal de l'ubuntu.
Deixa'l arrencar automàticament, tardarà una estona (per anar sobre segur calcula 5 minuts).
A les hores, pulsa el botó per apujar la brillantor de la pantalla (normalment tecla fn+ el símbol d'una bombeta que brilla)

Si et funciona, solucionar que es vegi bé és bastant fàcil, un cop instal·lat s'han d'afegir un paràmetre al grub.

De fet en un dels intents d'instal·lació del "normal" vaig haver de deixar un moment l'ordinador mentre es carregava el CD i quan vaig tornar es veia el menu per a escollir de provar l'Ubuntu sense instal·lar-lo o instal·lar-lo directament. Vaig provar-lo sense instal·lar i vaig parar. 

Ara l'he engegat amb el CD del "normal" i porto 10 minuts veient el menú en el fons obscur il·legible. Premo Fn + F12 (augmentar la brillantor) i no canvia res.

De tota manera si em vols donar el paràmetre per al grub, ho provaré per veure si soluciono el punt 3) de quan reinicio l'alternate que hi tinc instal·lat.

============================================

Una pregunta a part: El tema del Windows i del recovery del Windows, no podria ser que no funcionés pel fet de que quan s'instal·la l'Ubuntu reconverteix les particions del Windows de FAT a NTFS? O és que estic mal fixat amb això de les particions HPFS/NTFS/exFAT?

---

### Post by albandy on 2012-10-16
> **jinglada said:**
> De fet en un dels intents d'instal·lació del "normal" vaig haver de deixar un moment l'ordinador mentre es carregava el CD i quan vaig tornar es veia el menu per a escollir de provar l'Ubuntu sense instal·lar-lo o instal·lar-lo directament. Vaig provar-lo sense instal·lar i vaig parar. 

Ara l'he engegat amb el CD del "normal" i porto 10 minuts veient el menú en el fons obscur il·legible. Premo Fn + F12 (augmentar la brillantor) i no canvia res.

De tota manera si em vols donar el paràmetre per al grub, ho provaré per veure si soluciono el punt 3) de quan reinicio l'alternate que hi tinc instal·lat.

============================================

Una pregunta a part: El tema del Windows i del recovery del Windows, no podria ser que no funcionés pel fet de que quan s'instal·la l'Ubuntu reconverteix les particions del Windows de FAT a NTFS? O és que estic mal fixat amb això de les particions HPFS/NTFS/exFAT?


backlight=vendor acpi_osi=linux

---

### Post by jinglada on 2012-10-16
> **albandy said:**
> backlight=vendor acpi_osi=linux

L'he posat al final del fitxer grub.cfg i ha funcionat en el "REINICIA" però no en l'"Atura temporalment"

---

### Post by albandy on 2012-10-17
> **jinglada said:**
> L'he posat al final del fitxer grub.cfg i ha funcionat en el "REINICIA" però no en l'"Atura temporalment"

un cop instal·lat posa'l al /etc/default/grub a la mateixa linia del splash, després has de  fer:

sudo update-grub
sudo grub-install /dev/sda

Ja que si el fiques al grub.cfg quan hi hagi una actualització del grub o inclús del kernel desapareixerà.

Que no es vegi després de realitzar la suspensió es un tema que s'hauria de tractar en un nou fil.

---

### Post by jinglada on 2012-10-17
> **albandy said:**
> un cop instal·lat posa'l al /etc/default/grub a la mateixa linia del splash, després has de  fer:

sudo update-grub
sudo grub-install /dev/sda

Ja que si el fiques al grub.cfg quan hi hagi una actualització del grub o inclús del kernel desapareixerà.

Que no es vegi després de realitzar la suspensió es un tema que s'hauria de tractar en un nou fil.

Gràcies albandy. Obro un nou fil i poso SOLVED en aquest.

---

