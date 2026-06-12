---
title: "Ubuntu Studio 12.04 - no monta DVDROM"
date: 2012-12-16
forum: Catalan Team
---

### Post by venusfenix on 2012-12-16
Buenas,
fa un temps que vaig decidir fer una instal.lació de cero amb el meu portatil Acer Aspire 7520. El resultar ha sigut molt positiu, el habituals problemes de wifi que tenia entre actualitzacions de kernel ha desaparagut, i altres petits inconvenients tambe. no sé, si es auto-suggestió pero formatar els disc durs a EXT4 semblen ser mes rapids, pero en conclusió tot molt positiu, a mes la col.lecio de programes en Studio esta molt ben pensada.
el unic probleme que tinc ara es que no hem reconeix el DVDrom.
hi vaig a l'utilitat de disc i (crec) que hauria de sortir el controlador, i sortir el DVDrom, i res.
he fet en un terminal:
sudo lshw |grep dvd;lshw | grep cd
WARNING: you should run this program as super-user.
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

alguna idea?

gracies,

---

### Post by wgarcia on 2012-12-17
El warning que surt és pel segon lshw que no porta el "sudo" endavant. T'hauria de funcionar sense warning amb:

sudo lshw |grep dvd;sudo lshw | grep cd

Quant al DVD: tens constància que no té problemes de funcionament? Amb un CD o USB autònom (Live), es veu el CD o DVD?

Una altra cosa a mirar: tenir uan terminal oberta, posar un CD o un DVD, entrar la instrucció "dmsg" a la terminal, i mirar les últimes línies a veure si surt algun error per insertar el CD o DVD.

---

### Post by venusfenix on 2012-12-17
sudo lshw |grep dvd;sudo lshw | grep cd

          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3


Respecte a les teves preguntes, abans amb edubuntu tot be, tot correcte, ara amb ubuntu studio, no va res. encara que posi un disc, no surt cap icona, no es munta res.

sobre l'ordre dmesg, he trobat el següent:
[    0.892368] isapnp: No Plug & Play device found
[    0.943048] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    0.944002] ata1.00: ATA-8: Hitachi HTS542516K9SA00, BBCOC31P, max UDMA/133
[    0.944019] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    0.944037] ata2: SATA link down (SStatus 0 SControl 300)
[    0.944052] ata4: SATA link down (SStatus 0 SControl 300)
[    0.944071] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    0.945028] ata3.00: ATA-8: Hitachi HTS542516K9SA00, BBCOC31P, max UDMA/133
[    0.945032] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    0.945193] ata1.00: configured for UDMA/133
[    0.945397] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54251 BBCO PQ: 0 ANSI: 5

no se que mes aportar. pero no he vist res en les ultimes linies....

gracias,

---

### Post by wgarcia on 2012-12-18
Torna a usar sisplau lshw a veure si surt el cd, amb:

```
sudo lshw -C disk; sudo lshw -C drive
```

---

### Post by venusfenix on 2012-12-19
*-disk:0                
       description: ATA Disk
       product: Hitachi HTS54251
       vendor: Hitachi
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: BBCO
       serial: 071028BB0C00WGGTD29C
       size: 149GiB (160GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000368ec
  *-disk:1
       description: ATA Disk
       product: Hitachi HTS54251
       vendor: Hitachi
       physical id: 1
       bus info: scsi@2:0.0.0
       logical name: /dev/sdb
       version: BBCO
       serial: 071028BB0C00WGGT534C
       size: 149GiB (160GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000d2300


he comprovat en la Bios, tampoc surt, es possible que s'hagi espatllat, amb la qual cosa, nomes queda, camviar-la.

gracies,

---

### Post by wgarcia on 2012-12-20
Jo faria una comprovació iniciant el sistema amb un USB si pots per verificar si és un problema de configuració de al teva instal·lació d'Ubuntu o efectivament s'ha espatllat la unitat i s'ha de canviar.

---

### Post by venusfenix on 2012-12-30
buenas,
aixo ja l'he probat i res, no sembla un error de configuracion sino que l'unitat esta espatllada... 

la Bios tampoc ho reconeix.


gracies per l'ajuda.

---

