---
title: "Pot ser que el nucli 2.6-24-24 falli? [Era:  Compte!!! actualitzacio a kernel 2.6...]"
date: 2009-07-07
forum: Catalan Team
---

### Post by astarothvg on 2009-07-07
Hola a tothom, ahir vaig actualitzar el kernel com em demanaven les actualitzacions automàtiques i des de llavors que nomes tinc problemes, el paquet no es va poder instal-lar per falta de dependències , això diu, però esta instal·lat i ara no pita res, ni so, ni X, ni wi-fi ni res, tinc una nvidia i ni baixant els drivers de la pagina web no he pogut fer-lo funcionar.

Dades- Ubuntu [SIZE=2][SIZE=2]8.04 LTS, portatil asus G2s, tarja grafica Nvidia GeForce 8600M GT.
El error per terminal diu

S'està configurant linux-image-2.6.24-24-generic (2.6.24-24.55) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-24-generic
Running postinst hook script /sbin/update-grub.
[: 25: ==: unexpected operator
exec: 25: -a: not found
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: s'ha produït un error en processar linux-image-2.6.24-24-generic (--configure):
 el subprocés post-installation script retornà el codi d'eixida d'error 2
S'està configurant linux-source-2.6.24 (2.6.24-24.55) ...
S'han trobat errors en processar:
 linux-image-2.6.24-24-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
Ha fallat la instal·lació d'un paquet. S'està intentant la recuperació:
S'està configurant linux-image-2.6.24-24-generic (2.6.24-24.55) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-24-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.24-24.53 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.24-24.53 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
[: 25: ==: unexpected operator
exec: 25: -a: not found
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: s'ha produït un error en processar linux-image-2.6.24-24-generic (--configure):

Em podrie-ho ajudar siusplau.
Gracies
[/SIZE]
 
[/SIZE]

---

### Post by astarothvg on 2009-07-07
Ja esta, resulta que tot el merder venia de que vaig instal·lar el paquet Gfxboot i des-instal·lar el grub i per això donava problemes.

Perdoneu, m'he esverat molt de pressa, [-o< no ho tornaré a fer.

Salut.

---

