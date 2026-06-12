---
title: "Instalar ubuntu por medio de un USB"
date: 2007-02-21
forum: Argentina Team
---

### Post by fetova on 2007-02-21
Hola! Me compre una lap y quiero ponerle xubuntu (pa' probar) pero resulta que no tiene unidad de cd, tengo una memoria de un giga, y quiero instalarlo desde el usb, he buscado, pero la verdad a lo que he encontrado, no le entiendo nada...

Agradeceria mucho la ayuda :)

---

### Post by BlackHero on 2007-02-21
la verdad que me la complicaste no tener letora tenes otras opciones si tenes placa de red podes mandarle booteo por red pero eso nunca lo hize podes buscar un howto acerca de eso, tenes otras opciones talves radicales si es que no le vas a comprar la letora de cd podes sacar el disco de la laptop y fijate que disco es tambien mandarle los conectores nesesarios y  coloralo en otra pc como master instalarlo nose bien como funcionaria despues si es que te lo instala con tal hard pero tendria que volverte a reconocer el hard y andaria bien, tambien tenes una opcion parecida a la que vos decis que es instalarlo en el usb drive y no desde el usb drive como decis vos entendes a lo que me refiero osea que el sistema operativo corra desde el drive pero man fijate que conectores tiene tu laptop para ver si de alguna forma le enganchas una lectora para simplificarte la vida =) saludos

---

### Post by fetova on 2007-02-21
> **BlackHero said:**
> la verdad que me la complicaste no tener letora tenes otras opciones si tenes placa de red podes mandarle booteo por red pero eso nunca lo hize podes buscar un howto acerca de eso, tenes otras opciones talves radicales si es que no le vas a comprar la letora de cd podes sacar el disco de la laptop y fijate que disco es tambien mandarle los conectores nesesarios y  coloralo en otra pc como master instalarlo nose bien como funcionaria despues si es que te lo instala con tal hard pero tendria que volverte a reconocer el hard y andaria bien, tambien tenes una opcion parecida a la que vos decis que es instalarlo en el usb drive y no desde el usb drive como decis vos entendes a lo que me refiero osea que el sistema operativo corra desde el drive pero man fijate que conectores tiene tu laptop para ver si de alguna forma le enganchas una lectora para simplificarte la vida =) saludos

la verdad si que me la complique, pero me gusto, dijeran por ahi: buena, bonita y barata,

Pues para la de red si tiene conexion y todo, LAN, Infrarojo, bluetooth, y wireless, asi que puedo hacer lo de por red, porque para una lectora necesito comprarla y me quede sin lana

tons por red como va? Gracias.

---

### Post by MeduZa on 2007-02-23
> **fetova said:**
> la verdad si que me la complique, pero me gusto, dijeran por ahi: buena, bonita y barata,

Pues para la de red si tiene conexion y todo, LAN, Infrarojo, bluetooth, y wireless, asi que puedo hacer lo de por red, porque para una lectora necesito comprarla y me quede sin lana

tons por red como va? Gracias.

si te deja botear desde un pendisk tendias q recrear el cd de boteo del OS en el pendriver que creo que se puede lo que no se es como :)

---

### Post by beuno on 2007-02-23
Pegale una mirada a estos:

[http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811)
[http://frontier05.blogspot.com/2006/01/installing-ubuntu-to-external-usb.html](http://frontier05.blogspot.com/2006/01/installing-ubuntu-to-external-usb.html)

---

### Post by ariel on 2007-02-25
Yo uso un hard disk usb para instalar las nuevas versiones de linux, desde los tiempos de breezy que no quemo un cd / dvd para esto.

Para complicarla un poco mas, el USB HD tiene muchas particiones. Una particion en especial es de 5GB y es la que uso para volcar el contenido de los ISOs de la distro que quiero probar.

Me acuerdo fue un poco complicado para hacerlo funcionar, pero una vez que funciona una vez (para breezy en mi caso), despues cuando queres probar una nueva distro, te bajas el iso y copias el contenido en la particion de 5GB, y chau. Asi instale breezy, dapper, edgy, feisty alphas, opensuse, knoppix etc etc. Funciona en mi desktop y en las laptops que uso en la oficina (dell y thinkpad)

Estas son las instrucciones (para Ubuntu) que me compile de paginas web que encontre, hace como un anio. Espero que todavia sean validas y te sean utiles.

Salu2
A


> Boot from USB disk with multiple partitions
    Grub method: {assumes that /dev/sda is your usb disk, sda1 the partition you want to boot from}
            1) Create the partition in the usb disk as needed: cfdisk /dev/sda; makeit bootable (boot flag), type 0E (FAT16 LBA)
            2) Format it: mkdosfs -F 16 -v /dev/sda1
            3) Mount the partition mount /dev/sda1 /mnt
            4) To setup Grub to boot from the USB drive, copy Grub's working files, namely, stage1, stage2 etc, to the partition
                mkdir -p /mnt/boot/grub
                cp -r /boot/grub/* /mnt/boot/grub
            5) Edit /mnt/boot/grub/device.map and set:
                (hd0) /dev/sda
                (hd1) /dev/sdb
                (hd2) /dev/sdc
            6) grub-install --root-directory=/mnt --no-floppy '(hd0)'
            7) edit /mnt/boot/grub/menu.lst and set:
                default 0
                timeout 5
                color cyan/blue white/blue
                title Ubuntu Installer in sda1
                root (hd0,0)
                kernel /casper/vmlinuz boot=casper initrd=/casper/initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash --
                initrd /casper/initrd.gz
                boot
            8 ) Mount your Dapper iso (or just open it with file-roller) can copy the whole thing to the new bootable partition in the usb disk
                sudo mount -o loop img.iso /media/iso   (sudo mount -t iso9660 -o loop <FILENAME.iso> /media/cdrom)
            9) Reboot your box, and in BIOS: ensure that your USB Boot is set to mode: USB-HDD ("Auto" mode worked for me too); reboot
         Note: to install a new release: delete everthing in the bootable partition _except_ the "/boot" folder; hacer un Empty-Trash; 
               por ultimo copiar todo el contenido del nuevo iso en la particion.

---

### Post by fetova on 2007-02-28
gracias a todos, estaba checando un post qu esta aca que habla de un .exe para instalar desde guindos, pero como el (...) que tenia la lap le modifico la particion primaria a 2Gb y no alcanzaba el espacio, use el partition magic para agrandarla, se reinicio y................... 

ya no prendio :guitar:

entonces el que me la vendio ofrecio hacer las instalaciones de los sistemas por mi ;) de cualquier manera, muchisimas gracias:)

---

