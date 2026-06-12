---
title: "Error ata2.00 exception Emask..."
date: 2008-03-10
forum: Argentina Team
---

### Post by pol666 on 2008-03-10
_**Esto le paso a un amigo**_



> Hola

Bueno, trate de probar el live cd (para despues instalarlo) del ubuntu 7.10 pero me encuentro con esta sorpesa

Primero, si inserto el cd y reinicio, no me lo detecta . Solo me lo detecta instalando el woobicd-boot desde windows (que viene dentro del cd de ubuntu)

Una vez que reinicio me aparece esto

[http://i32.tinypic.com/zjyn8n.jpg](http://i32.tinypic.com/zjyn8n.jpg)

Elijo Linux Ubuntu

Luego esto (en ese orden):

[http://i29.tinypic.com/33wtqg2.jpg](http://i29.tinypic.com/33wtqg2.jpg)

[http://i26.tinypic.com/f2rp03.jpg](http://i26.tinypic.com/f2rp03.jpg) (este por un segundo)

y por ultimo esto: [http://i32.tinypic.com/x4rac9.jpg](http://i32.tinypic.com/x4rac9.jpg)

[175.697311] ata2.00: exception Emask 0x0 Sact 0x0 SEtt 0x0 action 0x2 frozen
[175.697311] ata2.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096

...el problema es que en ningun momento me aparece la pantalla de inicio de ubuntu: [http://www.moixo.com/files/ubuntu-install-01.jpg](http://www.moixo.com/files/ubuntu-install-01.jpg)

El cd lo probe en otra computadora y funciona (el live cd, no se la instalacion, calculo que si, no lo probe xq es computadora de trabajo y si pasa algo con los datos a la hora de particionar o cualquier otra cosa me matan)

Hardware:
Procesador Amd Athlon de 1Ghz (K7)

512 de RAM

Disco Duro Sata de 80Gb

Chipset sis

Todo onboard (excepto una placa de red que no esta en uso)

Desde ya muchas gracias 

---

### Post by gmunioz on 2008-03-11
Hola pol...:

Para solucionar este problema prueba seguir los siguientes pasos:

   1. Al iniciar el live-cd
   
   2. Selecciona la opción F6.
   
   3. Al final de la línea de comandos que aparece (después del guión -) escribe:
      break=top.
   
   4. Presiona para continuar.
   
   5. Casi de manera inmediata, muestra el indicador de mensaje BusyBox y una línea de comandos.
   
   6. En la línea de comandos de busybox escribe los comandos: 
      
      modprobe ide_generic
      
      modprobe ide_cd
      
      modprobe ide_disk
      
      exit
  
O puedes intentar lo siguiente

   6. En la linea de comandos escribir:
      
      modprobe piix
      
      exit
  

Luego de instalar el sistema en la pc deberas:

    7.- Iniciar en una terminal pulsando

        Aplicaciones->Accesorios->Terminal

    
    8.-Crear un directorio

       sudo mkdir /media/ubuntu

    9.-Montar la particion del rígido donde fue instalado /, por ejemplo hda1

       sudo mount /dev/hda1 /media/ubuntu

   10.-Hacer que /media/ubuntu sea el directorio de trabajo

       sudo chroot /media/ubuntu

   11.-Editar el archivo /etc/initramfs-tools/modules

       sudo gedit /etc/initramfs-tools/modules
 
Añadir al final la línea
 
        piix

   12.-Actualizar el sistema ejecutando

       sudo update-initramfs -u

   13.-Reiniciar desde el rígido

Saludos.

---

### Post by pol666 on 2008-03-11
Bueno,  el usuario me dice que no puede ni siquiera inciar el live cd.. antes que tenga las opciones le tira ese error.

---

### Post by gmunioz on 2008-03-11
Hola pol...:

Que revise el setup de la pc para ver si los discos y cds estan bien seteados, si el lector de cd / dvd es PATA que le coloque el dip switch como cable select y lo enchufe en el extremo de la manguera de la ide0.
----Edito-----
Si esto no le funciona que intente con el alternate-cd
----fin edición------
Saludos

---

