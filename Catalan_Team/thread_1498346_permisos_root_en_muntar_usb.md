---
title: "permisos root en muntar usb"
date: 2010-05-31
forum: Catalan Team
---

### Post by quitus on 2010-05-31
hola, retocant l'arxiu fstab he perdut el funcionament optim del meu ordinador. En endollar el llapis, em munta el dispositiu però com a root, curiosament si desmunto i torno a muntar, els permisos son correctes.

Aquí el fstab

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid    0  0  
# / was on /dev/sda3 during installation
UUID=2dfc75cf-5d37-473a-a476-32d0756635e4  /            ext4  errors=remount-ro      0  1  
# /home was on /dev/sda1 during installation
UUID=3dae9cd7-9122-4984-94e5-d5e076fb69bb  /home        ext4  defaults               0  2  
# swap was on /dev/sda2 during installation
UUID=c2178330-4d7f-4e20-9e0e-ba4b4ad203cb  none         swap  sw                     0  0  

/dev/sdb1                                  /media/sdb1  vfat  defaults,users,noauto  0  0  
```

salut

---

### Post by wgarcia on 2010-06-01
Però necessites realment una línia al /etc/fstab per al llapis usb? Jo crec que sense aquesta línia es munta automàticament quan l'endolles, i queda assignat a l'usuari que està loguejat.

La línia del /etc/fstab podria ser útil perquè el llapis usb es munti (si el tens endollat) fins i tot sense sessió d'escriptori, per exemple si els fas servir per còpies de seguretat sense haver entrat a l'escriptori, però si l'únic que vols es fer-lo servir des de l'escriptori penso que no fa falta. 

Perquè es munti amb la línia del fstab (i quedi assignat a un usuari) necessites una "regla udev" (a /etc/udev/rules.d) que són força complicades d'escriure i estan poc documentades. A més l'udev ha canviat força amb els últims nuclis de Linux, és el mètode preferit ara per gestionar discos (substituint a "hal", que no és allò d'Odisea 2001).

---

### Post by quitus on 2010-06-01
Tens tota la raó del mon, un cop eliminada la línia tot torna a funcionar. Diria que ja havia provat d'eliminar la línia del fstab i no va funcionar, pero potser vaig provar 2 o 3 coses a l'hora i s'hem van barrejar. No se on vaig llegir que si no apareixia en el fstab es muntava com a root.

Sobre udev ja vaig fullejar una revisteta on apareix un article però realment no entenc ni papa.

salut i gracies.

---

