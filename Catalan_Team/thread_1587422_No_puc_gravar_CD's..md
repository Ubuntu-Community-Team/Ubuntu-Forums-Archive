---
title: "No puc gravar CD's."
date: 2010-10-03
forum: Catalan Team
---

### Post by undesnofilo on 2010-10-03
No puc gravar CD's ni amb el K3b ni amb el Gnome Baker.
L'ordinador reconeix les unitats de CD i CD/RW però no hi puc accedir, em podeu ajudar?

---

### Post by wgarcia on 2010-10-04
Quin és l'error que et surt?

---

### Post by undesnofilo on 2010-10-04
Quan engego el K3b em surt:
p, li { white-space: pre-wrap; } [COLOR=#BF0303]No optical drive found.[/COLOR]
K3b did not find any optical device in your system.
*Solution*: Make sure HAL daemon is running, it is used by K3b for finding devices.
i al Gnome Baker després de convertir els mp3 en arxius d'audio diu:

Fallat audio CD

amb la versió 9-04 d'ubuntu m'anava perfectament i al atualitzar a 10.04 és quan han deixat de funcionar el lector i el gravador.

---

### Post by undesnofilo on 2010-10-04
Al gnome baker l'eror és:

wodim: No write mode specified.
wodim: Assuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
scsidev: '/dev/sr1'
devname: '/dev/sr1'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.10
SCSI buffer size: 64512
wodim: Cannot do inquiry for CD/DVD-Recorder.
TOC Type: 0 = CD-DA
Driveropts: 'burnfree'
Errno: 5 (Input/output error), test unit ready scsi sendcmd: fatal error
CDB:  00 00 00 00 00 00
cmd finished after 0.000s timeout 40s

---

