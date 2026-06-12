---
title: "Problemes amb el SWAP"
date: 2009-01-12
forum: Catalan Team
---

### Post by kukat on 2009-01-12
Estic a clase amb un ordinador que no arriba als 500 MB de RAM...i crec que no te partició SWAP...

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=5845a5e7-e155-4ac6-b08e-2e1232ad9705 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=d3ea48aa-5134-4f7a-8e05-66c9ff6f0146 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

M'equivoque?? 

El millor de tot es que te un Debian per a Administrar els ordinadors, i crec que deu haver-hi una partició SWAP...es pot modificar el fitxer de dalt per a que tinga  SWAP? que puc fer? gràcies

---

### Post by kukat on 2009-01-12
la partició SWAP està en /dev/sda5...però crec que no està gastant-la!

---

### Post by kukat on 2009-01-12
val, ja està tot solucionat!

he fet el seguent: 
sudo swapon /dev/sda5

però crec que amb afegir aquesta linia al fitxer /etc/fstab sobra: 

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
**/dev/sda5       swap            swap      defaults            0       0**


He fet alguna cosa mal? Crec que ja funciona!!! Al monitor del sistema posa que tinc 1GB de SWAP!:)

---

