---
title: "Problemes gravant DVD"
date: 2010-03-10
forum: Catalan Team
---

### Post by Daerun on 2010-03-10
Fa un parell de dies que tinc problemes en gravar DVDs. Va començar la cosa donant-me un error just en acabar el procés de gravar -ho sento, no se'm va acudir en aquell moment de mirar quin missatge donava-; després el disc es gravava, però quan el tornava a insertar, alguns dels fitxers estaven corrumputs.
Avui, directament, el Brasero no em reconeix cap disc on gravar les dades, i només em dóna la possibilitat de crear una imatge .iso :? Fins i tot em vaig instal·lar el K3b, per veure si es que era alguna errada del Brasero, pero els problemes són els mateixos (tampoc em reconeix el disc per gravar, i només em deixa crear una .iso)

---

### Post by wgarcia on 2010-03-12
Suposo que també hauràs provat amb diversos discos, no sigui cosa que el problema sigui un disc fet malbé.

També pots intentar veure si es genera algun error provinent de la unitat, entrant "dmesg" en una terminal i mirant les últimes línies que et mostra, just després d'haver intentat gravar un disc.

---

### Post by Miquel Ubuntero on 2010-03-12
Bones.
Si el programari de gravació, sigui el que sigui, només et grava imatges iso, pot se degut a que no es detecta correctament el dispositiu de gravació de maquinari (o sigui la gravadora cd's).
Amb k3b pot veure si es detecta correctament mirant a: Arranjament - Configura k3b - Dispositius.
Normalment la detecció de maquinari ho fa automàticament. Però crec que també es pot fer manualment.
Sort.

---

### Post by Daerun on 2010-03-13
Molt bé, això és el que em surt després de fallar la gravació amb el K3b:

```
Devices
-----------------------
HL-DT-ST DVDRAM GSA-H42N RL00 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump] [%7]

K3b::IsoImager
-----------------------
mkisofs print size result: 2091334 (4283052032 bytes)

System
-----------------------
K3b Version: 1.68.0
KDE Version: 4.3.2 (KDE 4.3.2)
QT Version:  4.5.2
Kernel:      2.6.31-20-generic

Used versions
-----------------------
mkisofs: 1.1.9
cdrecord: 1.1.9

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/sr0'
devname: '/dev/sr0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.9
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
Errno: 5 (Input/output error), read buffer scsi sendcmd: no error
CDB:  3C 00 00 00 00 00 00 FC 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 04 00 00 00 00 0A C4 F1 01 0E 08 03 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x08 Qual 0x03 (logical unit communication crc error (ultra-dma/32)) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.006s timeout 200s
TOC Type: 1 = CD-ROM
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identification : 'DVDRAM GSA-H42N '
Revision       : 'RL00'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x001B (DVD+R)
Profile: 0x0012 (DVD-RAM) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x001A (DVD+RW) 
Profile: 0x001B (DVD+R) (current)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x0009 (CD-R) 
Profile: 0x000A (CD-RW) 
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc DVD-R(W) driver (mmc_mdvd).
Driver flags   : SWABAUDIO BURNFREE 
Supported modes: PACKET SAO
Drive buf size : 1114112 = 1088 KB
FIFO size      : 12582912 = 12288 KB
Speed set to 24930 KB/s
Track 01: data  4084 MB        
Total size:     4690 MB (464:44.45) = 2091334 sectors
Lout start:     4691 MB (464:46/34) = 2091334 sectors
Current Secsize: 2048
HINT: use dvd+rw-mediainfo from dvd+rw-tools for information extraction.
Blocks total: 2295104 Blocks current: 2295104 Blocks remaining: 203770
Starting to write CD/DVD at speed  20.0 in real SAO mode for single session.
Last chance to quit, starting real write in    2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Sending CUE sheet...
Starting new track at sector: 0
Track 01:    0 of 4084 MB written.
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 00 00 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 04 00 00 00 00 0A 00 00 00 0E 08 03 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x08 Qual 0x03 (logical unit communication crc error (ultra-dma/32)) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.023s timeout 200s
/usr/bin/wodim: A write error occured.
/usr/bin/wodim: Please properly read the error message above.
write track data: error after 0 bytes
Writing  time:   35.914s
Average write speed 111.0x.
Fixating...
Errno: 5 (Input/output error), close track/session scsi sendcmd: no error
CDB:  5B 00 02 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 5B 35 30 0E 72 03 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x72 Qual 0x03 (session fixation error - incomplete track in session) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.808s timeout 1000s
Errno: 5 (Input/output error), flush cache scsi sendcmd: no error
CDB:  35 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 35 72 03 0E A0 80 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0xA0 Qual 0x80 (vendor unique sense code 0xA0) [No matching qualifier] Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.005s timeout 1000s
Trouble flushing the cache
Fixating time:    1.143s
/usr/bin/wodim: fifo had 192 puts and 1 gets.
/usr/bin/wodim: fifo was 0 times empty and 0 times full, min fill was 100%.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/sr0 speed=18 -sao driveropts=burnfree -data -tsize=2091334s -

mkisofs
-----------------------
2091334
I: -input-charset not specified, using utf-8 (detected in locale settings)
Using KENT_BROCKMAN___MISS_SPR000.AVI;1 for  /Kent Brockman - Miss Springfield Junior 2.avi (Kent Brockman - Miss Springfield Junior 1.avi)
  0.02% done, estimate finish Sat Mar 13 13:08:16 2010
  0.05% done, estimate finish Sat Mar 13 12:34:10 2010
  0.07% done, estimate finish Sat Mar 13 12:22:24 2010
  0.10% done, estimate finish Sat Mar 13 12:16:43 2010
  0.12% done, estimate finish Sat Mar 13 12:13:17 2010
  0.14% done, estimate finish Sat Mar 13 12:10:59 2010
  0.17% done, estimate finish Sat Mar 13 12:09:18 2010
  0.19% done, estimate finish Sat Mar 13 12:08:04 2010
  0.22% done, estimate finish Sat Mar 13 12:07:07 2010
  0.24% done, estimate finish Sat Mar 13 12:06:21 2010
  0.26% done, estimate finish Sat Mar 13 12:05:42 2010
  0.29% done, estimate finish Sat Mar 13 12:05:11 2010

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -print-size -quiet -volid Videos Simpsons -volset  -appid K3B THE CD KREATOR (C) 1998-2007 SEBASTIAN TRUEG -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-daerunubuntu/k3bPS5291.tmp -rational-rock -hide-list /tmp/kde-daerunubuntu/k3bGm5291.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-daerunubuntu/k3bNY5291.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 3 -path-list /tmp/kde-daerunubuntu/k3beo5291.tmp

mkisofs command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -volid Videos Simpsons -volset  -appid K3B THE CD KREATOR (C) 1998-2007 SEBASTIAN TRUEG -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-daerunubuntu/k3btn5291.tmp -rational-rock -hide-list /tmp/kde-daerunubuntu/k3bbr5291.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-daerunubuntu/k3bLP5291.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 3 -path-list /tmp/kde-daerunubuntu/k3bDi5291.tmp
```


Això el que em diu el Brasero:

```
Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1848)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI burn:// URI found burn:///Krusty%20-%20Aprovaci%C3%B3n.avi
BraseroBurnURI called brasero_job_set_current_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI Information retrieval for burn:///Krusty%20-%20Aprovaci%C3%B3n.avi
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Krusty - Aprovación.avi at /Krusty - Aprovación.avi
BraseroBurnURI Information retrieval for burn:///Burns%20-%20Donde%20Dejamos%20Estos%20Bidones.ogg
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Burns - Donde Dejamos Estos Bidones.ogg at /Burns - Donde Dejamos Estos Bidones.ogg
BraseroBurnURI Information retrieval for burn:///Alcalde%20Quimby%20-%20A%20lo%20de%20la%20Pasta.ogg
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Alcalde Quimby - A lo de la Pasta.ogg at /Alcalde Quimby - A lo de la Pasta.ogg
BraseroBurnURI Information retrieval for burn:///Bart%20-%20Det%C3%A9nganlo.ogg
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Bart - Deténganlo.ogg at /Bart - Deténganlo.ogg
BraseroBurnURI Information retrieval for burn:///Kent%20Brockman%20-%20Miss%20Springfield%20Junior%201.avi
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Kent Brockman - Miss Springfield Junior 1.avi at /Kent Brockman - Miss Springfield Junior 1.avi
BraseroBurnURI Information retrieval for burn:///Bart%20-%20Con%20Lo%20Larga%20Que%20Es%20la%20Cola.ogg
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Bart - Con Lo Larga Que Es la Cola.ogg at /Bart - Con Lo Larga Que Es la Cola.ogg
BraseroBurnURI Information retrieval for burn:///Homer%20-%20Yogullado.avi
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Homer - Yogullado.avi at /Homer - Yogullado.avi
BraseroBurnURI Information retrieval for burn:///Homer%20-%20Vaaaaya,%20Tiene%20un%20Bicho.ogg
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Homer - Vaaaaya, Tiene un Bicho.ogg at /Homer - Vaaaaya, Tiene un Bicho.ogg
BraseroBurnURI Information retrieval for burn:///Bart%20y%20Lisa%20-%20El%20Juego%20de%20Contar.ogg
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Bart y Lisa - El Juego de Contar.ogg at /Bart y Lisa - El Juego de Contar.ogg
BraseroBurnURI Information retrieval for burn:///Kent%20Brockman%20-%20Fuego.avi
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Kent Brockman - Fuego.avi at /Kent Brockman - Fuego.avi
BraseroBurnURI Information retrieval for burn:///Lionel%20Hutz%20-%20La%20Historia%20Interminable.avi
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Lionel Hutz - La Historia Interminable.avi at /Lionel Hutz - La Historia Interminable.avi
BraseroBurnURI Information retrieval for burn:///Homer%20-%20Vamos%20Tele,%20Dame%20Emociones%20Fuertes%20a%20Porrillo.avi
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Homer - Vamos Tele, Dame Emociones Fuertes a Porrillo.avi at /Homer - Vamos Tele, Dame Emociones Fuertes a Porrillo.avi
BraseroBurnURI Information retrieval for burn:///Krusty%20-%20Olimpiadas%2084.avi
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Krusty - Olimpiadas 84.avi at /Krusty - Olimpiadas 84.avi
BraseroBurnURI Information retrieval for burn:///Homer%20-%20El%20Bocadillo%20de%20Tres%20Metros.ogg
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Homer - El Bocadillo de Tres Metros.ogg at /Homer - El Bocadillo de Tres Metros.ogg
BraseroBurnURI Information retrieval for burn:///Kent%20Brockman%20-%20Rasca%20y%20Pica%20la%20Pel%C3%ADcula.avi
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Kent Brockman - Rasca y Pica la Película.avi at /Kent Brockman - Rasca y Pica la Película.avi
BraseroBurnURI Information retrieval for burn:///Dr%20Nick%20Riviera%20-%20Esa%20Cosa%20Se%20Articula%20Con%20Mi%20Reloj.ogg
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Dr Nick Riviera - Esa Cosa Se Articula Con Mi Reloj.ogg at /Dr Nick Riviera - Esa Cosa Se Articula Con Mi Reloj.ogg
BraseroBurnURI Information retrieval for burn:///Kent%20Brockman%20-%20Krisis%20en%20Kampamento%20Krusty.avi
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Kent Brockman - Krisis en Kampamento Krusty.avi at /Kent Brockman - Krisis en Kampamento Krusty.avi
BraseroBurnURI Information retrieval for burn:///Kent%20Brockman%20-%20Miss%20Springfield%20Junior%202.avi
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Kent Brockman - Miss Springfield Junior 2.avi at /Kent Brockman - Miss Springfield Junior 2.avi
BraseroBurnURI Information retrieval for burn:///Burns%20-%20En%20el%20%C3%9Altimo%20%C3%81rbol%20Cupieron%20Nueve.ogg
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Burns - En el Último Árbol Cupieron Nueve.ogg at /Burns - En el Último Árbol Cupieron Nueve.ogg
BraseroBurnURI Information retrieval for burn:///Selma%20Bouvier%20-%20La%20Cerver%C3%A1mide.ogg
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Selma Bouvier - La Cerverámide.ogg at /Selma Bouvier - La Cerverámide.ogg
BraseroBurnURI Information retrieval for burn:///Homer%20-%20Qu%C3%A9%20Vida%20Me%20Iba%20a%20Dar.avi
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Homer - Qué Vida Me Iba a Dar.avi at /Homer - Qué Vida Me Iba a Dar.avi
BraseroBurnURI Information retrieval for burn:///Bart%20-%20Disruptor%20de%20Neuronas.ogg
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Bart - Disruptor de Neuronas.ogg at /Bart - Disruptor de Neuronas.ogg
BraseroBurnURI Information retrieval for burn:///Rasca%20y%20Pica%20la%20Pel%C3%ADcula.avi
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Rasca y Pica la Película.avi at /Rasca y Pica la Película.avi
BraseroBurnURI Information retrieval for burn:///Krusty%20-%20Es%20Una%20Forma%20de%20Pagar%20Por%20Mis%20Problemas%20Con%20Glu%20Glu,%20Brum%20Brum,%20Zam%20Zam.ogg
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Krusty - Es Una Forma de Pagar Por Mis Problemas Con Glu Glu, Brum Brum, Zam Zam.ogg at /Krusty - Es Una Forma de Pagar Por Mis Problemas Con Glu Glu, Brum Brum, Zam Zam.ogg
BraseroBurnURI Information retrieval for burn:///Dr%20Nick%20Riviera%20-%20La%20B%20Es%20de%20Barato.ogg
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Dr Nick Riviera - La B Es de Barato.ogg at /Dr Nick Riviera - La B Es de Barato.ogg
BraseroBurnURI Information retrieval for burn:///Burns%20-%20Cancele%20el%20Jam%C3%B3n.ogg
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Burns - Cancele el Jamón.ogg at /Burns - Cancele el Jamón.ogg
BraseroBurnURI Information retrieval for burn:///Homer%20-%20Cama%20Arriba,%20Cama%20abajo.ogg
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Homer - Cama Arriba, Cama abajo.ogg at /Homer - Cama Arriba, Cama abajo.ogg
BraseroBurnURI Information retrieval for burn:///Krusty%20-%20La%20Palabra%20Secreta%20es%20Fuerte.avi
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Krusty - La Palabra Secreta es Fuerte.avi at /Krusty - La Palabra Secreta es Fuerte.avi
BraseroBurnURI Information retrieval for burn:///Homer%20-%20Esos%20Dos%20Monos%20Se%20Van%20a%20Matar.avi
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Homer - Esos Dos Monos Se Van a Matar.avi at /Homer - Esos Dos Monos Se Van a Matar.avi
BraseroBurnURI Information retrieval for burn:///Krusty%20-%20Zombi.avi
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Krusty - Zombi.avi at /Krusty - Zombi.avi
BraseroBurnURI Information retrieval for burn:///Skinner%20-%20Ex-Boina%20Verde.avi
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Skinner - Ex-Boina Verde.avi at /Skinner - Ex-Boina Verde.avi
BraseroBurnURI Information retrieval for burn:///Dr%20Nick%20Riviera%20-%20Donde%20Estan%20los%20Cad%C3%A1veres.ogg
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Dr Nick Riviera - Donde Estan los Cadáveres.ogg at /Dr Nick Riviera - Donde Estan los Cadáveres.ogg
BraseroBurnURI Information retrieval for burn:///Instituto%20Lanley%20de%20Conducci%C3%B3n%20de%20Monorail%202.ogg
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Instituto Lanley de Conducción de Monorail 2.ogg at /Instituto Lanley de Conducción de Monorail 2.ogg
BraseroBurnURI Information retrieval for burn:///Kent%20Brockman%20-%20Conductor%20del%20Monorail.ogg
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Kent Brockman - Conductor del Monorail.ogg at /Kent Brockman - Conductor del Monorail.ogg
BraseroBurnURI Information retrieval for burn:///Bart%20-%20Tal%C3%B3n,%20Punta,%20Tal%C3%B3n,%20Punta.avi
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Bart - Talón, Punta, Talón, Punta.avi at /Bart - Talón, Punta, Talón, Punta.avi
BraseroBurnURI Information retrieval for burn:///Skinner%20-%20Madre,%20el%20Traje%20de%20Marinero%20Ya%20No%20Me%20Cabe.ogg
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Skinner - Madre, el Traje de Marinero Ya No Me Cabe.ogg at /Skinner - Madre, el Traje de Marinero Ya No Me Cabe.ogg
BraseroBurnURI Information retrieval for burn:///Homer%20-%20No%20Veo%20Que%20Lisa%20Se%20Queje.ogg
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Homer - No Veo Que Lisa Se Queje.ogg at /Homer - No Veo Que Lisa Se Queje.ogg
BraseroBurnURI Information retrieval for burn:///Kent%20Brockman%20-%20Dejando%20al%20Mando%20al%20Vicepresidente.avi
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Kent Brockman - Dejando al Mando al Vicepresidente.avi at /Kent Brockman - Dejando al Mando al Vicepresidente.avi
BraseroBurnURI Information retrieval for burn:///Krusty%20-%20La%20Familia%20Orejotas.ogg
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Krusty - La Familia Orejotas.ogg at /Krusty - La Familia Orejotas.ogg
BraseroBurnURI Information retrieval for burn:///Burns%20-%20Mi%20Coraz%C3%B3n%20Late%20a%20Ritmo%20de%20Jazz.avi
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Burns - Mi Corazón Late a Ritmo de Jazz.avi at /Burns - Mi Corazón Late a Ritmo de Jazz.avi
BraseroBurnURI Information retrieval for burn:///Instituto%20Lanley%20de%20Conducci%C3%B3n%20de%20Monorail.ogg
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Instituto Lanley de Conducción de Monorail.ogg at /Instituto Lanley de Conducción de Monorail.ogg
BraseroBurnURI Information retrieval for burn:///Homer%20-%20No%20Digas%20Venganza.ogg
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Homer - No Digas Venganza.ogg at /Homer - No Digas Venganza.ogg
BraseroBurnURI Information retrieval for burn:///Rasca%20y%20Pica%20la%20Pel%C3%ADcula%20-%20La%20Cola.avi
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Rasca y Pica la Película - La Cola.avi at /Rasca y Pica la Película - La Cola.avi
BraseroBurnURI Information retrieval for burn:///Homer%20-%20Qu%C3%A9%20Tenemos%20Que%20Decir%20Cuando%20Lleguemos%20a%20la%20Taquilla.ogg
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Homer - Qué Tenemos Que Decir Cuando Lleguemos a la Taquilla.ogg at /Homer - Qué Tenemos Que Decir Cuando Lleguemos a la Taquilla.ogg
BraseroBurnURI Information retrieval for burn:///Homer%20-%20Ui,%20Me%20Ha%20Cambiado%20la%20Voz.ogg
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Homer - Ui, Me Ha Cambiado la Voz.ogg at /Homer - Ui, Me Ha Cambiado la Voz.ogg
BraseroBurnURI Information retrieval for burn:///Alcalde%20Quimby%20-%20A%20ver%20a%20M%C3%AD%20Cuantas%20Titis%20Me%20Tocan.ogg
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Alcalde Quimby - A ver a Mí Cuantas Titis Me Tocan.ogg at /Alcalde Quimby - A ver a Mí Cuantas Titis Me Tocan.ogg
BraseroBurnURI Information retrieval for burn:///Homer%20-%20Callaos%20hipogl%C3%BAcidos.avi
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Homer - Callaos hipoglúcidos.avi at /Homer - Callaos hipoglúcidos.avi
BraseroBurnURI Information retrieval for burn:///Homer%20-%20Otro%20Hermoso%20Dia%20Sin%20Salir%20del%20%C3%9Atero.avi
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Homer - Otro Hermoso Dia Sin Salir del Útero.avi at /Homer - Otro Hermoso Dia Sin Salir del Útero.avi
BraseroBurnURI Information retrieval for burn:///Rasca%20y%20Pica%20-%20Flay%20Me%20to%20the%20Moon.avi
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Rasca y Pica - Flay Me to the Moon.avi at /Rasca y Pica - Flay Me to the Moon.avi
BraseroBurnURI Information retrieval for burn:///Bart%20y%20Homer%20-%20M%C3%A1s%20Alto%20Papa,%20M%C3%A1s%20Alto.ogg
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Bart y Homer - Más Alto Papa, Más Alto.ogg at /Bart y Homer - Más Alto Papa, Más Alto.ogg
BraseroBurnURI Information retrieval for burn:///Bart%20-%20Su%20Primera%20Palabra.avi
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Bart - Su Primera Palabra.avi at /Bart - Su Primera Palabra.avi
BraseroBurnURI Information retrieval for burn:///Homer%20-%20Lo%20Tienen%20en%20Rubio%C2%BF.ogg
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Homer - Lo Tienen en Rubio¿.ogg at /Homer - Lo Tienen en Rubio¿.ogg
BraseroBurnURI Information retrieval for burn:///Barney%20-%20Por%20Que%20pat%C3%A9tico%20Borracho%20Me%20Has%20Tomado.avi
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Barney - Por Que patético Borracho Me Has Tomado.avi at /Barney - Por Que patético Borracho Me Has Tomado.avi
BraseroBurnURI Information retrieval for burn:///Jardines%20Duff%20-%20Duff%20Para%20Tu,%20Duff%20Para%20M%C3%AD.ogg
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Jardines Duff - Duff Para Tu, Duff Para Mí.ogg at /Jardines Duff - Duff Para Tu, Duff Para Mí.ogg
BraseroBurnURI Information retrieval for burn:///Jefe%20Wiggum%20-%20Bad%20Cops%202.ogg
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Jefe Wiggum - Bad Cops 2.ogg at /Jefe Wiggum - Bad Cops 2.ogg
BraseroBurnURI Information retrieval for burn:///Selma%20-%20Heterosexualidad.avi
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Selma - Heterosexualidad.avi at /Selma - Heterosexualidad.avi
BraseroBurnURI Information retrieval for burn:///Jefe%20Wiggum%20-%20Bad%20Cops.ogg
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Jefe Wiggum - Bad Cops.ogg at /Jefe Wiggum - Bad Cops.ogg
BraseroBurnURI Information retrieval for burn:///Rasca%20y%20Pica%20-%20Los%20100%20Metros%20Lisiados.avi
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Rasca y Pica - Los 100 Metros Lisiados.avi at /Rasca y Pica - Los 100 Metros Lisiados.avi
BraseroBurnURI Information retrieval for burn:///Lionel%20Hutz%20-%20Marge%20vs%20Burns.avi
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Lionel Hutz - Marge vs Burns.avi at /Lionel Hutz - Marge vs Burns.avi
BraseroBurnURI Information retrieval for burn:///Homer%20-%20Batman%20es%20Cient%C3%ADfico.ogg
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Homer - Batman es Científico.ogg at /Homer - Batman es Científico.ogg
BraseroBurnURI Information retrieval for burn:///Kent%20Brockman%20-%20Tolomeo.ogg
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Kent Brockman - Tolomeo.ogg at /Kent Brockman - Tolomeo.ogg
BraseroBurnURI Information retrieval for burn:///Dr%20Hibbert%20-%20Pero%20Doctor,%20Si%20Todavia%20No%20Se%20Lo%20He%20Inyectado.ogg
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Dr Hibbert - Pero Doctor, Si Todavia No Se Lo He Inyectado.ogg at /Dr Hibbert - Pero Doctor, Si Todavia No Se Lo He Inyectado.ogg
BraseroBurnURI Information retrieval for burn:///Homer%20-%20Hombre%20Tropieza%20Gracioso.avi
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Homer - Hombre Tropieza Gracioso.avi at /Homer - Hombre Tropieza Gracioso.avi
BraseroBurnURI Information retrieval for burn:///Homer%20-%20Mantel%20Individual.ogg
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Homer - Mantel Individual.ogg at /Homer - Mantel Individual.ogg
BraseroBurnURI Information retrieval for burn:///Jardines%20Duff.ogg
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Jardines Duff.ogg at /Jardines Duff.ogg
BraseroBurnURI Information retrieval for burn:///Bart%20-%20Cervecigafas.ogg
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Bart - Cervecigafas.ogg at /Bart - Cervecigafas.ogg
BraseroBurnURI Information retrieval for burn:///Burns%20-%20Llevo%20la%20Cartera%20en%20el%20Bolsillo%20Derecho.ogg
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Burns - Llevo la Cartera en el Bolsillo Derecho.ogg at /Burns - Llevo la Cartera en el Bolsillo Derecho.ogg
BraseroBurnURI Information retrieval for burn:///Barney%20-%20Banco%20de%20Esperma.ogg
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Barney - Banco de Esperma.ogg at /Barney - Banco de Esperma.ogg
BraseroBurnURI Information retrieval for burn:///Rasca%20y%20Pica%20-%20Gati%20Gati%20Bang%20Bang.ogg
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Rasca y Pica - Gati Gati Bang Bang.ogg at /Rasca y Pica - Gati Gati Bang Bang.ogg
BraseroBurnURI Information retrieval for burn:///Homer%20-%20Pozo%20Sin%20Fondo.avi
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Homer - Pozo Sin Fondo.avi at /Homer - Pozo Sin Fondo.avi
BraseroBurnURI Information retrieval for burn:///Homer%20-%20Voy%20Para%20All%C3%A1.ogg
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Homer - Voy Para Allá.ogg at /Homer - Voy Para Allá.ogg
BraseroBurnURI Information retrieval for burn:///Homer%20-%20Mil%20Dagas%20Ardientes.ogg
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Homer - Mil Dagas Ardientes.ogg at /Homer - Mil Dagas Ardientes.ogg
BraseroBurnURI Information retrieval for burn:///Kent%20Brockman%20-%20Viaje%20Inaugural%20del%20Monorail.ogg
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Kent Brockman - Viaje Inaugural del Monorail.ogg at /Kent Brockman - Viaje Inaugural del Monorail.ogg
BraseroBurnURI Information retrieval for burn:///Homer%20-%20R%20de%20Arriveredchi.avi
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Homer - R de Arriveredchi.avi at /Homer - R de Arriveredchi.avi
BraseroBurnURI Information retrieval for burn:///Marge%20-%20Su%20M%C3%A1quina.avi
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Marge - Su Máquina.avi at /Marge - Su Máquina.avi
BraseroBurnURI Information retrieval for burn:///Lionel%20Hutz%20-%20Testamento%20de%20Gladys%20Bouvier.ogg
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Lionel Hutz - Testamento de Gladys Bouvier.ogg at /Lionel Hutz - Testamento de Gladys Bouvier.ogg
BraseroBurnURI Information retrieval for burn:///Selma%20Bouvier%20y%20Hans%20Topo.ogg
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Selma Bouvier y Hans Topo.ogg at /Selma Bouvier y Hans Topo.ogg
BraseroBurnURI Information retrieval for burn:///Bart%20y%20Homer%20-%20M%C3%A1s%20Alto%20Papa,%20M%C3%A1s%20Alto.mp4
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Bart y Homer - Más Alto Papa, Más Alto.mp4 at /Bart y Homer - Más Alto Papa, Más Alto.mp4
BraseroBurnURI Information retrieval for burn:///Kampamento%20Krusty.avi
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Kampamento Krusty.avi at /Kampamento Krusty.avi
BraseroBurnURI Information retrieval for burn:///Homer%20-%20Inseminaci%C3%B3n%20Artificial.ogg
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Homer - Inseminación Artificial.ogg at /Homer - Inseminación Artificial.ogg
BraseroBurnURI Information retrieval for burn:///Homer%20-%20Perchas,%20Medicinas%20Caducadas%20y%20Peri%C3%B3dicos%20Atrasados.avi
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Homer - Perchas, Medicinas Caducadas y Periódicos Atrasados.avi at /Homer - Perchas, Medicinas Caducadas y Periódicos Atrasados.avi
BraseroBurnURI Information retrieval for burn:///Dr%20Hibbert%20-%20Cancele%20Mi%20Cita%20de%20la%201.ogg
BraseroBurnURI Added file /home/daerunubuntu/kdenlive/Simpson/Dr Hibbert - Cancele Mi Cita de la 1.ogg at /Dr Hibbert - Cancele Mi Cita de la 1.ogg
BraseroBurnURI called brasero_job_add_track
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI Finished track successfully
BraseroBurnURI stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_set_output_size_for_current_track
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack no remote URIs
BraseroLocalTrack stopping
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs getting varg
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_get_flags
BraseroGrowisofs called brasero_job_get_speed
BraseroGrowisofs called brasero_job_get_device
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_session_output_size
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_get_fd_in
BraseroGrowisofs Using genisoimage
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_get_tmp_dir
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs got varg:
	growisofs
	-use-the-force-luke=notray
	-use-the-force-luke=4gms
	-dvd-compat
	-speed=12
	-use-the-force-luke=tty
	-Z
	/dev/sr0
	-dry-run
	-r
	-J
	-input-charset
	utf8
	-graft-points
	-path-list
	/tmp/brasero_tmp_5P2J9U
	-exclude-list
	/tmp/brasero_tmp_AU2J9U
	-print-size
BraseroGrowisofs Launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stdout: Executing 'genisoimage -r -J -input-charset utf8 -graft-points -path-list /tmp/brasero_tmp_5P2J9U -exclude-list /tmp/brasero_tmp_AU2J9U -print-size | builtin_dd of=/dev/sr0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: Using KENT_000.AVI;1 for  /Kent Brockman - Rasca y Pica la Película.avi (Kent Brockman - Dejando al Mando al Vicepresidente.avi)
BraseroGrowisofs stderr: Using HOMER000.AVI;1 for  /Homer - Yogullado.avi (Homer - Perchas, Medicinas Caducadas y Periódicos Atrasados.avi)
BraseroGrowisofs stderr: Using HOMER000.OGG;1 for  /Homer - Qué Tenemos Que Decir Cuando Lleguemos a la Taquill.ogg (Homer - Mil Dagas Ardientes.ogg)
BraseroGrowisofs stderr: Using INSTI000.OGG;1 for  /Instituto Lanley de Conducción de Monorail 2.ogg (Instituto Lanley de Conducción de Monorail.ogg)
BraseroGrowisofs stderr: Using HOMER001.OGG;1 for  /Homer - Mil Dagas Ardientes.ogg (Homer - Lo Tienen en Rubio¿.ogg)
BraseroGrowisofs stderr: Using BURNS000.OGG;1 for  /Burns - Llevo la Cartera en el Bolsillo Derecho.ogg (Burns - Cancele el Jamón.ogg)
BraseroGrowisofs stderr: Using HOMER002.OGG;1 for  /Homer - Lo Tienen en Rubio¿.ogg (Homer - No Veo Que Lisa Se Queje.ogg)
BraseroGrowisofs stderr: Using BURNS001.OGG;1 for  /Burns - Cancele el Jamón.ogg (Burns - En el Último Árbol Cupieron Nueve.ogg)
BraseroGrowisofs stderr: Using BURNS002.OGG;1 for  /Burns - En el Último Árbol Cupieron Nueve.ogg (Burns - Donde Dejamos Estos Bidones.ogg)
BraseroGrowisofs stderr: Using KENT_000.OGG;1 for  /Kent Brockman - Conductor del Monorail.ogg (Kent Brockman - Tolomeo.ogg)
BraseroGrowisofs stderr: Using HOMER001.AVI;1 for  /Homer - Perchas, Medicinas Caducadas y Periódicos Atrasados.avi (Homer - Callaos hipoglúcidos.avi)
BraseroGrowisofs stderr: Using DR_HI000.OGG;1 for  /Dr Hibbert - Cancele Mi Cita de la 1.ogg (Dr Hibbert - Pero Doctor, Si Todavia No Se Lo He Inyectado.ogg)
BraseroGrowisofs stderr: Using HOMER003.OGG;1 for  /Homer - No Veo Que Lisa Se Queje.ogg (Homer - Inseminación Artificial.ogg)
BraseroGrowisofs stderr: Using KENT_001.AVI;1 for  /Kent Brockman - Dejando al Mando al Vicepresidente.avi (Kent Brockman - Miss Springfield Junior 1.avi)
BraseroGrowisofs stderr: Using HOMER002.AVI;1 for  /Homer - Callaos hipoglúcidos.avi (Homer - Esos Dos Monos Se Van a Matar.avi)
BraseroGrowisofs stderr: Using RASCA000.AVI;1 for  /Rasca y Pica la Película - La Cola.avi (Rasca y Pica - Los 100 Metros Lisiados.avi)
BraseroGrowisofs stderr: Using HOMER004.OGG;1 for  /Homer - Inseminación Artificial.ogg (Homer - Vaaaaya, Tiene un Bicho.ogg)
BraseroGrowisofs stderr: Using KENT_002.AVI;1 for  /Kent Brockman - Miss Springfield Junior 1.avi (Kent Brockman - Fuego.avi)
BraseroGrowisofs stderr: Using HOMER005.OGG;1 for  /Homer - Vaaaaya, Tiene un Bicho.ogg (Homer - Mantel Individual.ogg)
BraseroGrowisofs stderr: Using HOMER003.AVI;1 for  /Homer - Esos Dos Monos Se Van a Matar.avi (Homer - Vamos Tele, Dame Emociones Fuertes a Porrillo.avi)
BraseroGrowisofs stderr: Using HOMER006.OGG;1 for  /Homer - Mantel Individual.ogg (Homer - Voy Para Allá.ogg)
BraseroGrowisofs stderr: Using HOMER007.OGG;1 for  /Homer - Voy Para Allá.ogg (Homer - Ui, Me Ha Cambiado la Voz.ogg)
BraseroGrowisofs stderr: Using KENT_003.AVI;1 for  /Kent Brockman - Fuego.avi (Kent Brockman - Miss Springfield Junior 2.avi)
BraseroGrowisofs stderr: Using LIONE000.AVI;1 for  /Lionel Hutz - La Historia Interminable.avi (Lionel Hutz - Marge vs Burns.avi)
BraseroGrowisofs stderr: Using HOMER004.AVI;1 for  /Homer - Vamos Tele, Dame Emociones Fuertes a Porrillo.avi (Homer - Qué Vida Me Iba a Dar.avi)
BraseroGrowisofs stderr: Using HOMER008.OGG;1 for  /Homer - Ui, Me Ha Cambiado la Voz.ogg (Homer - Cama Arriba, Cama abajo.ogg)
BraseroGrowisofs stderr: Using SELMA000.OGG;1 for  /Selma Bouvier - La Cerverámide.ogg (Selma Bouvier y Hans Topo.ogg)
BraseroGrowisofs stderr: Using KRUST000.AVI;1 for  /Krusty - Aprovación.avi (Krusty - Olimpiadas 84.avi)
BraseroGrowisofs stderr: Using RASCA001.AVI;1 for  /Rasca y Pica - Los 100 Metros Lisiados.avi (Rasca y Pica la Película.avi)
BraseroGrowisofs stderr: Using BART_000.OGG;1 for  /Bart - Disruptor de Neuronas.ogg (Bart - Deténganlo.ogg)
BraseroGrowisofs stderr: Using ALCAL000.OGG;1 for  /Alcalde Quimby - A lo de la Pasta.ogg (Alcalde Quimby - A ver a Mí Cuantas Titis Me Tocan.ogg)
BraseroGrowisofs stderr: Using KRUST001.AVI;1 for  /Krusty - Olimpiadas 84.avi (Krusty - La Palabra Secreta es Fuerte.avi)
BraseroGrowisofs stderr: Using HOMER009.OGG;1 for  /Homer - Cama Arriba, Cama abajo.ogg (Homer - Batman es Científico.ogg)
BraseroGrowisofs stderr: Using JEFE_000.OGG;1 for  /Jefe Wiggum - Bad Cops 2.ogg (Jefe Wiggum - Bad Cops.ogg)
BraseroGrowisofs stderr: Using KENT_001.OGG;1 for  /Kent Brockman - Tolomeo.ogg (Kent Brockman - Viaje Inaugural del Monorail.ogg)
BraseroGrowisofs stderr: Using KRUST002.AVI;1 for  /Krusty - La Palabra Secreta es Fuerte.avi (Krusty - Zombi.avi)
BraseroGrowisofs stderr: Using HOMER005.AVI;1 for  /Homer - Qué Vida Me Iba a Dar.avi (Homer - R de Arriveredchi.avi)
BraseroGrowisofs stderr: Using HOMER006.AVI;1 for  /Homer - R de Arriveredchi.avi (Homer - Otro Hermoso Dia Sin Salir del Útero.avi)
BraseroGrowisofs stderr: Using RASCA002.AVI;1 for  /Rasca y Pica la Película.avi (Rasca y Pica - Flay Me to the Moon.avi)
BraseroGrowisofs stderr: Using DR_NI000.OGG;1 for  /Dr Nick Riviera - Donde Estan los Cadáveres.ogg (Dr Nick Riviera - Esa Cosa Se Articula Con Mi Reloj.ogg)
BraseroGrowisofs stderr: Using KENT_004.AVI;1 for  /Kent Brockman - Miss Springfield Junior 2.avi (Kent Brockman - Krisis en Kampamento Krusty.avi)
BraseroGrowisofs stderr: Using DR_NI001.OGG;1 for  /Dr Nick Riviera - Esa Cosa Se Articula Con Mi Reloj.ogg (Dr Nick Riviera - La B Es de Barato.ogg)
BraseroGrowisofs stderr: Using BART_001.OGG;1 for  /Bart - Cervecigafas.ogg (Bart - Con Lo Larga Que Es la Cola.ogg)
BraseroGrowisofs stderr: Using KRUST000.OGG;1 for  /Krusty - Es Una Forma de Pagar Por Mis Problemas Con Glu Glu.ogg (Krusty - La Familia Orejotas.ogg)
BraseroGrowisofs stderr: Using HOMER007.AVI;1 for  /Homer - Otro Hermoso Dia Sin Salir del Útero.avi (Homer - Hombre Tropieza Gracioso.avi)
BraseroGrowisofs stderr: Using HOMER00A.OGG;1 for  /Homer - Batman es Científico.ogg (Homer - No Digas Venganza.ogg)
BraseroGrowisofs stderr: Using HOMER008.AVI;1 for  /Homer - Hombre Tropieza Gracioso.avi (Homer - Pozo Sin Fondo.avi)
BraseroGrowisofs stderr: Using HOMER00B.OGG;1 for  /Homer - No Digas Venganza.ogg (Homer - El Bocadillo de Tres Metros.ogg)
BraseroGrowisofs stderr: Using JARDI000.OGG;1 for  /Jardines Duff.ogg (Jardines Duff - Duff Para Tu, Duff Para Mí.ogg)
BraseroGrowisofs stderr: Total extents scheduled to be written = 2125258
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_output_size_for_current_track
BraseroGrowisofs Finished successfully session
BraseroGrowisofs stopping
BraseroGrowisofs got killed
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs getting varg
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_flags
BraseroGrowisofs called brasero_job_get_speed
BraseroGrowisofs called brasero_job_get_device
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_session_output_size
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_get_fd_in
BraseroGrowisofs Using genisoimage
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_get_tmp_dir
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_data_label
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs got varg:
	growisofs
	-use-the-force-luke=notray
	-use-the-force-luke=4gms
	-dvd-compat
	-speed=12
	-use-the-force-luke=tracksize:2125258
	-use-the-force-luke=tty
	-Z
	/dev/sr0
	-r
	-J
	-input-charset
	utf8
	-graft-points
	-path-list
	/tmp/brasero_tmp_ZE568U
	-exclude-list
	/tmp/brasero_tmp_C7468U
	-A
	Brasero-2.28.2
	-sysid
	LINUX
	-v
BraseroGrowisofs Launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stdout: Executing 'genisoimage -r -J -input-charset utf8 -graft-points -path-list /tmp/brasero_tmp_ZE568U -exclude-list /tmp/brasero_tmp_C7468U -A Brasero-2.28.2 -sysid LINUX -v | builtin_dd of=/dev/sr0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: genisoimage 1.1.9 (Linux)
BraseroGrowisofs stderr: Using KENT_000.AVI;1 for  /Kent Brockman - Rasca y Pica la Película.avi (Kent Brockman - Dejando al Mando al Vicepresidente.avi)
BraseroGrowisofs stderr: Using HOMER000.AVI;1 for  /Homer - Yogullado.avi (Homer - Perchas, Medicinas Caducadas y Periódicos Atrasados.avi)
BraseroGrowisofs stderr: Using HOMER000.OGG;1 for  /Homer - Qué Tenemos Que Decir Cuando Lleguemos a la Taquill.ogg (Homer - Mil Dagas Ardientes.ogg)
BraseroGrowisofs stderr: Using INSTI000.OGG;1 for  /Instituto Lanley de Conducción de Monorail 2.ogg (Instituto Lanley de Conducción de Monorail.ogg)
BraseroGrowisofs stderr: Using HOMER001.OGG;1 for  /Homer - Mil Dagas Ardientes.ogg (Homer - Lo Tienen en Rubio¿.ogg)
BraseroGrowisofs stderr: Using BURNS000.OGG;1 for  /Burns - Llevo la Cartera en el Bolsillo Derecho.ogg (Burns - Cancele el Jamón.ogg)
BraseroGrowisofs stderr: Using HOMER002.OGG;1 for  /Homer - Lo Tienen en Rubio¿.ogg (Homer - No Veo Que Lisa Se Queje.ogg)
BraseroGrowisofs stderr: Using BURNS001.OGG;1 for  /Burns - Cancele el Jamón.ogg (Burns - En el Último Árbol Cupieron Nueve.ogg)
BraseroGrowisofs stderr: Using BURNS002.OGG;1 for  /Burns - En el Último Árbol Cupieron Nueve.ogg (Burns - Donde Dejamos Estos Bidones.ogg)
BraseroGrowisofs stderr: Using KENT_000.OGG;1 for  /Kent Brockman - Conductor del Monorail.ogg (Kent Brockman - Tolomeo.ogg)
BraseroGrowisofs stderr: Using HOMER001.AVI;1 for  /Homer - Perchas, Medicinas Caducadas y Periódicos Atrasados.avi (Homer - Callaos hipoglúcidos.avi)
BraseroGrowisofs stderr: Using DR_HI000.OGG;1 for  /Dr Hibbert - Cancele Mi Cita de la 1.ogg (Dr Hibbert - Pero Doctor, Si Todavia No Se Lo He Inyectado.ogg)
BraseroGrowisofs stderr: Using HOMER003.OGG;1 for  /Homer - No Veo Que Lisa Se Queje.ogg (Homer - Inseminación Artificial.ogg)
BraseroGrowisofs stderr: Using KENT_001.AVI;1 for  /Kent Brockman - Dejando al Mando al Vicepresidente.avi (Kent Brockman - Miss Springfield Junior 1.avi)
BraseroGrowisofs stderr: Using HOMER002.AVI;1 for  /Homer - Callaos hipoglúcidos.avi (Homer - Esos Dos Monos Se Van a Matar.avi)
BraseroGrowisofs stderr: Using RASCA000.AVI;1 for  /Rasca y Pica la Película - La Cola.avi (Rasca y Pica - Los 100 Metros Lisiados.avi)
BraseroGrowisofs stderr: Using HOMER004.OGG;1 for  /Homer - Inseminación Artificial.ogg (Homer - Vaaaaya, Tiene un Bicho.ogg)
BraseroGrowisofs stderr: Using KENT_002.AVI;1 for  /Kent Brockman - Miss Springfield Junior 1.avi (Kent Brockman - Fuego.avi)
BraseroGrowisofs stderr: Using HOMER005.OGG;1 for  /Homer - Vaaaaya, Tiene un Bicho.ogg (Homer - Mantel Individual.ogg)
BraseroGrowisofs stderr: Using HOMER003.AVI;1 for  /Homer - Esos Dos Monos Se Van a Matar.avi (Homer - Vamos Tele, Dame Emociones Fuertes a Porrillo.avi)
BraseroGrowisofs stderr: Using HOMER006.OGG;1 for  /Homer - Mantel Individual.ogg (Homer - Voy Para Allá.ogg)
BraseroGrowisofs stderr: Using HOMER007.OGG;1 for  /Homer - Voy Para Allá.ogg (Homer - Ui, Me Ha Cambiado la Voz.ogg)
BraseroGrowisofs stderr: Using KENT_003.AVI;1 for  /Kent Brockman - Fuego.avi (Kent Brockman - Miss Springfield Junior 2.avi)
BraseroGrowisofs stderr: Using LIONE000.AVI;1 for  /Lionel Hutz - La Historia Interminable.avi (Lionel Hutz - Marge vs Burns.avi)
BraseroGrowisofs stderr: Using HOMER004.AVI;1 for  /Homer - Vamos Tele, Dame Emociones Fuertes a Porrillo.avi (Homer - Qué Vida Me Iba a Dar.avi)
BraseroGrowisofs stderr: Using HOMER008.OGG;1 for  /Homer - Ui, Me Ha Cambiado la Voz.ogg (Homer - Cama Arriba, Cama abajo.ogg)
BraseroGrowisofs stderr: Using SELMA000.OGG;1 for  /Selma Bouvier - La Cerverámide.ogg (Selma Bouvier y Hans Topo.ogg)
BraseroGrowisofs stderr: Using KRUST000.AVI;1 for  /Krusty - Aprovación.avi (Krusty - Olimpiadas 84.avi)
BraseroGrowisofs stderr: Using RASCA001.AVI;1 for  /Rasca y Pica - Los 100 Metros Lisiados.avi (Rasca y Pica la Película.avi)
BraseroGrowisofs stderr: Using BART_000.OGG;1 for  /Bart - Disruptor de Neuronas.ogg (Bart - Deténganlo.ogg)
BraseroGrowisofs stderr: Using ALCAL000.OGG;1 for  /Alcalde Quimby - A lo de la Pasta.ogg (Alcalde Quimby - A ver a Mí Cuantas Titis Me Tocan.ogg)
BraseroGrowisofs stderr: Using KRUST001.AVI;1 for  /Krusty - Olimpiadas 84.avi (Krusty - La Palabra Secreta es Fuerte.avi)
BraseroGrowisofs stderr: Using HOMER009.OGG;1 for  /Homer - Cama Arriba, Cama abajo.ogg (Homer - Batman es Científico.ogg)
BraseroGrowisofs stderr: Using JEFE_000.OGG;1 for  /Jefe Wiggum - Bad Cops 2.ogg (Jefe Wiggum - Bad Cops.ogg)
BraseroGrowisofs stderr: Using KENT_001.OGG;1 for  /Kent Brockman - Tolomeo.ogg (Kent Brockman - Viaje Inaugural del Monorail.ogg)
BraseroGrowisofs stderr: Using KRUST002.AVI;1 for  /Krusty - La Palabra Secreta es Fuerte.avi (Krusty - Zombi.avi)
BraseroGrowisofs stderr: Using HOMER005.AVI;1 for  /Homer - Qué Vida Me Iba a Dar.avi (Homer - R de Arriveredchi.avi)
BraseroGrowisofs stderr: Using HOMER006.AVI;1 for  /Homer - R de Arriveredchi.avi (Homer - Otro Hermoso Dia Sin Salir del Útero.avi)
BraseroGrowisofs stderr: Using RASCA002.AVI;1 for  /Rasca y Pica la Película.avi (Rasca y Pica - Flay Me to the Moon.avi)
BraseroGrowisofs stderr: Using DR_NI000.OGG;1 for  /Dr Nick Riviera - Donde Estan los Cadáveres.ogg (Dr Nick Riviera - Esa Cosa Se Articula Con Mi Reloj.ogg)
BraseroGrowisofs stderr: Using KENT_004.AVI;1 for  /Kent Brockman - Miss Springfield Junior 2.avi (Kent Brockman - Krisis en Kampamento Krusty.avi)
BraseroGrowisofs stderr: Using DR_NI001.OGG;1 for  /Dr Nick Riviera - Esa Cosa Se Articula Con Mi Reloj.ogg (Dr Nick Riviera - La B Es de Barato.ogg)
BraseroGrowisofs stderr: Using BART_001.OGG;1 for  /Bart - Cervecigafas.ogg (Bart - Con Lo Larga Que Es la Cola.ogg)
BraseroGrowisofs stderr: Using KRUST000.OGG;1 for  /Krusty - Es Una Forma de Pagar Por Mis Problemas Con Glu Glu.ogg (Krusty - La Familia Orejotas.ogg)
BraseroGrowisofs stderr: Using HOMER007.AVI;1 for  /Homer - Otro Hermoso Dia Sin Salir del Útero.avi (Homer - Hombre Tropieza Gracioso.avi)
BraseroGrowisofs stderr: Using HOMER00A.OGG;1 for  /Homer - Batman es Científico.ogg (Homer - No Digas Venganza.ogg)
BraseroGrowisofs stderr: Using HOMER008.AVI;1 for  /Homer - Hombre Tropieza Gracioso.avi (Homer - Pozo Sin Fondo.avi)
BraseroGrowisofs stderr: Using HOMER00B.OGG;1 for  /Homer - No Digas Venganza.ogg (Homer - El Bocadillo de Tres Metros.ogg)
BraseroGrowisofs stderr: Using JARDI000.OGG;1 for  /Jardines Duff.ogg (Jardines Duff - Duff Para Tu, Duff Para Mí.ogg)
BraseroGrowisofs stderr: Writing:   Initial Padblock                        Start Block 0
BraseroGrowisofs stderr: Done with: Initial Padblock                        Block(s)    16
BraseroGrowisofs stderr: Writing:   Primary Volume Descriptor               Start Block 16
BraseroGrowisofs stderr: Done with: Primary Volume Descriptor               Block(s)    1
BraseroGrowisofs stderr: Writing:   Joliet Volume Descriptor                Start Block 17
BraseroGrowisofs stderr: Done with: Joliet Volume Descriptor                Block(s)    1
BraseroGrowisofs stderr: Writing:   End Volume Descriptor                   Start Block 18
BraseroGrowisofs stderr: Done with: End Volume Descriptor                   Block(s)    1
BraseroGrowisofs stderr: Writing:   Version block                           Start Block 19
BraseroGrowisofs stderr: Done with: Version block                           Block(s)    1
BraseroGrowisofs stderr: Writing:   Path table                              Start Block 20
BraseroGrowisofs stderr: Done with: Path table                              Block(s)    4
BraseroGrowisofs stderr: Writing:   Joliet path table                       Start Block 24
BraseroGrowisofs stderr: Done with: Joliet path table                       Block(s)    4
BraseroGrowisofs stderr: Writing:   Directory tree                          Start Block 28
BraseroGrowisofs stderr: Done with: Directory tree                          Block(s)    7
BraseroGrowisofs stderr: Writing:   Joliet directory tree                   Start Block 35
BraseroGrowisofs stderr: Done with: Joliet directory tree                   Block(s)    5
BraseroGrowisofs stderr: Writing:   Directory tree cleanup                  Start Block 40
BraseroGrowisofs stderr: Done with: Directory tree cleanup                  Block(s)    0
BraseroGrowisofs stderr: Writing:   Extension record                        Start Block 40
BraseroGrowisofs stderr: Done with: Extension record                        Block(s)    1
BraseroGrowisofs stderr: Writing:   The File(s)                             Start Block 41
BraseroGrowisofs stderr:   0.24% done, estimate finish Sat Mar 13 12:04:31 2010
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   0.47% done, estimate finish Sat Mar 13 12:04:31 2010
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   0.71% done, estimate finish Sat Mar 13 12:06:52 2010
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr: /dev/sr0: "Current Write Speed" is 12.3x1352KBps.
BraseroGrowisofs stderr: :-[ WRITE@LBA=10h failed with SK=4h/LOGICAL UNIT COMMUNICATION CRC ERROR (ULTRA-DMA/32)]: Input/output error
BraseroGrowisofs stderr: :-( write failed: Input/output error
BraseroGrowisofs stderr: /dev/sr0: flushing cache
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr: /dev/sr0: closing track
BraseroGrowisofs stderr: /dev/sr0: closing disc
BraseroGrowisofs stdout: HUP
BraseroGrowisofs stderr: HUP
BraseroGrowisofs process finished with status 5
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
	error		= 0
	message	= "no message"
BraseroGrowisofs stopping
BraseroGrowisofs got killed
Session error : unknown (brasero_burn_record brasero-burn.c:2811)
```


I això és el dmesg (ja havia tret el disc, no sé si això influeix o no...)


```
[    0.208041] NetLabel:  domain hash size = 128
[    0.208041] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.208053] NetLabel:  unlabeled traffic allowed by default
[    0.208184] hpet clockevent registered
[    0.208188] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.208194] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.208203] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.224018] pnp: PnP ACPI init
[    0.224047] ACPI: bus type pnp registered
[    0.228615] pnp: PnP ACPI: found 15 devices
[    0.228619] ACPI: ACPI bus type pnp unregistered
[    0.228624] PnPBIOS: Disabled by ACPI PNP
[    0.228640] system 00:01: ioport range 0xb78-0xb7b has been reserved
[    0.228645] system 00:01: ioport range 0xf78-0xf7b has been reserved
[    0.228649] system 00:01: ioport range 0xa78-0xa7b has been reserved
[    0.228653] system 00:01: ioport range 0xe78-0xe7b has been reserved
[    0.228657] system 00:01: ioport range 0xbbc-0xbbf has been reserved
[    0.228661] system 00:01: ioport range 0xfbc-0xfbf has been reserved
[    0.228665] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.228669] system 00:01: ioport range 0x294-0x297 has been reserved
[    0.228683] system 00:0d: ioport range 0x400-0x4bf could not be reserved
[    0.228693] system 00:0e: iomem range 0xd0000-0xd3fff has been reserved
[    0.228698] system 00:0e: iomem range 0xf0000-0xf7fff could not be reserved
[    0.228702] system 00:0e: iomem range 0xf8000-0xfbfff could not be reserved
[    0.228706] system 00:0e: iomem range 0xfc000-0xfffff could not be reserved
[    0.228711] system 00:0e: iomem range 0x7fff0000-0x7fffffff could not be reserved
[    0.228715] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[    0.228719] system 00:0e: iomem range 0x100000-0x7ffeffff could not be reserved
[    0.228723] system 00:0e: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.228727] system 00:0e: iomem range 0xfec01000-0xfed8ffff could not be reserved
[    0.228731] system 00:0e: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.228735] system 00:0e: iomem range 0xffb00000-0xffbfffff has been reserved
[    0.228740] system 00:0e: iomem range 0xfff00000-0xffffffff has been reserved
[    0.228744] system 00:0e: iomem range 0xe0000-0xeffff has been reserved
[    0.263463] AppArmor: AppArmor Filesystem Enabled
[    0.263504] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.263507] pci 0000:00:01.0:   IO window: disabled
[    0.263513] pci 0000:00:01.0:   MEM window: 0xf4000000-0xf6ffffff
[    0.263519] pci 0000:00:01.0:   PREFETCH window: 0xe0000000-0xefffffff
[    0.263525] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.263528] pci 0000:00:1e.0:   IO window: disabled
[    0.263534] pci 0000:00:1e.0:   MEM window: 0xf7000000-0xf70fffff
[    0.263540] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.263556] pci 0000:00:1e.0: setting latency timer to 64
[    0.263563] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.263567] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.263571] pci_bus 0000:01: resource 1 mem: [0xf4000000-0xf6ffffff]
[    0.263574] pci_bus 0000:01: resource 2 pref mem [0xe0000000-0xefffffff]
[    0.263578] pci_bus 0000:02: resource 1 mem: [0xf7000000-0xf70fffff]
[    0.263582] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.263585] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
[    0.263640] NET: Registered protocol family 2
[    0.263779] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.264282] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.265039] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.265458] TCP: Hash tables configured (established 131072 bind 65536)
[    0.265463] TCP reno registered
[    0.265616] NET: Registered protocol family 1
[    0.265727] Trying to unpack rootfs image as initramfs...
[    0.508679] Freeing initrd memory: 7719k freed
[    0.517101] cpufreq-nforce2: No nForce2 chipset.
[    0.517140] Scanning for low memory corruption every 60 seconds
[    0.517272] audit: initializing netlink socket (disabled)
[    0.517292] type=2000 audit(1268438716.516:1): initialized
[    0.525322] highmem bounce pool size: 64 pages
[    0.525330] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.527354] VFS: Disk quotas dquot_6.5.2
[    0.527445] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.528245] fuse init (API version 7.12)
[    0.528364] msgmni has been set to 1705
[    0.528706] alg: No test for stdrng (krng)
[    0.528729] io scheduler noop registered
[    0.528733] io scheduler anticipatory registered
[    0.528736] io scheduler deadline registered
[    0.528804] io scheduler cfq registered (default)
[    0.528922] pci 0000:01:00.0: Boot video device
[    0.529055] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.529091] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.529264] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.529269] ACPI: Power Button [PWRF]
[    0.529337] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.529341] ACPI: Power Button [PWRB]
[    0.529405] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.529412] ACPI: Sleep Button [SLPB]
[    0.529498] fan PNP0C0B:00: registered as cooling_device0
[    0.529507] ACPI: Fan [FAN] (on)
[    0.529808] processor LNXCPU:00: registered as cooling_device1
[    0.529864] processor LNXCPU:01: registered as cooling_device2
[    0.533201] thermal LNXTHERM:01: registered as thermal_zone0
[    0.533213] ACPI: Thermal Zone [THRM] (48 C)
[    0.533303] isapnp: Scanning for PnP cards...
[    0.708827] Switched to high resolution mode on CPU 1
[    0.712044] Switched to high resolution mode on CPU 0
[    0.886980] isapnp: No Plug & Play device found
[    0.888549] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.888654] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.888748] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.889106] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.889250] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.890734] brd: module loaded
[    0.891380] loop: module loaded
[    0.891491] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.891650] ata_piix 0000:00:1f.1: version 2.13
[    0.891671]   alloc irq_desc for 18 on node -1
[    0.891675]   alloc kstat_irqs on node -1
[    0.891684] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.891741] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.891866] scsi0 : ata_piix
[    0.892004] scsi1 : ata_piix
[    0.892970] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    0.892974] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    0.894242] Fixed MDIO Bus: probed
[    0.894293] PPP generic driver version 2.4.2
[    0.894441] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.894473]   alloc irq_desc for 23 on node -1
[    0.894476]   alloc kstat_irqs on node -1
[    0.894485] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.894504] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.894509] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.894560] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.898464] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    0.898484] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf7100000
[    0.913013] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.913123] usb usb1: configuration #1 chosen from 1 choice
[    0.913165] hub 1-0:1.0: USB hub found
[    0.913180] hub 1-0:1.0: 8 ports detected
[    0.913278] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.913309] uhci_hcd: USB Universal Host Controller Interface driver
[    0.913358]   alloc irq_desc for 16 on node -1
[    0.913361]   alloc kstat_irqs on node -1
[    0.913369] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.913379] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.913383] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.913433] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.913466] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000c000
[    0.913572] usb usb2: configuration #1 chosen from 1 choice
[    0.913612] hub 2-0:1.0: USB hub found
[    0.913622] hub 2-0:1.0: 2 ports detected
[    0.913681]   alloc irq_desc for 19 on node -1
[    0.913685]   alloc kstat_irqs on node -1
[    0.913691] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.913698] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.913703] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.913745] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.913774] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000c400
[    0.913873] usb usb3: configuration #1 chosen from 1 choice
[    0.913912] hub 3-0:1.0: USB hub found
[    0.913922] hub 3-0:1.0: 2 ports detected
[    0.913981] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.913989] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.913993] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.914035] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.914065] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000c800
[    0.914173] usb usb4: configuration #1 chosen from 1 choice
[    0.914210] hub 4-0:1.0: USB hub found
[    0.914221] hub 4-0:1.0: 2 ports detected
[    0.914281] uhci_hcd 0000:00:1d.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.914288] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.914293] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.914343] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.914366] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000cc00
[    0.914470] usb usb5: configuration #1 chosen from 1 choice
[    0.914506] hub 5-0:1.0: USB hub found
[    0.914517] hub 5-0:1.0: 2 ports detected
[    0.914656] PNP: PS/2 Controller [PNP0f13:PS2M] at 0x60,0x64 irq 12
[    0.914659] PNP: PS/2 controller doesn't have KBD irq; using default 1
[    0.916872] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.916882] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.917010] mice: PS/2 mouse device common for all mice
[    0.917159] rtc_cmos 00:03: RTC can wake from S4
[    0.917208] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.917234] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.917388] device-mapper: uevent: version 1.0.3
[    0.917527] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.917643] device-mapper: multipath: version 1.1.0 loaded
[    0.917648] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.917817] EISA: Probing bus 0 at eisa.0
[    0.917859] EISA: Detected 0 cards.
[    0.918002] cpuidle: using governor ladder
[    0.918008] cpuidle: using governor menu
[    0.918799] TCP cubic registered
[    0.918978] NET: Registered protocol family 10
[    0.919661] lo: Disabled Privacy Extensions
[    0.920208] NET: Registered protocol family 17
[    0.920237] Bluetooth: L2CAP ver 2.13
[    0.920240] Bluetooth: L2CAP socket layer initialized
[    0.920244] Bluetooth: SCO (Voice Link) ver 0.6
[    0.920247] Bluetooth: SCO socket layer initialized
[    0.920310] Bluetooth: RFCOMM TTY layer initialized
[    0.920314] Bluetooth: RFCOMM socket layer initialized
[    0.920317] Bluetooth: RFCOMM ver 1.11
[    0.920365] Using IPI No-Shortcut mode
[    0.920466] PM: Resume from disk failed.
[    0.920484] registered taskstats version 1
[    0.920623]   Magic number: 2:466:51
[    0.920707] rtc_cmos 00:03: setting system clock to 2010-03-13 00:05:17 UTC (1268438717)
[    0.920711] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.920714] EDD information not available.
[    1.064599] ata2.01: ATAPI: HL-DT-ST DVDRAM GSA-H42N, RL00, max UDMA/66
[    1.064630] ata2.01: limited to UDMA/33 due to 40-wire cable
[    1.080183] ata2.01: configured for UDMA/33
[    1.105590] ata1.00: ATA-7: ST3160215A, 3.AAD, max UDMA/100
[    1.105595] ata1.00: 312581808 sectors, multi 16: LBA48 
[    1.156242] ata1.01: ATA-7: MAXTOR STM3200820A, 3.AAD, max UDMA/100
[    1.156246] ata1.01: 390721968 sectors, multi 16: LBA48 
[    1.205531] ata1.00: configured for UDMA/100
[    1.247699] ata1.01: configured for UDMA/100
[    1.247833] scsi 0:0:0:0: Direct-Access     ATA      ST3160215A       3.AA PQ: 0 ANSI: 5
[    1.248071] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.248088] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.248221] sd 0:0:0:0: [sda] Write Protect is off
[    1.248229] scsi 0:0:1:0: Direct-Access     ATA      MAXTOR STM320082 3.AA PQ: 0 ANSI: 5
[    1.248234] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.248289] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.248472] sd 0:0:1:0: Attached scsi generic sg1 type 0
[    1.248565] sd 0:0:1:0: [sdb] 390721968 512-byte logical blocks: (200 GB/186 GiB)
[    1.248724] sd 0:0:1:0: [sdb] Write Protect is off
[    1.248729]  sda:
[    1.248734] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    1.248862] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.251814] scsi 1:0:1:0: CD-ROM            HL-DT-ST DVDRAM GSA-H42N  RL00 PQ: 0 ANSI: 5
[    1.263414] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.263419] Uniform CD-ROM driver Revision: 3.20
[    1.263541] sr 1:0:1:0: Attached scsi CD-ROM sr0
[    1.263613] sr 1:0:1:0: Attached scsi generic sg2 type 5
[    1.270132]  sda1 sda3 sda4 <
[    1.295348]  sdb: sda5 sdb1 sdb2
[    1.325937]  sda6
[    1.337697] sd 0:0:1:0: [sdb] Attached SCSI disk
[    1.337708]  sda7 sda8 >
[    1.338203] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.338227] Freeing unused kernel memory: 540k freed
[    1.338903] Write protecting the kernel text: 4580k
[    1.338981] Write protecting the kernel read-only data: 1840k
[    1.512873] Linux agpgart interface v0.103
[    1.519213] agpgart-intel 0000:00:00.0: Intel 865 Chipset
[    1.522187] agpgart-intel 0000:00:00.0: AGP aperture is 64M @ 0xf0000000
[    1.573083] Floppy drive(s): fd0 is 1.44M
[    1.597069] FDC 0 is a post-1991 82077
[    1.633202] usb 3-2: new full speed USB device using uhci_hcd and address 2
[    1.674748] b44 0000:02:0e.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.744131] ssb: Sonics Silicon Backplane found on PCI device 0000:02:0e.0
[    1.744177] b44.c:v2.0
[    1.765109] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:10:5c:eb:83:ef
[    1.807047] usb 3-2: configuration #1 chosen from 1 choice
[    1.811700] hub 3-2:1.0: USB hub found
[    1.813703] hub 3-2:1.0: 4 ports detected
[    2.093665] usb 3-2.1: new low speed USB device using uhci_hcd and address 3
[    2.228753] usb 3-2.1: configuration #1 chosen from 1 choice
[    2.239908] usbcore: registered new interface driver hiddev
[    2.255074] input: USB-compliant keyboard as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2.1/3-2.1:1.0/input/input4
[    2.255177] generic-usb 0003:0B38:0003.0001: input,hidraw0: USB HID v1.10 Keyboard [USB-compliant keyboard] on usb-0000:00:1d.1-2.1/input0
[    2.283219] input: USB-compliant keyboard as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2.1/3-2.1:1.1/input/input5
[    2.283402] generic-usb 0003:0B38:0003.0002: input,hiddev96,hidraw1: USB HID v1.10 Mouse [USB-compliant keyboard] on usb-0000:00:1d.1-2.1/input1
[    2.283428] usbcore: registered new interface driver usbhid
[    2.283432] usbhid: v2.6:USB HID core driver
[    2.655146] vesafb: framebuffer at 0xe0000000, mapped to 0xf8180000, using 5120k, total 5120k
[    2.655151] vesafb: mode is 1280x1024x32, linelength=5120, pages=0
[    2.655154] vesafb: scrolling: redraw
[    2.655160] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    2.655237] fb0: VESA VGA frame buffer device
[    2.664097] Console: switching to colour frame buffer device 160x64
[    3.055069] xor: automatically using best checksumming function: pIII_sse
[    3.072001]    pIII_sse  :  3541.000 MB/sec
[    3.072006] xor: using function: pIII_sse (3541.000 MB/sec)
[    3.075509] device-mapper: dm-raid45: initialized v0.2594b
[    3.615851] PM: Starting manual resume from disk
[    3.615858] PM: Resume from partition 8:5
[    3.615862] PM: Checking hibernation image.
[    3.616065] PM: Resume from disk failed.
[    3.636118] EXT4-fs (sda8): barriers enabled
[    3.643781] kjournald2 starting: pid 389, dev sda8:8, commit interval 5 seconds
[    3.643866] EXT4-fs (sda8): delayed allocation enabled
[    3.643872] EXT4-fs: file extents enabled
[    3.644011] EXT4-fs: mballoc enabled
[    3.644033] EXT4-fs (sda8): mounted filesystem with ordered data mode
[    4.354536] type=1505 audit(1268438720.931:2): operation="profile_load" pid=414 name=/usr/share/gdm/guest-session/Xsession
[    4.372332] type=1505 audit(1268438720.951:3): operation="profile_load" pid=415 name=/sbin/dhclient3
[    4.372923] type=1505 audit(1268438720.951:4): operation="profile_load" pid=415 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    4.373252] type=1505 audit(1268438720.951:5): operation="profile_load" pid=415 name=/usr/lib/connman/scripts/dhclient-script
[    4.419739] type=1505 audit(1268438720.995:6): operation="profile_load" pid=416 name=/usr/bin/evince
[    4.429610] type=1505 audit(1268438721.007:7): operation="profile_load" pid=416 name=/usr/bin/evince-previewer
[    4.435514] type=1505 audit(1268438721.011:8): operation="profile_load" pid=416 name=/usr/bin/evince-thumbnailer
[    4.467922] type=1505 audit(1268438721.043:9): operation="profile_load" pid=418 name=/usr/lib/cups/backend/cups-pdf
[    4.468640] type=1505 audit(1268438721.047:10): operation="profile_load" pid=418 name=/usr/sbin/cupsd
[   15.874259] udev: starting version 147
[   15.926587] Adding 2104472k swap on /dev/sda5.  Priority:-1 extents:1 across:2104472k 
[   15.936524] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.967459] lp: driver loaded but no devices found
[   16.040249] intel_rng: FWH not detected
[   16.258008] nvidia: module license 'NVIDIA' taints kernel.
[   16.258015] Disabling lock debugging due to kernel taint
[   16.402430] ip_tables: (C) 2000-2006 Netfilter Core Team
[   16.490345] EXT4-fs (sda8): internal journal on sda8:8
[   16.548682] parport_pc 00:09: reported by Plug and Play ACPI
[   16.548740] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   16.557802] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.558159] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.20  Thu Jun 25 19:23:24 PDT 2009
[   16.675396] parport0: Printer, HEWLETT-PACKARD DESKJET 840C
[   16.675747] lp0: using parport0 (interrupt-driven).
[   16.702124] psmouse serio1: ID: 10 00 64
[   16.708694] ppdev: user-space parallel port driver
[   16.717606] gameport: NS558 PnP Gameport is pnp00:0b/gameport0, io 0x201, speed 890kHz
[   16.799435] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   16.799862] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   16.799867] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[   16.799872] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   16.813914] logips2pp: Detected unknown logitech mouse model 89
[   16.936675]   alloc irq_desc for 17 on node -1
[   16.936681]   alloc kstat_irqs on node -1
[   16.936694] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   16.936760] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   17.264038] intel8x0_measure_ac97_clock: measured 53622 usecs (2584 samples)
[   17.264043] intel8x0: clocking to 48000
[   17.310326] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input6
[   17.578020] EXT4-fs (sda1): barriers enabled
[   17.592538] kjournald2 starting: pid 856, dev sda1:8, commit interval 5 seconds
[   17.601444] EXT4-fs (sda1): internal journal on sda1:8
[   17.601451] EXT4-fs (sda1): delayed allocation enabled
[   17.601457] EXT4-fs: file extents enabled
[   17.601887] EXT4-fs: mballoc enabled
[   17.601912] EXT4-fs (sda1): mounted filesystem with ordered data mode
[   17.879363] __ratelimit: 6 callbacks suppressed
[   17.879377] type=1505 audit(1268435134.455:13): operation="profile_replace" pid=939 name=/usr/share/gdm/guest-session/Xsession
[   17.884145] type=1505 audit(1268435134.463:14): operation="profile_replace" pid=940 name=/sbin/dhclient3
[   17.884893] type=1505 audit(1268435134.463:15): operation="profile_replace" pid=940 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   17.885352] type=1505 audit(1268435134.463:16): operation="profile_replace" pid=940 name=/usr/lib/connman/scripts/dhclient-script
[   17.900282] type=1505 audit(1268435134.479:17): operation="profile_replace" pid=1005 name=/usr/bin/evince
[   17.913853] type=1505 audit(1268435134.491:18): operation="profile_replace" pid=1005 name=/usr/bin/evince-previewer
[   17.925048] type=1505 audit(1268435134.503:19): operation="profile_replace" pid=1005 name=/usr/bin/evince-thumbnailer
[   17.935624] type=1505 audit(1268435134.511:20): operation="profile_replace" pid=1008 name=/usr/lib/cups/backend/cups-pdf
[   17.936471] type=1505 audit(1268435134.515:21): operation="profile_replace" pid=1008 name=/usr/sbin/cupsd
[   17.940239] type=1505 audit(1268435134.519:22): operation="profile_replace" pid=1009 name=/usr/sbin/mysqld-akonadi
[   17.965049] kjournald starting.  Commit interval 5 seconds
[   17.974041] EXT3 FS on sdb1, internal journal
[   17.974057] EXT3-fs: mounted filesystem with writeback data mode.
[   18.056450] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.431269] agpgart-intel 0000:00:00.0: AGP 3.0 bridge
[   19.431299] agpgart-intel 0000:00:00.0: putting AGP V3 device into 8x mode
[   19.431368] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
[   21.079494] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   21.079499] vboxdrv: Successfully done.
[   21.079502] vboxdrv: Found 2 processor cores.
[   21.079613] vboxdrv: fAsync=0 offMin=0x47c offMax=0x24f8
[   21.079675] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   21.079678] vboxdrv: Successfully loaded version 3.1.4 (interface 0x00100001).
[   21.805188] b44: eth0: Link is up at 100 Mbps, full duplex.
[   21.805194] b44: eth0: Flow control is off for TX and off for RX.
[   21.805564] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   22.430821] CPU0 attaching NULL sched-domain.
[   22.430830] CPU1 attaching NULL sched-domain.
[   22.445094] CPU0 attaching sched-domain:
[   22.445100]  domain 0: span 0-1 level SIBLING
[   22.445104]   groups: 0 1
[   22.445111]   domain 1: span 0-1 level MC
[   22.445115]    groups: 0-1 (__cpu_power = 2048)
[   22.445124] CPU1 attaching sched-domain:
[   22.445127]  domain 0: span 0-1 level SIBLING
[   22.445131]   groups: 1 0
[   22.445138]   domain 1: span 0-1 level MC
[   22.445142]    groups: 0-1 (__cpu_power = 2048)
[   23.695327] CPU0 attaching NULL sched-domain.
[   23.695342] CPU1 attaching NULL sched-domain.
[   23.708205] CPU0 attaching sched-domain:
[   23.708217]  domain 0: span 0-1 level SIBLING
[   23.708224]   groups: 0 1
[   23.708241] CPU1 attaching sched-domain:
[   23.708248]  domain 0: span 0-1 level SIBLING
[   23.708256]   groups: 1 0
[   32.617029] eth0: no IPv6 routers present
[  237.022018] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.129 DST=239.255.255.250 LEN=128 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=50868 DPT=1900 LEN=108 
[  239.024123] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.129 DST=239.255.255.250 LEN=128 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=50868 DPT=1900 LEN=108 
[  243.025093] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.129 DST=239.255.255.250 LEN=128 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=50868 DPT=1900 LEN=108 
[  249.028326] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.129 DST=239.255.255.250 LEN=128 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=50868 DPT=1900 LEN=108 
[  257.029026] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.129 DST=239.255.255.250 LEN=128 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=50868 DPT=1900 LEN=108 
[ 4287.319200] Inbound IN=eth0 OUT= MAC=00:10:5c:eb:83:ef:00:1a:2b:53:33:e0:08:00 SRC=93.130.69.4 DST=192.168.1.129 LEN=70 TOS=0x00 PREC=0x00 TTL=252 ID=63240 PROTO=UDP SPT=16595 DPT=47840 LEN=50 
[ 4287.647074] Inbound IN=eth0 OUT= MAC=00:10:5c:eb:83:ef:00:1a:2b:53:33:e0:08:00 SRC=93.130.69.4 DST=192.168.1.129 LEN=93 TOS=0x00 PREC=0x00 TTL=252 ID=63262 PROTO=UDP SPT=16595 DPT=47840 LEN=73 
[ 6949.151430] Inbound IN=eth0 OUT= MAC=00:10:5c:eb:83:ef:00:1a:2b:53:33:e0:08:00 SRC=134.153.97.220 DST=192.168.1.129 LEN=70 TOS=0x00 PREC=0x00 TTL=252 ID=33747 PROTO=UDP SPT=41762 DPT=47840 LEN=50 
[29373.711779] Inbound IN=eth0 OUT= MAC=00:10:5c:eb:83:ef:00:1a:2b:53:33:e0:08:00 SRC=187.47.166.156 DST=192.168.1.129 LEN=40 TOS=0x00 PREC=0x00 TTL=252 ID=56151 DF PROTO=TCP SPT=31494 DPT=52991 WINDOW=16560 RES=0x00 ACK URGP=0 
[36962.439335] Inbound IN=eth0 OUT= MAC=00:10:5c:eb:83:ef:00:1a:2b:53:33:e0:08:00 SRC=89.155.232.72 DST=192.168.1.129 LEN=40 TOS=0x00 PREC=0x00 TTL=252 ID=1765 DF PROTO=TCP SPT=27810 DPT=42334 WINDOW=52240 RES=0x00 ACK URGP=0 
[37041.292730] Inbound IN=eth0 OUT= MAC=00:10:5c:eb:83:ef:00:1a:2b:53:33:e0:08:00 SRC=89.155.232.72 DST=192.168.1.129 LEN=40 TOS=0x00 PREC=0x00 TTL=252 ID=8012 DF PROTO=TCP SPT=27810 DPT=42334 WINDOW=65340 RES=0x00 ACK URGP=0 
[42480.635253] cdrom: This disc doesn't have any tracks I recognize!
[42847.326131] cdrom: This disc doesn't have any tracks I recognize!
[42847.361860] sr 1:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[42847.361870] sr 1:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[42847.361881] Info fld=0x0
[42847.361885] sr 1:0:1:0: [sr0] Add. Sense: Logical block address out of range
[42847.361895] end_request: I/O error, dev sr0, sector 0
[42847.361904] __ratelimit: 3 callbacks suppressed
[42847.361909] Buffer I/O error on device sr0, logical block 0
[42847.367144] sr 1:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[42847.367156] sr 1:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[42847.367166] Info fld=0x0
[42847.367170] sr 1:0:1:0: [sr0] Add. Sense: Logical block address out of range
[42847.367181] end_request: I/O error, dev sr0, sector 0
[42847.367190] Buffer I/O error on device sr0, logical block 0
[42847.392729] sr 1:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[42847.392746] sr 1:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[42847.392757] Info fld=0x0
[42847.392761] sr 1:0:1:0: [sr0] Add. Sense: Logical block address out of range
[42847.392772] end_request: I/O error, dev sr0, sector 0
[42847.392783] Buffer I/O error on device sr0, logical block 0
[42847.398529] sr 1:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[42847.398539] sr 1:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[42847.398549] Info fld=0x0
[42847.398553] sr 1:0:1:0: [sr0] Add. Sense: Logical block address out of range
[42847.398564] end_request: I/O error, dev sr0, sector 0
[42847.398574] Buffer I/O error on device sr0, logical block 0
[43093.076824] warning: `growisofs' uses 32-bit capabilities (legacy support in use)
[43133.561382] cdrom: This disc doesn't have any tracks I recognize!
[43133.587194] sr 1:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[43133.587206] sr 1:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[43133.587217] Info fld=0x0
[43133.587222] sr 1:0:1:0: [sr0] Add. Sense: Logical block address out of range
[43133.587232] end_request: I/O error, dev sr0, sector 0
[43133.587243] Buffer I/O error on device sr0, logical block 0
[43133.592376] sr 1:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[43133.592387] sr 1:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[43133.592397] Info fld=0x0
[43133.592401] sr 1:0:1:0: [sr0] Add. Sense: Logical block address out of range
[43133.592412] end_request: I/O error, dev sr0, sector 0
[43133.592422] Buffer I/O error on device sr0, logical block 0
[43203.671361] UDF-fs: No VRS found
[43203.671367] UDF-fs: No partition found (1)
[43203.685338] ISO 9660 Extensions: Microsoft Joliet Level 3
[43203.686799] attempt to access beyond end of device
[43203.686804] sr0: rw=0, want=164, limit=128
[43203.686807] Unable to read rock-ridge attributes
[43203.686810] ISOFS: changing to secondary root
[43203.686823] attempt to access beyond end of device
[43203.686826] sr0: rw=0, want=144, limit=128
[43203.686829] ISOFS: unable to read i-node block
[43203.686834] isofs_fill_super: get root inode failed

```

---

### Post by Daerun on 2011-03-16
Rescato aquest tema perquè el problema segueix igual: quan necessito gravar un disc ho he de fer des de Windows. He googlejat molt i arribo a la conclusió que és un problema bastant generalitzat i que afecta totes les distros, però enlloc he trobat cap solució, a veure si algú ha sigut capaç de trobar-ne alguna.

---

