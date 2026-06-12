---
title: "[SOLVED] problema en server con cdrecord"
date: 2008-05-16
forum: Argentina Team
---

### Post by sergiom99 on 2008-05-16
Hola gente, tengo un problemon con script de backup en un server. no puedo hacer que grabe el CD-RW.
El script es asi:
```
#!/bin/bash
#Uso: burn_cd.sh directorio etiqueta
#

# cdrecord dev=ATAPI: -scanbus
CDRECORD_DEV="ATA:1,0,0"

/usr/bin/cdrecord dev=$CDRECORD_DEV blank=fast

IMG_SIZE='/usr/bin/mkisofs -J -R -V $2 -q -print-size $1 2>&1 | \
          sed -e "s/.* = //"'
echo $IMG_SIZE [ "0$IMG_SIZE" -ne 0 ] && /usr/bin/mkisofs -J -R -V $2 $1 | \
  /usr/bin/cdrecord dev=$CDRECORD_DEV fs=30m tsize=${IMG_SIZE}s -data -

```
En otros equipos funciona perfecto, y en este mismo, cuando le hago grabar un solo archivito tambien.
Pero cuando quiero grabar un dir, con mas contenido adentro, tira este error:
> [root@totem-conplas ~]# ./burn_cd.sh /backup/backup_2008-05-15 backapeo
Cdrecord-Clone 2.01-dvd (i686-pc-linux-gnu) Copyright (C) 1995-2004 JÃ¶rg Schilling
Note: This version is an unofficial (modified) version with DVD support
Note: and therefore may have bugs that are not present in the original.
Note: Please send bug reports or support requests to [http://bugzilla.redhat.com/bugzilla](http://bugzilla.redhat.com/bugzilla)
Note: The author of cdrecord should not be bothered with problems in this version.
scsidev: 'ATA:1,0,0'
devname: 'ATA'
scsibus: 1 target: 0 lun: 0
Linux sg driver version: 3.5.27
Using libscg version 'schily-0.8'.
/usr/bin/cdrecord: Warning: using inofficial libscg transport code version (schily - Red Hat-scsi-linux-sg.c-1.83-RH '@(#)scsi-linux-sg.c        1.83 04/05/20 Copyright 1997 J. Schilling').
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   :
Vendor_info    : 'HL-DT-ST'
Identifikation : 'CD-RW GCE-8527B '
Revision       : '1.04'
Device seems to be: Generic mmc CD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO BURNFREE
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Speed set to 705 KB/s
Starting to write CD/DVD at speed   4.0 in real BLANK mode for single session.
Last chance to quit, starting real write    0 seconds. Operation starts.
/usr/bin/mkisofs -J -R -V $2 -q -print-size $1 2>&1 | \ sed -e "s/.* = //" [ 0/usr/bin/mkisofs -J -R -V $2 -q -print-size $1 2>&1 | \
          sed -e "s/.* = //" -ne 0 ]
INFO:   UTF-8 character encoding detected by locale settings.
        Assuming UTF-8 encoded filenames on source filesystem,
        use -input-charset to override.
/usr/bin/cdrecord: Bad Option: tsize=/usr/bin/mkisofs.
Usage: /usr/bin/cdrecord [options] track1...trackn

Use     /usr/bin/cdrecord -help
to get a list of valid options.

Use     /usr/bin/cdrecord blank=help
to get a list of valid blanking options.

Use     /usr/bin/cdrecord dev=b,t,l driveropts=help -checkdrive
to get a list of drive specific options.

Use     /usr/bin/cdrecord dev=help
to get a list of possible SCSI transport specifiers.
Unknown file type (unallocated) /backup/backup_2008-05-15/.. - ignoring and continuing.
Using PGSQL000.BZ2;1 for  /backup/backup_2008-05-15/pgsql-data-totem-conplas-2008-05-15/pgsql-data-totem-conplas-2008-05-15_16-21-41.tar.bz2 (pgsql-data-totem-conplas-2008-05-15_23-00-01.tar.bz2)
Using PGSQL001.BZ2;1 for  /backup/backup_2008-05-15/pgsql-data-totem-conplas-2008-05-15/pgsql-data-totem-conplas-2008-05-15_23-00-01.tar.bz2 (pgsql-data-totem-conplas-2008-05-15_16-45-03.tar.bz2)
Using TOTEM000.GZ;1 for  /backup/backup_2008-05-15/pgsql-totem-conplas-2008-05-15/totem-conplas-pgsql-nkdatos-callejero-2008-05-15_16-21-41.sql.gz (totem-conplas-pgsql-nkdatos-totem-2008-05-15_16-21-41.sql.gz)
Using TOTEM001.GZ;1 for  /backup/backup_2008-05-15/pgsql-totem-conplas-2008-05-15/totem-conplas-pgsql-nkdatos-totem-2008-05-15_16-21-41.sql.gz (totem-conplas-pgsql-nkdatos-totem-2008-05-15_16-45-03.sql.gz)
Using TOTEM002.GZ;1 for  /backup/backup_2008-05-15/pgsql-totem-conplas-2008-05-15/totem-conplas-pgsql-nkdatos-totem-2008-05-15_16-45-03.sql.gz (totem-conplas-pgsql-nkdatos-totem-2008-05-15_23-00-01.sql.gz)
Using TOTEM003.GZ;1 for  /backup/backup_2008-05-15/pgsql-totem-conplas-2008-05-15/totem-conplas-pgsql-nkdatos-totem-2008-05-15_23-00-01.sql.gz (totem-conplas-pgsql-nkdatos-callejero-2008-05-15_16-45-03.sql.gz)
Using TOTEM004.GZ;1 for  /backup/backup_2008-05-15/pgsql-totem-conplas-2008-05-15/totem-conplas-pgsql-nkdatos-callejero-2008-05-15_16-45-03.sql.gz (totem-conplas-pgsql-nkdatos-callejero-2008-05-15_23-00-01.sql.gz)
Using TOTEM000.TGZ;1 for  /backup/backup_2008-05-15/sys-totem-conplas-2008-05-15/totem-conplas-netkey-2008-05-15.tar.gz (totem-conplas-smb-2008-05-15.tar.gz)
Using TOTEM001.TGZ;1 for  /backup/backup_2008-05-15/sys-totem-conplas-2008-05-15/totem-conplas-smb-2008-05-15.tar.gz (totem-conplas-named-2008-05-15.tar.gz)
Using TOTEM002.TGZ;1 for  /backup/backup_2008-05-15/sys-totem-conplas-2008-05-15/totem-conplas-named-2008-05-15.tar.gz (totem-conplas-recomended-2008-05-15.tar.gz)
Using TOTEM003.TGZ;1 for  /backup/backup_2008-05-15/sys-totem-conplas-2008-05-15/totem-conplas-recomended-2008-05-15.tar.gz (totem-conplas-etc-2008-05-15.tar.gz)


ya probe de borrar y reinstalar mkisofs y cdrecord. No tengo entorno grafico.

Gracias por cualquier tip

---

### Post by sergiom99 on 2008-05-16
despues de buscar por todos lados y mirar mil veces el script y la salida, modifique esta linea para que no de bola al mensaje de unknown...
y quedo asi y funciona perfecto.

IMG_SIZE=`/usr/bin/mkisofs -J -r -V $2 -q -print-size $1 2>&1 | \
          sed -e "s/.* = //" | grep -v Unknown`

Espero a alguien le sirva.

---

