---
title: "No puedo montar un disco duro"
date: 2018-09-11
forum: Catalan Team
---

### Post by paurubert on 2018-09-11
Mi disco duro externo de golpe no me funciona. Mensaje.
Error mounting /dev/sde1 at /media/pau/TOSHIBA EXT: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sde1" "/media/pau/TOSHIBA EXT"' exited with non-zero exit status 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sde1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

---

### Post by wgarcia on 2018-09-12
Sembla que el sistema de fitxers NTFS s'ha corromput i li cal una neteja. Hi ha eines per fer això a l'Ubuntu, però sent el format NTFS el millor és fer-lo a un sistema que tingui Windows, si tens accés. Quan endollis aquest disc al sistema Windows t'hauria de dir que vol netejar el sistema. Si no ho fa, clicant amb el botó dret del ratolí i anant a "Propietats" hi ha una opció per netejar el sistema de fitxers del disc.

---

