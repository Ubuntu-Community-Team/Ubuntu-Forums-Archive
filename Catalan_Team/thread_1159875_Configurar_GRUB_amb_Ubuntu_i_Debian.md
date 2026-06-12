---
title: "Configurar GRUB amb Ubuntu i Debian"
date: 2009-05-15
forum: Catalan Team
---

### Post by kukat on 2009-05-15
Hola a tots!

Vull preguntar un problema que ja he tingut moltes vegades, i que mai he sabut solucionar bé.

He insta&#322;lat Debian al meu ordinador (que solament tenia el Ubuntu Jaunty Jackalope) per a veure com funciona el pare de l'Ubuntu...jejeje

I m'ha insta&#322;lat el carregador GRUB a la partició del Debian. El cas es que no puc muntar cap partició al debian amb el mount =?=

Com puc modificar el GRUB per a tindre les dos particions en aquest?

Ho siga....jo edite el grub amb gedit /boot/grub/menu.lst:

title		Debian GNU/Linux, kernel 2.6.26-1-686
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.26-1-686 root=/dev/hda7 ro quiet
initrd		/boot/initrd.img-2.6.26-1-686

title		Debian GNU/Linux, kernel 2.6.26-1-686 (single-user mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.26-1-686 root=/dev/hda7 ro single
initrd		/boot/initrd.img-2.6.26-1-686

Em surt el de dalt...

I Ubuntu està al /dev/hda6 segons el GParted...però lo de "kernel" i "initrd"....com puc saber-ho??? Hi ha alguna comanda que em permeta saber això? o simplement canviar a hda6???


Salut!

---

### Post by kimet on 2009-05-15
Son dues coses diferents, no sé si els que no pots fer és muntar la partició d'ubuntu desde debian o no pots entrar a l'ubuntu perqué no surt al grub...

Per muntar partició:

-Creas un directori on muntar la partició, (és sol anomenar /media).

```
# mkdir /media/nom_del_directori_creat
```

-Muntes la partició:

```
mount -t ext3 /dev/hda6 /media/nom_del_directori_creat
```
(tingues en compte el format, ext3,ext4,etc...)


-Edites fstab:

```
nano(o el editor que vulguis)/etc/fstab
```

-I afegeixes al final:

```
/dev/hda6 /media/nom_del_directori_creat ext3 defaults 0 0
```

ho guardes: control+o enter control+x ( si has fet servir nano)

-i ho muntes tot:

> mount -a


Si el que et passaba és que no et sortia la partició d'ubuntu al grub,
simplement entres al grub d'ubuntu desde debian, copies les línies de menu.lst que t'interessen i les enganxes al menu.lst de debian.

Salut.

Edito:

Si no saps segur quina és la partició que vols muntar pots fer servir:

> fdisk -l

---

### Post by kukat on 2009-05-15
Gràcies!!
Eren les dos coses....i estic fent-me un embolic!! jejej però ja està!
Hi havia un problema, i es que no es poden muntar particions ext4 al debian, hi ha que insta&#322;lar altre kernel de Linux:
[http://www.gulix.cl/foro3/como-tener-el-kernel-2-6-28-en-lenny-t1373.html](http://www.gulix.cl/foro3/como-tener-el-kernel-2-6-28-en-lenny-t1373.html)

Després comente si ha anat tot bé!

Moltes gràcies!

---

### Post by kukat on 2009-05-15
al final he optat per insta&#320;lar el grub a la particí de l'ubuntu amb
grub-install '(hd0,5)'

que al final ho he fet des del live CD amb un:

[B]sudo grub
root (hd0,5)
setup (hd0)
quit[/B]

Però ara em tira el següent error a l'iniciar Ubuntu:

Log of fsck -C -R -A -a 
Fri May 15 12:39:48 2009

fsck 1.41.4 (27-Jan-2009)
fsck.ext3: Unable to resolve 'UUID=be6e949d-592f-45ea-8eec-9e82857194a8'

fsck died with exit status 8

Fri May 15 12:39:48 2009
----------------

Lo demés està tot correctament amb el Debian i Ubuntu....He adjuntat el Grub per si les mosques


Salut!

---

### Post by kimet on 2009-05-15
Mira que les etiquetes UUID coincideixin al menu.lst i  al /etc/fstab.
Son etiquetes per identificar particions que usa ubuntu però no debian.

O sigui que això: UUID=be6e949d-592f-45ea-8eec-9e82857194a8 coincideixi amb el que diu a /etc/fstab sobre aquesta partició concretament.

O bé restaurar el grub que tenies a debian amb "super grub disk"

Fins ara.

---

