---
title: "Problema amb lo disc dur extern"
date: 2012-06-25
forum: Catalan Team
---

### Post by lo gambusí on 2012-06-25
Salutacions,

Intento carregar lo disc dur extern i en connectar-lo a l'ordinador em surt automàticament el següent missatge d'error:

> Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.


Què hauria de fer? Veig que em diu els passos a seguir però no acabo de saber interpretar-los...

Gràcies :)

---

### Post by wgarcia on 2012-06-26
Sembla dir-te que és un disc amb format NTFS de Windows i que té errors en alguns sectors. Això normalment ho arregla algun programa de verificació, però sent format NTFS et suggereix fer-lo des de Windows i et dóna instruccions detallades de com fer-ho (chkdsk /f). 

També pot ser un problema de maquinari del disc. No crec que sigui la tercera possibilitat que suggereix (SoftRAID/FakeRAID) perquè això és una configuració avençada que recordaries haver fet.

---

### Post by AlbertJB on 2012-07-07
[http://ubuntuforums.org/showthread.php?t=1144175](http://ubuntuforums.org/showthread.php?t=1144175)

---

