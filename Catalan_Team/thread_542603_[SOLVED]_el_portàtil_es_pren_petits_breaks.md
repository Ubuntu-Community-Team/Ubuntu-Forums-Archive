---
title: "[SOLVED] el portàtil es pren petits breaks"
date: 2007-09-04
forum: Catalan Team
---

### Post by guillemsola on 2007-09-04
Des de fa uns dies el portàtil amb fesity es queda penjat durant mig minut a estones. És allò que t'obliga a anar fent parades no fos cas que em cansés! Per molt que ell insisteixi és una mica molest pq quant hi estic posat em fot molt anar parant, m'oblido del que feia....

En fi, al que anava. No sé perquè ho fa.  Però cada vegada que em passa apareix tot això al dmesg. Enteneu alguna cosa per tenir una pista del que passa?
pren petites parades

> [ 1006.168000] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 1006.168000] ata1.01: cmd a0/01:00:00:00:00/00:00:00:00:00/b0 tag 0 cdb 0x43 data 12 in
[ 1006.168000]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[ 1013.168000] ata1: port is slow to respond, please be patient (Status 0xd0)
[ 1036.184000] ata1: port failed to respond (30 secs, Status 0xd0)
[ 1036.184000] ata1: soft resetting port
[ 1036.584000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[ 1036.592000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[ 1036.592000] ata1.00: configured for UDMA/100
[ 1036.772000] ata1.01: configured for UDMA/33
[ 1036.772000] ata1: EH complete
[ 1036.780000] SCSI device sda: 195371568 512-byte hdwr sectors (100030 MB)
[ 1036.788000] sda: Write Protect is off
[ 1036.788000] sda: Mode Sense: 00 3a 00 00
[ 1036.804000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1036.812000] SCSI device sda: 195371568 512-byte hdwr sectors (100030 MB)
[ 1036.812000] sda: Write Protect is off
[ 1036.812000] sda: Mode Sense: 00 3a 00 00
[ 1036.816000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA

---

### Post by RaZer0r on 2007-09-04
and in english this would be?

---

### Post by papapep on 2007-09-04
> and in english this would be?

It would be in another fòrum, as this is the catalan speakers one ;-)

**angrychai** explains that his laptop takes small breaks every one and then, and shows the dmesg output that shows the messages from when that happens.

---

### Post by RaZer0r on 2007-09-04
sorry i noticed to late :) 
I was just answering unanswerd posts, so i didn't notice in which forum i was :)

catalan is some sort of spanish right? (If i remember correct from high school :p)

---

### Post by CarlesOriol on 2007-09-04
Entenent que tens un disc dur SATA i un CD a ATA pot ser que el cd que tinguis al lector tingui problemes.

En qualsevol cas pot veure que el dispositiu que hi ha al cable 'ATA està donant un error.

---

### Post by CarlesOriol on 2007-09-04
> **RaZer0r said:**
> sorry i noticed to late :) 
I was just answering unanswerd posts, so i didn't notice in which forum i was :)

catalan is some sort of spanish right? [-X (If i remember correct from high school :p)

Not at all.

Catalan it's a latin language like french, italian or spanish spoken by near 10 milion people in spain, france, andorra and italy.

If you like you can get more information about catalan at [http://en.wikipedia.org/wiki/Catalan_language](http://en.wikipedia.org/wiki/Catalan_language) and information about catalan countries at [http://en.wikipedia.org/wiki/Catalan_countries](http://en.wikipedia.org/wiki/Catalan_countries).

---

### Post by guillemsola on 2007-09-04
Doncs de moment ja has entès més que jo que veia que alguna cosa tenia a veure amb el disc però no he rascat gaire.

Havia desactivat les entrades que tenia amb 3g-ntfs per que era lo nou i sospitós.

Ara posaré # a la línia del cdrom a fstab per desavilitar -lo. Solucionaré temporalment el problema no dient-li al sistema que munti el cdrom? Si no us ho diré jo provant-ho.

> Fstab:
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

Però quin deu ser el problema real? Al disc no hi ha cap disc.

gràcies

---

### Post by guillemsola on 2007-09-04
He reiniciat l'ubuntu sense cdrom a fstab i sorpresa. Des de la consola no hi ha res muntat però el nautilus encara és capaç de navegar pel cd.

Qui serà el culpable d'aquests accessos que pausen el sistema?

SaluT!

---

### Post by CarlesOriol on 2007-09-04
ha de ser un disc o dispositiu ata. Sembla evidentment un error físic a un disc .

No son pauses per que alguna cosa accedeixi al dispositiu.

Mira:

[ 1013.168000] ata1: port is slow to respond, please be patient (Status 0xd0)
[ 1036.184000] ata1: port failed to respond (30 secs, Status 0xd0)

---

### Post by guillemsola on 2007-09-04
Vaja, he estat buscant una mica d'informació i m'ha semblat entendre que els problemes podrien derivar d'un error en el dispositiu o d'un kernel de linux amb alguna incompatibilitat. Però no n'he tret l'aigua clara.

Des que he desactivat el cdrom sembla que es comporta millor però que digui ata1 vol dir que és el cdrom? Ho dic pq fent **hdparm -I /dev/sda** fa referencia a ATA. No se em semblaria més lògic un problema amb el disc dur que amb un cdrom que buit que no faig servir.

> 
ATA device, with non-removable media
        Model Number:       ST9100825A                              
        Serial Number:      3PL0HY4Q
        Firmware Revision:  3.04    
[B]Standards:
        Used: ATA/ATAPI-6 T13 1410D revision 2 
        Supported: 6 5 4 
[/B]Configuration:
        Logical         max     current
        cylinders       16383   16383
        heads           16      16
        sectors/track   63      63
        --
        CHS current addressable sectors:   16514064
        LBA    user addressable sectors:  195371568
        LBA48  user addressable sectors:  195371568
        device size with M = 1024*1024:       95396 MBytes
        device size with M = 1000*1000:      100030 MBytes (100 GB)
Capabilities:
        LBA, IORDY(can be disabled)
        Standby timer values: spec'd by Standard, no device specific minimum
        R/W multiple sector transfer: Max = 16  Current = 16
        Advanced power management level: unknown setting (0x8080)
        Recommended acoustic management value: 254, current value: 0
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5 
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4 
             Cycle time: no flow control=240ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
           *    SMART feature set
                Security Mode feature set
           *    Power Management feature set
           *    Write cache
           *    Look-ahead
           *    Host Protected Area feature set
           *    WRITE_BUFFER command
           *    READ_BUFFER command
           *    DOWNLOAD_MICROCODE
           *    Advanced Power Management feature set
                SET_MAX security extension
           *    48-bit Address feature set
           *    Device Configuration Overlay feature set
           *    Mandatory FLUSH_CACHE
           *    FLUSH_CACHE_EXT
           *    SMART error logging
           *    SMART self-test
           *    IDLE_IMMEDIATE with UNLOAD
           *    SMART Command Transport (SCT) feature set
Security: 
        Master password revision code = 65534
                supported
        not     enabled
        not     locked
        not     frozen
        not     expired: security count
        not     supported: enhanced erase
HW reset results:
        CBLID- above Vih
        Device num = 0 determined by CSEL
Checksum: correct

SaluT!

---

### Post by papapep on 2007-09-04
Tal i com tu dius, [les referències que hi ha a internet]("http://tinyurl.com/356q6w") no parlen d'errors físics de disc sinó de problemes en la configuració d'accés als mateixos.

Seria necessari saber quina marca i model d'ordinador tens (el disc ja el sabem pel **model number** del dmesg), ja que veig que hi ha vàries sol·lucions (o això diuen) però hi ha gent a qui li funcionen i gent a qui no.

---

### Post by guillemsola on 2007-09-06
Bé senyors, el problema té tela.  Després de llegir tota lo documentació del launchpad resulta que hi ha un lector de DVD maleït i sí, aquest és el meu. un fantàstic TS-L632D_SC01 que munten a alguns portàtils.

Una solució molt divertida és deixar un disc a dins de la unitat. Desapareix el problema.

L'altre ha estat actualitzar el firmware del DVD. M'ha costat una mica perquè com sempre els fabricans no donen suport als problemes de Linux. 

El portàtil és un ASUS A6JC i a la web del fabricant si ja no trobem updates dels drivers de M$ no parlem dels de linux!

En fi agrair-os a tots l'ajuda perquè no sabia per on començar. I ja només em resta demanar que em poseu un SOLVED ben gros!!!

SalutT!!!

---

### Post by papapep on 2007-09-06
Fet!! Enhorabona pel teu èxit ;-)

---

