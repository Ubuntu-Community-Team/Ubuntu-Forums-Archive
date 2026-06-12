---
title: "Com restaurar un sistema sense nucli instal·lat?"
date: 2009-11-08
forum: Catalan Team
---

### Post by jmaspons on 2009-11-08
Hola,

Sembla ser que vaig vaig desinstal·lar tots els nuclis (linux-image*) que tenia i ara no puc arrencar el sistema.

He arrencat amb un cd autoexecutable i he intentat instal·lar un nucli entrant al sistema amb chroot:

```

ubuntu@ubuntu:~$ sudo chroot /media/disk/
root@ubuntu:/# mount proc/
root@ubuntu:/boot# sudo apt-get install linux-image-2.6.31-14-generic
sudo: unable to resolve host ubuntu
S'està llegint la llista de paquets... Fet
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat... Fet
linux-image-2.6.31-14-generic ja es troba en la versió més recent.
0 actualitzats, 0 nous a instal·lar, 0 a suprimir i 0 no actualitzats.
2 no instal·lats o suprimits completament.
Després d'aquesta operació s'empraran 0B d'espai en disc addicional.
No es pot escriure el registre, ha fallat openpty() (no s'ha muntat /dev/pts?)
S'està configurant linux-image-2.6.31-14-generic (2.6.31-14.48) ...
Running depmod.
/usr/sbin/update-initramfs: 553: cannot create /dev/null: Permission denied
update-initramfs: Generating /boot/initrd.img-2.6.31-14-generic
/usr/sbin/mkinitramfs: 222: cannot create /dev/null: Permission denied

[...]

/usr/sbin/mkinitramfs: 308: cannot create /dev/null: Permission denied
/usr/sbin/mkinitramfs: 309: cannot create /dev/null: Permission denied
/usr/sbin/mkinitramfs: 309: cannot create /dev/null: Permission denied
/usr/sbin/mkinitramfs: 314: cannot create /dev/null: Permission denied
/usr/sbin/mkinitramfs: 314: cannot create /dev/null: Permission denied
/usr/share/initramfs-tools/hooks/brltty: 20: cannot create /dev/null: Permission denied
/usr/share/initramfs-tools/hooks/brltty: 20: cannot create /dev/null: Permission denied
/usr/share/initramfs-tools/hooks/brltty: 22: cannot create /dev/null: Permission denied
/usr/share/initramfs-tools/hooks/brltty: 22: cannot create /dev/null: Permission denied
/usr/share/initramfs-tools/hooks/cryptroot: 473: cannot create /dev/null: Permission denied
/usr/share/initramfs-tools/hooks/cryptroot: 473: cannot create /dev/null: 

[...]

 Permission denied
/usr/share/initramfs-tools/hooks/cryptroot: 491: cannot create /dev/null: Permission denied
/usr/share/initramfs-tools/hooks/framebuffer: 21: cannot create /dev/null: Permission denied
/usr/share/initramfs-tools/hooks/framebuffer: 21: cannot create /dev/null: Permission denied
/usr/share/initramfs-tools/hooks/framebuffer: 21: cannot create /dev/null: Permission denied
/usr/share/initramfs-tools/hooks/framebuffer: 21: cannot create /dev/null: Permission denied

[...]

/usr/share/initramfs-tools/hooks/dmsetup: 22: cannot create /dev/null: Permission denied
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.31-14.48 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.31-14.48 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
/sbin/update-grub: 15: cannot create /dev/null: Permission denied
sh: cannot create /dev/null: Permission denied
sh: cannot create /dev/null: Permission denied
Searching for GRUB installation directory ... found: /boot/grub
findfs: unable to resolve 'UUID=97fa05cd-7cec-4d32-8f37-9e08b7bb8ff3'
Cannot determine root device.  Assuming /dev/hda1
This error is probably caused by an invalid /etc/fstab
/usr/sbin/update-grub: line 390: /dev/null: Permission denied
/usr/sbin/update-grub: line 251: /dev/null: Permission denied
/usr/sbin/update-grub: line 257: /dev/null: Permission denied
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.31-14-generic
Found kernel: /boot/memtest86+.bin
Can't open /dev/null: Permission denied
User postinst hook script [/sbin/update-grub] exited with value 13
dpkg: s'ha produït un error en processar linux-image-2.6.31-14-generic (--configure):
 el subprocés installed post-installation script retornà el codi d'eixida d'error 13
dpkg: problemes de dependències impedeixen la configuració de linux-image-generic:
 linux-image-generic depèn de linux-image-2.6.31-14-generic; tot i així:
  El paquet linux-image-2.6.31-14-generic encara no està configurat.
dpkg: s'ha produït un error en processar linux-image-generic (--configure):
 problemes de dependències - es deixa sense configurar
No apport report written because the error message indicates its a followup error from a previous failure.
S'han trobat errors en processar:
 linux-image-2.6.31-14-generic
 linux-image-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:/boot# 


```

Avanç d'això havia instal·lat el mateix paquet fent "dpkg intall /var/cache/apt/archives/linux-image-2.6.31-14-generic"

Com ho puc arreglar?

Gràcies

---

