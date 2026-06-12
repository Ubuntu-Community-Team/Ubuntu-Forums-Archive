---
title: "En actualitzar no en carrega la home (particio)"
date: 2010-11-18
forum: Catalan Team
---

### Post by pserra on 2010-11-18
relacionar arrel i home?
Hola, per solucionar el tema de conexions a internet, al final m'he passat a la versió 10.10... però per variar sempre m'havien de sortir altres problemes:
el principal:
quan vaig passar-me a la 10.04 vaig crear una partició per a l'arrel:/ i un altre per la home.... per evitar començar de 0 en les actualitzacions..
El cas es que al instal·lar des de el cd, m'ha demanat adreça de arrel, li he fet formatejar-la i ha instal·lat tot   (demanant altre vegada nom..etc)
Però ara no em carrega rés de la configuració anterior... com hoo faig ara per carregar la home anterior? o per dir-li que la home esta a sda7?

m'he saltat algun pas al instal·lar?

es millor tornar-lo a instal·lar i en algun pas que m'ha passat dir-li on és la home?

Merci

---

### Post by akyra on 2010-11-18
Hola pserra,

Quan l'has intal·lat li has dit que formategi la "/", però li has dis a on té la "/home"?
Si no li has dit li hauries de dir, pero sense seleccionar formategerla.

No sé, si hi ha alguna altre manera de fer-ho una vegada instal·lat.

Salutacions

---

### Post by kimet on 2010-11-18
Edita /etc/fstab per que munti a partició /home
p.ex.
```
/dev/sda1       /home           ext3    defaults        0       2
```

pd. Possiblement tinguis que eliminar la /home de la partició en que està el sistema...

---

### Post by pserra on 2010-11-18
> **akyra said:**
> Hola pserra,

Quan l'has intal·lat li has dit que formategi la "/", però li has dis a on té la "/home"?
Si no li has dit li hauries de dir, pero sense seleccionar formategerla.

No sé, si hi ha alguna altre manera de fer-ho una vegada instal·lat.

Salutacions

a la pantalla on li he dit on era la "/"
no era gaire 'intuitiva'  i me la he passat.... 
crec que a través del fstab li puc dir on esta la home... i al reiniciar me la tindria que carregar com a home... es així?
passo la fstab actual:
> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda8       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=632ba305-c807-406d-9db4-707088895310 none            swap    sw              0       0
la meva uuid és:
> pere@pere-Compaq-Presario-CQ71-Notebook-PC:~$ ls -l /dev/disk/by-uuid 
total 0
lrwxrwxrwx 1 root root 10 2010-11-18 13:40 0A186C40186C2CBF -> ../../sda2
lrwxrwxrwx 1 root root 10 2010-11-18 13:40 136fd397-e857-4cfe-982a-614098b4f570 -> ../../sda7
lrwxrwxrwx 1 root root 10 2010-11-18 13:40 3F6F75982CCD6A12 -> ../../sda4
lrwxrwxrwx 1 root root 10 2010-11-18 13:40 632ba305-c807-406d-9db4-707088895310 -> ../../sda6
lrwxrwxrwx 1 root root 10 2010-11-18 13:40 6C156B214FCCE763 -> ../../sda1
lrwxrwxrwx 1 root root 10 2010-11-18 13:40 7994-2DA0 -> ../../sda5
lrwxrwxrwx 1 root root 10 2010-11-18 13:40 b94c04b6-2e34-40be-93cc-7e648a28a229 -> ../../sda8
[B]la meva arrel esta a sda8
i la /home anterior esta a sda7[/B]
> 
pere@pere-Compaq-Presario-CQ71-Notebook-PC:~$ sudo fdisk -l

Disc /dev/sda: 320.1 GB, 320072933376 octets
255 heads, 63 sectors/track, 38913 cylinders
Units = cilindres of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9fca1fd5

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sda1   *           1       13462   108133483+   7  HPFS/NTFS
/dev/sda2           13463       34639   170104252+   7  HPFS/NTFS
/dev/sda3           34640       37632    24036762    5  Estesa
/dev/sda4           37632       38913    10292224    7  HPFS/NTFS
/dev/sda5           34640       35199     4498168+   b  W95 FAT32
/dev/sda6           35200       35566     2947896   82  Intercanvi Linux / Solaris
/dev/sda7           35567       36539     7812500   83  Linux
/dev/sda8           36539       37632     8777728   83  Linux


com ho puc solventar? si es pot fer a través del fstab que he de modificar?
Merci

---

### Post by wgarcia on 2010-11-18
Sí, com t'han dit ho pots fer al fstab, assegurat del UUID de la partició on està "home" i del tipus de formateig (ext3, ext4) que té aquesta partició.

---

### Post by pserra on 2010-11-18
Merci wgarcia i akira problema arreglat,
pega que he de instal·lar   part  del programari  .....
però ja m'he estalviat molta feina...almeys ara em torna a anar internet...
Merci

---

