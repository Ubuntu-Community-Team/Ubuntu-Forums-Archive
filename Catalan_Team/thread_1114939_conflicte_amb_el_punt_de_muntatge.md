---
title: "conflicte amb el punt de muntatge"
date: 2009-04-03
forum: Catalan Team
---

### Post by Miquel Ubuntero on 2009-04-03
Hola.
Tinc una clau usb amb Ubuntu "Live CD".
Un cop al escriptori, si intento insta&#320;lar Ubuntu en una altre clau usb no puc, perquè el sistema hem diu que desmunti la clau destí. Hem demana desmuntar /media/cdrom

El problema be, segons he vist am un editor de particions, que el punt de muntatge de les dos claus usb és el mateix "media/cdrom". Aleshores, no puc desmuntar i no se per on tirar!

Algú te cap idea, sisplau.

---

### Post by papapep on 2009-04-03
Enganxa el que et surti (amb els dos pendrives punxats, i espera un minutet a fer-ho que no sigui que li costi muntar-lo):

```
cat /etc/mtab
```

---

### Post by Miquel Ubuntero on 2009-04-03
Aquí ho tens:

custom@custom:~$ cat /etc/mtab
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
/proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
rootfs / rootfs rw 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
/dev/sdb1 /media/cdrom vfat rw,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1 0 0
/dev/loop0 /rofs squashfs ro,noatime 0 0
tmpfs /tmp tmpfs rw,nosuid,nodev 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/custom/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=custom 0 0
/dev/sdb1 /media/disk vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush 0 0
/dev/sdb2 /media/disk-1 ext2 rw,nosuid,nodev,uhelper=hal 0 0
custom@custom:~$

---

### Post by papapep on 2009-04-03
Doncs aquí veig dos dispositius (a banda del CD i d'una ISO (loop)):

> /dev/sdb1 /media/disk vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=99 9,utf8,umask=077,flush 0 0
/dev/sdb2 /media/disk-1 ext2 rw,nosuid,nodev,uhelper=hal 0 0

Crec que et deus confondre al moment de dir-li on ha d'instal·lar l'Ubuntu. Per cert, suposo que tens clar que un dels pendrives el tens formatat a vfat i l'altre a ext2.

---

### Post by Miquel Ubuntero on 2009-04-03
El dispositiu /deb/sdb1 amb format fat seria el destí, això ho tinc clar. Aquest dispositiu, segons l'editor de particions, te com a punt de muntatge /media/cdrom
Donat que el dispositiu "Live CD" te el mateix punt de muntatge!! /media/cdrom, dons no puc desmuntar /deb/sdb1 per prosseguir l'insta&#320;lació. Ni puc desmuntar-lo ni formatar-lo ni res :mad:

Per cert, gracies per respondre tan ràpid!

---

### Post by papapep on 2009-04-03
Doncs desmunta'l:

```
sudo umount /dev/sdb1
```

i torna'l a muntar a un altre lloc:

```
sudo mount /dev/sdb1 /on/tu/vulguis
```

sempre que existeixi el directori, clar...

---

### Post by Miquel Ubuntero on 2009-04-03
Hola.
Amb sudo umount /dev/sdb1 sembla que ho desmunta, desapareix del escriptori la icona del usb. Però no solventa el problema. En el procés s'insta&#320;lació demana desmuntar /dev/cdrom

Be, però per sort,o per rumiar una mica, ho he so&#320;lucionat!! :guitar:

Amb una Live-CD (cdrom real, no usb) he eliminat totalment les particions del usb en qüestió. Després he iniciat de nou el Live-usb (amb la meva estimada iso totalment personalitzada) i llavors si que he pogut insta&#320;lar-la a la nova clau usb de 16 GB.

En fi, "solved", moltes gracies als que us heu interessat pel meu problema.

Salut! i molt Ubuntu ):P

---

### Post by SiscoGarcia on 2009-04-05
Miquel, perdona la meua ignorància i que em posi pel mig, però aquest és un tema que m'interessa perquè havia pensat la possibilitat d'instal·lar-me ubuntu a una clau usb de 8 GB. 2 coses:

1.- Creus que hi cabrà a 8 GB? Suposo que sí perquè ho tinc al netbook.

2.- Pots explicar amb més detall com has fet per instal·lar-la; vull dir que com li has dit que la destinació sigui la clau usb?

Gràcies.

---

### Post by Miquel Ubuntero on 2009-04-06
Hola company.
1. 8GB és més que suficient. Una instal·lació normal ocupa uns 4 GB aproximadament. També, un cop instal·lat, tens l'opció d'eliminar espai desintal·lant el programari que no facis servir. Que és justament el que vaig fer en una clau usb que tinc de 4 GB.

2. En quant "com dir-li de'instal·lar al usb", també molt sencill. El procés és el mateix que instal·lar a un disc dur normal. Quan arrivis al punt de l'instal·lació que has de triar el disc dur, segurament veuras la teva clau usb com un disc dur més. Pot ser tindras un disc dur detectat com sda i la clau com sdb, o quelcom semblant. La mida de la clau també t'ajudara a distingir-la. Per la resta d'instal·lació no hi ha diferència.

Una recomanació, per evitar equivocacions. Si pots, desconecta el disc dur del pc que facis servir per aquesta tasca.

Si tens més dubtes, pregunta, pregunta ;)

---

### Post by papapep on 2009-04-06
1T1F?? (un tema, un fil?)

---

### Post by SiscoGarcia on 2009-04-06
> **papapep said:**
> 1T1F?? (un tema, un fil?)

Mil perdons, no creia estar canviant de tema. Sóc un fervent defensor de la màxima 1T1F. :oops:

---

