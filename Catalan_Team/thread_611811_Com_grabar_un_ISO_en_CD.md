---
title: "Com grabar un ISO en CD"
date: 2007-11-13
forum: Catalan Team
---

### Post by jaume69 on 2007-11-13
Hola,de nou(senso obrir un altre post),però és que no he trobat res als fòrums.
Estic a Gnome i em baixo alguna distrib. d'Ubuntu i la deixo a Tmp o Home.
Llavors,ho he intentat amb Serpentine i GnomeBaker per gravar la imatge ISO,però no hi ha hagut maneres de poder..
Recordo fe temps que vaig fer un disc ISO amb Serpentine posant-li Feisty i em va anar bé.
Ara quan ho faig amb GnomeBaker al principi em demana si vull inclure el fitxer de Imatge que ve a dins,i jo tan si li poso si com no,no m'ho graba bé.
Quan poso al disc grabat per iniciar em surt la pamtalla d'opcions però queda enganxat quan li dones a Iniciar o Ínstal.lar.

Penso que no sigui problema de l'Unitat Lectora.:confused:
Es pot combrobar si està en bon estat?(Per grabació)
Merci.

---

### Post by kukat on 2007-11-13
Has provat amb el programa k3b? Per a mi és molt semblant a Nero, igual des d'aquest programa es funciona bé. 

Tan sols: sudo apt-get install k3b en la consola, i després pots seguir els pasos d'aquesta web (en castellà)
[http://www.angelfire.com/linux/gatolinux/public/spanish/manuales/GrabarISOconK3B.html](http://www.angelfire.com/linux/gatolinux/public/spanish/manuales/GrabarISOconK3B.html)

---

### Post by CarlesOriol on 2007-11-13
Des del mateix gnome butó de la dreta del ratolí sobre la iso i escriure al disc.

---

### Post by jodufi on 2007-11-13
A  mi em va genial el Brasero. Potser no és tant complet com el K3B, però per gravar una imatge o arxius n'hi de sobre, i no has de carregar totes les llibreries QT.

Salut

---

### Post by jaume69 on 2007-11-14
No sé,la veritat que no sé on està el problema...,pot ser que allà on ho vull gravar ha sigut prèviament esborrat amb el GnomeBaker ?
CD de dades i Imatge ISO deu ser el mateix a l'hora de grabar,crec.
:confused:

---

### Post by papapep on 2007-11-14
No, un cd de dades no és el mateix que gravar una ISO.

T'adjunto un volcat de pantalla per que vegis on tens la opció al GnomeBaker.

---

### Post by jaume69 on 2007-11-15
Ho he gravat i quan reinicio em surt la pantalla inicial pero queda bloquejat al,Iniciar o Instal.lar.

Mode gravació: (Imatge Iso)
[IMG]http://godlike.cl/up/im/25/pantalvwwo.png[/IMG]

Sortida GnomeBaker,final gravació:

wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/sr0'
devname: '/dev/sr0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 3 = CD-ROM XA mode 2
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'TSSTcorp'
Identification : 'CD/DVDW TS-L632D'
Revision       : 'ac00'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x000A (CD-RW)
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0012 (DVD-RAM) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) (current)
Profile: 0x0009 (CD-R) 
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1306624 = 1276 KB
FIFO size      : 12582912 = 12288 KB
Speed set to 1764 KB/s
   4 seconds.   3 seconds.   2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Starting new track at sector: 0
Writing  time:  490.227s
Average write speed   9.9x.
Min drive buffer fill was 98%
Fixating...
Fixating time:   35.658s
wodim: fifo had 11516 puts and 11516 gets.
BURN-Free was never needed.
wodim: fifo was 0 times empty and 11304 times full, min fill was 94%.
:confused:

---

### Post by papapep on 2007-11-15
> Ho he gravat i quan reinicio em surt la pantalla inicial pero queda bloquejat al,Iniciar o Instal.lar.

Això ja és tema d'un fil nou. Aquest anava sobre gravar iso's a cd.

---

### Post by jaume69 on 2007-12-04
Doncs el problema ja **està resolt!!**!,encara que sembli imposible..
Tot venia del CDs que utilitzo,CD-RW,suposo que aquests CDs(es pot dir la marca?) només soporten una o un parell de regravacions perquè si graves i el borres és posible que et quedi **fragmentat**.Pot ser a la segona regravació o tercera és on deu ser més perillós.No sé..
Jo normalment els grabo un o dos cops.
:)

---

### Post by CarlesOriol on 2007-12-06
> **jaume69 said:**
> 
1. CD-RW,suposo que aquests CDs(es pot dir la marca?) només soporten una o un parell de regravacions
2.  perquè si graves i el borres és posible que et quedi **fragmentat**.
:)

1. Improbable. Tot i que poden ser consumibles de molt baixa qualitat 2 gravacions per un cd-rw, que no hagis esborrat amb paper de vidre, seria un producte clarament defectuos.

2. Impossible. La fragmentació es pot produir quan hi ha escriptures acumulatives en diversos sistemes d'arxius. En un volcat d'una iso o un enregistrament normal amb l'ubuntu (excepte si uses udf -però em sembla que cal recompilar el kernel per suportar-ho) no es pot produir MAI fragmentació.
[INDENT]
T'explico:

tenim dos arxius a(10) i b(5) i els enregistrem

aaaaaaaaaabbbbb

ara si tinguessim un sistema d'escriptura acumulatiu i ampliessim la mida d'a a 15 podria quedar:

aaaaaaaaabbbbbaaaaa (a partit en dos trossos)

però com que al escriure un CD reenregistrable ho esborrem tot (insisteixo que sempre que no usem un sistema de paquets) ens quedarà SEMPRE:

aaaaaaaaaaaaaaaabbbbb

Això que comentes et pot passar amb el windows vista i és absolutament fantàstic veure el temps que pot arribar a trigar en llegir un arxiu del cd.


 
[/INDENT]

---

### Post by jaume69 on 2007-12-06
Jo dic el que me va dir **Brasero** a la sortida de la gravació.

Vaig mirar amb un programa que no recordo ara,comprovar el meu** HD** i em sembla que em va dir que no tenia cap problema,ho dic que no fos cas que l'error vingés d'aquí.
Doncs el problema pot venir que no borra bé les dades.
Aquests CD-RW (**Philips**) tenen 1 o 2 anys..?¿,no recordo.

El que si et puc asegurar és que amb un CD d'aquests verge,he pogut** GRAVAR** un parell d'Isos!! i han quedat bé.

---

