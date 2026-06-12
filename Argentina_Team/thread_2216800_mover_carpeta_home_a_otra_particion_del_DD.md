---
title: "mover carpeta /home a otra particion del DD"
date: 2014-04-14
forum: Argentina Team
---

### Post by dimas-belisario on 2014-04-14
soy nuevo usuario de ubuntu estoy usando la version 12.04 en mi DD tengo una particion para window (ntfs), para ubuntu (etx4), swap, y otra para documentos (fat32). mi interrigante es como hago para q los documentos que se guardan en /home/ tanto los del administrador como los del usuario de ubuntu se guarden en la particion que cree para documentos (fat32), para que puedan ser vistos por usuarios que usen window
busque tutoriales acerca de como realizar esto pero creo que falle en algun paso porque al reiniciar me dice que fallo al montar el Home presione S para desmontar o M para "hacer halgo manualmente (no recuerdo bien esta opcion XD)"
Adjunto imagen del DD  
[IMG]http://i59.tinypic.com/i4466p.jpg[/IMG]

   
segun lo poco que logre entender:
primero deberia crear una carpeta para montar la particion 
 use este comando


[LIST]
[*]sudo mkdir /home/ubuntu
[/LIST]

luego al archivo fstab le agregue esta linea al final

[LIST]
[*] /dev/sda7 /home/ubuntu fat32 vfat iocharset=utf8,umask=000 0 2
[/LIST]


luego este comando

   
[LIST]
[*]sudo mount -t vfat /dev/sda7 /home/ubuntu -o defaults
[/LIST]
supuestamente realixe todo bien pero al reiniciar me el error hantes descripto
que estoy haciendo mal o que me falto hacer?

---

### Post by gmunioz on 2014-04-14
En principio es muy mala idea guardar documentos en sistema de archivos fat32, particularmente no uso sistemas de archivos de Microsoft en Gnu/Linux, pero de usarlos usaría ntfs.
Debes montar la partición en un directorio (carpeta) de tu usuario, por ejemplo /home/tuusaurio/compartida y entonces en una terminal sería
mkdir compartida
sudo su
nano /etc/fstab
(en el archivo que se abre agregar:)
/dev/sda7 /home/tuusuario/compartida    vfat	auto,user,exec,rw,async 0 0
(control + O guarda, control + X cierra)
reboot

---

### Post by dimas-belisario on 2014-04-15
cambie la particion de formato fat32 a formato ntfs 
agregue esta linea
[LIST]
[*]/dev/sda7 /home/usuario/respaldo     ntfs	auto,user,exec,rw,async 0 0
[/LIST]
y funciono bien, pero cuando inicio la pc con un usb conectado lo reconoce como /sda, y el DD como /sdb
¿ existe alguna forma para que el DD sea siempre /sda ?

---

### Post by gmunioz on 2014-04-15
Si bien no tiene que ver con el tema y deberás haber puesto otro post al respecto, en beneficio de quienes consulten el foro, va mi sugerencia:
Una opción podría ser deshabilitar de la bios la opción de iniciar de un usb u ordenar las opciones de booteo para que inicie en primer lugar desde el disco interno.
Otra opción sería que el disco interno, que seguramente es sata, ya que de ser ide tendría que ser reconocido como /dev/sda antes que cualquiera, verifiques esté instalado en el sata0 ó sata1, según se identifique en tu mother el primer sata.
No obstante cabe aclarar, que para evitar los contratiempos que puedan surgir de estos cambios de /dev/sdx existen los UUID de las particiones, desde hace tiempo se aconseja montar en /etc/fstab las particiones según segun su UUID, la misma se obtiene con el comando:
sudo su
blkid /dev/sda7
Para el caso de la particion ex fat32 y actual ntfs.
Las líneas de montaje deberían ser para cumplir con los protocolos:
#/dev/sda7 es /home/usuario/respaldo
UUID=lo.que.informo.blkid   /home/usuario/respaldo ntfs auto,user,exec,rw,async 0 0
Con esta medida cambiando discos e incluso ordenadores, no habría conflicto alguno con las particiones, ya que las UUID son únicas.

---

