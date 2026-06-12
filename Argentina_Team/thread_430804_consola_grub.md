---
title: "consola grub"
date: 2007-05-02
forum: Argentina Team
---

### Post by jajajavi on 2007-05-02
Tengo instalado ubuntu en una [macbook]("https://help.ubuntu.com/community/MacBook") y metiendo mano perdí el acceso a ubuntu, ahora me aparece la consola grub> (Minimal BASH-like editing is suported). Alguien sabe cómo puedo recuperar el acceso a ubuntu?

---

### Post by Gideon26 on 2007-05-02
Hola por lo que decis desconfiguraste el Grub vas a tener que iniciar desde un live de ubuntu (es mas facil asi) y corregir el grub para eso fijate en el menu.lst como esta configurado hace las correcciones y con sudo update-grub queda solucionado para eso necesitas sabr como esta particionado el disco (en el menu.lst tenes que indicar donde estan los os )

---

### Post by jajajavi on 2007-05-02
entro desde el live cd de ubuntu edgy pero no sé cómo acceder a
la partición linux que tengo instalada. el disco está particionado así:

/dev/sda1 fat32 (supongo que es rEFIt)
/dev/sda2 hfs+ MacOsx
/dev/sda3 ext3 Ubuntu
/dev/sda4 linux-swap

---

### Post by Al_maverick on 2007-05-02
para montarlo, primero crea una carpeta:

```
cd /media
mkdir sda3
```

despues montas el disco:
```
mount -t ext3 /dev/sda3 /media/sda3
```

con eso ya deberias poder acceder

---

### Post by jajajavi on 2007-05-02
muchas gracias, accedo a **menu.lst ** que en este caso está en /media/sda3/dev/grub 

```
title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=158a8c8f-eebf-4bcd-950b-d643232b9ec1 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=158a8c8f-eebf-4bcd-950b-d643232b9ec1 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=158a8c8f-eebf-4bcd-950b-d643232b9ec1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=158a8c8f-eebf-4bcd-950b-d643232b9ec1 ro single
initrd		/boot/initrd.img-2.6.17-11-generic

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=158a8c8f-eebf-4bcd-950b-d643232b9ec1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=158a8c8f-eebf-4bcd-950b-d643232b9ec1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet
```

no sé como reconocer lo que está fallando, pero no creo que el problema esté ahí ya que en esta laptop el acceso a linux lo hace desde **rEFIt** (un switch entre macosx y otros sistemas operativos) y nunca me apareció el menú del grub como en lo en la pc.

rEFIt > [IMG]http://sourceforge.net/dbimage.php?id=70853[/IMG]

voy a insistir en los foros específicos, pero si a alguien se le ocurre cómo solucionarlo estaré agradecido, supongo que es algo del rEFIt...

---

### Post by Al_maverick on 2007-05-03
podrias probar cambiando el root=uuid por root=/dev/sda3

Pero me parece que vos ni llegas a ver el menu del grub, asi que el problema es anterior a este menu.

---

### Post by jajajavi on 2007-05-08
Lo solucioné booteando con el cd de Feisty como me dijeron en [**un foro**]("http://magarto.com/foro/index.php/topic,17.0.html") de por ahí.

```

sudo mkdir /a
sudo mount -t ext3 /dev/sda3 /a
sudo grub-install --root-directory=/a /dev/sda
sudo umount /a
```

Reinicio y arranca Ubuntu...

---

### Post by jajajavi on 2007-05-09
Esta entrada podría marcarse como** [RESOLVED]** no?

---

### Post by marianom on 2007-05-09
> **jajajavi said:**
> Esta entrada podría marcarse como** [RESOLVED]** no?

Podría si: entrá a tu post original (el primero) y editalo, abajo tenes la opción para marcarlo como resuelto.

---

