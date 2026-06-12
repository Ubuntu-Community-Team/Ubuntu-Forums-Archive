---
title: "portàtil samsung x05"
date: 2010-08-14
forum: Catalan Team
---

### Post by jinglada on 2010-08-14
Hola ubunterus:
Necessito utilitzar aquest portàtil, una mica antic, només per a consultes a la xarxa i jugar a escacs i poca cosa més.
Tenia a mà l'Ubuntu 8.04.1 (hardy), l'he instal·lat i va de conya però només s'atura apretant uns segons el botó d'arrancada.
He baixat el Lucid Linx i he fet un CD d'arrancada i el comença a carregar encenent i apagant puntets vermells i blancs però tot d'una es queda bloquejat. He provat el mateix CD en el portàtil nou de l'any passat i va perfecte.

Quina versió hauria de posar per aconseguir que rutlli bé?

El HD és de 40 GiB, processador Intel(R) Pentium(R) M processor de 1,6GHz i 500 MiB de RAM

Això següent potser també pot ajudar:

$ lshw -short
WARNING: you should run this program as super-user.
H/W path       Device  Class          Description
=================================================
                       system         Computer
/0                     bus            Motherboard
/0/0                   memory         502MiB System memory
/0/1                   processor      Intel(R) Pentium(R) M processor 1.60GHz
/0/100                 bridge         82852/82855 GM/GME/PM/GMV Processor to I/O
/0/100/0.1             system         82852/82855 GM/GME/PM/GMV Processor to I/O
/0/100/0.3             system         82852/82855 GM/GME/PM/GMV Processor to I/O
/0/100/2               display        82852/855GM Integrated Graphics Device
/0/100/2.1             display        82852/855GM Integrated Graphics Device
/0/100/1d              bus            82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB U
/0/100/1d.1            bus            82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB U
/0/100/1d.2            bus            82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB U
/0/100/1d.7            bus            82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Contro
/0/100/1e              bridge         82801 Mobile PCI Bridge
/0/100/1e/3            bridge         RL5c476 II
/0/100/1e/3.1          bridge         RL5c476 II
/0/100/1e/3.2          bus            R5C552 IEEE 1394 Controller
/0/100/1e/7    eth1    network        PRO/Wireless 2200BG Network Connection
/0/100/1e/8    eth0    network        82801DB PRO/100 VE (MOB) Ethernet Controll
/0/100/1f              bridge         82801DBM (ICH4-M) LPC Interface Bridge
/0/100/1f.1            storage        82801DBM (ICH4-M) IDE Controller
/0/100/1f.3            bus            82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus
/0/100/1f.5            multimedia     82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97
/0/100/1f.6            communication  82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97
--------------------------------------
Necessiteu alguna informació més?

Gràcies a la bestreta.

---

### Post by jinglada on 2010-08-14
> **jinglada said:**
> només s'atura apretant uns segons el botó d'arrancada.

A la línia del kernel del /boot/grub/menu.lst hi tenia:

kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2e7ec378-c230-4caa-a1ea-7ea9b8de7d48 ro quiet splash **acpi=off noapic nolapic pci=noacpi**

perquè hi havia afegit el que està en negreta per aconseguir que el ratolí no anés lent i malament i funcionava bé.

He trobat que per aconseguir que s'aturés havia d'afegir **apm power_off=1** a */etc/modules* i **acpi=force apm=power-off** a la línia del kernel del */boot/grub/menu.lst*

He aconseguit que s'aturés però llavors el ratolí tornava a anar lent i malament.

Al final deixant la línia del kernel com segueix he aconseguit que el ratolí funcioni bé però he de parar fent només una pulsació sobre el botó d'arrencada:

kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2e7ec378-c230-4caa-a1ea-7ea9b8de7d48 ro quiet splash **acpi=force apm=power-off acpi=off noapic nolapic pci=noacpi**

Es pot solucionar o  ho deixo així?

---

### Post by jinglada on 2010-08-14
> **jinglada said:**
> Al final deixant la línia del kernel com segueix he aconseguit que el ratolí funcioni bé però he de parar fent només una pulsació sobre el botó d'arrencada:

kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2e7ec378-c230-4caa-a1ea-7ea9b8de7d48 ro quiet splash **acpi=force apm=power-off acpi=off noapic nolapic pci=noacpi**

Es pot solucionar o  ho deixo així?

Ja ho he trobat; ja funciona el ratolí i s'atura sense haver de prèmer el botó d'arrancada i a més també funciona la suspensió temporal que abans tampoc funcionava. La línia del kernel ha quedat així:

kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2e7ec378-c230-4caa-a1ea-7ea9b8de7d48 ro quiet splash **acpi=force apm=power-off irqpoll pci=usepirqmask**

Ara només queda pendent si algú em pot dir la versió d'Ubuntu més adequada per aquest ordinador.

---

### Post by jinglada on 2010-09-06
> **jinglada said:**
> Ara només queda pendent si algú em pot dir la versió d'Ubuntu més adequada per aquest ordinador.

He mirat els requeriments a [http://ca.wikibooks.org/wiki/Guia_Ubuntu/Requeriments_m%C3%ADnims_de_maquinari](http://ca.wikibooks.org/wiki/Guia_Ubuntu/Requeriments_m%C3%ADnims_de_maquinari) i veig que hi ha ordinador de sobres. 

Llavors em podríeu orientar com esbrinar perquè el CD d'arrancada, del Lucid Linx, el comença a carregar encenent i apagant puntets vermells i blancs però tot d'una bloqueja l'ordinador i he de reiniciar-lo? Tal com vaig dir en el primer missatge, he provat el mateix CD en el portàtil nou de l'any passat i va perfecte.

---

### Post by kukat on 2010-09-06
has provat de fer-ho amb Kubuntu, en lloc de l'Ubuntu normal????

A mi també m'ha donat problemes en alguns ordinadors el Lucid Lynx normal (amb GNOME). Però el CD d'insta&#320;lació.....

Després pots insta&#320;lar el Gnome sense cap problema.


Amb un senzill:

sudo aptitude install ubuntu-desktop

---

### Post by CarlesOriol on 2010-09-08
Has provat d'insta&#320;lar amb la versió alternate?

---

### Post by jinglada on 2010-09-08
> **CarlesOriol said:**
> Has provat d'insta&#320;lar amb la versió alternate?

No en tenia ni idea que existia. És això: [http://releases.ubuntu.com/lucid/ubuntu-10.04.1-alternate-i386.iso](http://releases.ubuntu.com/lucid/ubuntu-10.04.1-alternate-i386.iso) ?

---

### Post by jinglada on 2010-09-08
> **kukat said:**
> has provat de fer-ho amb Kubuntu, en lloc de l'Ubuntu normal????

A mi també m'ha donat problemes en alguns ordinadors el Lucid Lynx normal (amb GNOME). Però el CD d'insta&#320;lació.....

Després pots insta&#320;lar el Gnome sense cap problema.

Després del Kubuntu instal·lo el Gnome, vols dir això?

---

### Post by gunyoles on 2010-09-08
A mi hem passava una cosa semblant amb un **portatil NEC del 1998**, teòricament tenia **RAM de sobres** per gestionar-ho tot, però sempre tancava malament fins que vaig posar el **Lubuntu** que es un dels que menja menys recursos, no es cap marevella pero funciona i he recuperat un ordinador que ja anava ha portar a la deixalleria.

Ves provant distribucions que necessitin menys recursos, sobretot les **Netbook Edition**, fins trobar la que et va be, pots fins i tot arribar a** U-Lite** que es per equips molt antics.

---

### Post by jinglada on 2010-09-10
> **jinglada said:**
> No en tenia ni idea que existia. És això: [http://releases.ubuntu.com/lucid/ubuntu-10.04.1-alternate-i386.iso](http://releases.ubuntu.com/lucid/ubuntu-10.04.1-alternate-i386.iso) ?

He engegat l'actualització del 8.04 al 10.04.1-alternate. 

Ha donat dos errors que m'ha fet reportar i al reinicialitzar-se s'ha parat després de:
Running local boot scripts (/etc/rc.local). [ok]

L'he reinicialitzat amb Alt-PetSis RSEIUB i les opcions que tinc són:
Instal·lar l'Ubuntu
Comprovar si el CD te defectes
Comprovació de la memòria
Arrenca des del primer disc dur
Rescata un sistema no funcional

Si arrenco des del disc dur em dona totes les vegades que ho he provat:

init: ureadahead main process (2491) terminated with status 5
libudev: udeo_monitor_new_from_notlink: error getting socked:
mountall: mountall.c: 3206: assertion failed in main: udeo_monitor_new_from_notlink (udeo, "udeo")
init: mounted main process (2494)killed by ABRT signal
General error mounting filesystem.
A maintenance shell will now be started
CONTROL-D will terminate this shell and reboot the system.
root@pepitu-laptop:~#

faig CONTROL-D, es reinicia i es repeteix el bucle.

Provo 'Rescata un sistema no funcional'?

De les 38,5 GB n'hi ha 9,9 amb dades i 18,2 Free, això vol dir que el que ha instal·lat són 10,1 GB?

Si faig 'Instal·lar l'Ubuntu' pot ser que vagi bé? Perdria les 9,9 GB de dades?

---

### Post by jinglada on 2010-09-11
> **jinglada said:**
> 
Provo 'Rescata un sistema no funcional'?

De les 38,5 GB n'hi ha 9,9 amb dades i 18,2 Free, això vol dir que el que ha instal·lat són 10,1 GB?

Si faig 'Instal·lar l'Ubuntu' pot ser que vagi bé? Perdria les 9,9 GB de dades?

Arrancant amb el CD del 8.04 he pogut copiar les 9,9 GB de dades.

He optat per instal·lar el 10.04.1-alternate i en el grub m'ha donat la possibilitat d'accedir a:

Ubuntu Linux 2.6.32-24 generic
Ubuntu Linux 2.6.32-24 generic recovery
??? x86 ???? memory test
Ubuntu 8.04 generic
Ubuntu 8.04 generic recovery
??? x86 ???? memory test

Ubuntu Linux 2.6.32-24 (suposo que és el 10.04.1-alternate).
Cap dels 4 ha funcionat; el recovery del 10.04.1-alternate m'ha donat la opció de *reparar paquets trencats*, ho he seleccionat i després de molta estona m'ha demanat de reiniciar i tampoc funciona res.

Al final he decidit reinstal·lar el 8.04 i he vist que hi havia 2 particions una de 8,9GB amb el 8.04 i una de 16,5 amb el 10.04.
He sortit i he tornat a provar d'arrancar les dues versions i res de res. 

He escollit usar tot el disc per eliminar tot el que no funcionava i torno a estar funcionant amb el 8.04 després de modificar la línia del kernel del /boot/grub/menu.lst, com indico en el segon missatge, per solucionar els problemes de ratolí i d'aturada de l'ordinador al parar-lo i solucionar els problemes del flash de Firefox amb 
$ sudo aptitude install ubuntu-restricted-extras

---

