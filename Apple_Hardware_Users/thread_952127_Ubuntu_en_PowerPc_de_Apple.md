---
title: "Ubuntu en PowerPc de Apple"
date: 2008-10-18
forum: Apple Hardware Users
---

### Post by snowsurfer on 2008-10-18
Necesito ayuda con una parte de la instalacion de ubuntu. Todo va de perlasss hasta que me pide en "Los puntos de Montaje", la particion de Apple_Bootstrap. 
El hecho es que la particion que pide de 800k para las apple de NewWorld ya la hice con Mac-Fdisk , pero igual me la pide, no se que onda. Si alguien sabe algo please ayuda.

Tengo en total de  4 particiones: 
1) /boot           Apple_BootStrap
2) /                ext3 de Unix
3) /swap            particion swap
4) /home            ext3

Ya me eh leido toda la informacion en la web pero hay algo que debe estar faltando....

---

### Post by squee on 2008-10-19
It will be hard for you to get help if you dont post in English. Maybe you could try another help boards.

---

### Post by tiresia on 2008-10-19
> **snowsurfer said:**
> Necesito ayuda con una parte de la instalacion de ubuntu. Todo va de perlasss hasta que me pide en "Los puntos de Montaje", la particion de Apple_Bootstrap. 
El hecho es que la particion que pide de 800k para las apple de NewWorld ya la hice con Mac-Fdisk , pero igual me la pide, no se que onda. Si alguien sabe algo please ayuda.

Tengo en total de  4 particiones: 
1) /boot           Apple_BootStrap
2) /                ext3 de Unix
3) /swap            particion swap
4) /home            ext3
.

Usually you don't need to use yourself mac-fdisk - the installer does it for you. Anyway, after you make the partitions, you need to write them to the disk (use 'w' and check it with 'P'). 
Can you please tell us the model of you Mac and which Ubuntu are you trying to install.

P.S. I can't speak spanish, but I understand quite well. If you can't write in english, you can send me a private message in spanish

---

### Post by snowsurfer on 2008-10-19
its ok i can speak a little of english.
 
I have an Imac PowerPc G4 - 700 Mhz.  The thing is that I already make the reorder of the partitions and then I press w and saw the table after a did it, and its fine. But it keeps telling that i dont have de apple_bootstrap partition.
Im studing Informatic Eng, and i really want to get envolvd with this os.

---

### Post by tiresia on 2008-10-19
With mac-fdisk you create the partitions. After that you may want to format these partitions with a file system. The apple_bootstrap partition needs hfs in order to install yaboot (the bootloader) on it.
The tool for it is 'hformat'. The hformat command is contained in the hfsutils package.
You can have more information from the man-pages ('man hformat')
Here you can find how it works, if you want to prepare an usb stick to install ubuntu
[https://help.ubuntu.com/8.04/installation-guide/powerpc/boot-usb-files.html](https://help.ubuntu.com/8.04/installation-guide/powerpc/boot-usb-files.html)

---

### Post by snowsurfer on 2008-10-19
> **tiresia said:**
> With mac-fdisk you create the partitions. After that you may want to format these partitions with a file system. The apple_bootstrap partition needs hfs in order to install yaboot (the bootloader) on it.
The tool for it is 'hformat'. The hformat command is contained in the hfsutils package.
You can have more information from the man-pages ('man hformat')
Here you can find how it works, if you want to prepare an usb stick to install ubuntu
[https://help.ubuntu.com/8.04/installation-guide/powerpc/boot-usb-files.html](https://help.ubuntu.com/8.04/installation-guide/powerpc/boot-usb-files.html)

ok de lujo!! i will try that later and i tell you how is it working out.
Gracias!!!

---

### Post by mkvnmtr on 2008-10-19
Salaudos, Ya puse Ubuntu en me Ibook G4 sin problemas. Dime cuanto ram tiene, que grande  el disco y como quieres poner las systemes. Quieres dual boot con Mac os y Ubuntu o solomente Ubuntu?. No debes tiener problemas con hacienda partitiones. Debe hacer automatico el disco desktop.

---

