---
title: "[SOLVED] [Ayuda]Compartir Carpetas entre linux"
date: 2008-02-22
forum: Argentina Team
---

### Post by lega on 2008-02-22
Hola,les cuento mi problema, tengo dos maquinas en red,una es mia y la otra de mi esposa.
Hasta ahora no habia tenido necesidad de compartir archivos entre ellas, pero ahora quiero pasarle una fotos asi que me dispuse a compartir carpetas, pero evidentemente algo no estoy haciendo o algo estoy haciendo mal

Les cuento que hice, fui a Carpetas compartidas me pregunto que sistema quería usar y dije NFS y me instalo los paquetes necesarios, luego en un cuadro que se me abrió añadí la carpeta a compartir y puse la ip de la maquina cliente aparentemente todo esta bien.

Luego en la pc cliente a la que tambien le instale los paquetes nfs,tipee lo siguiente :
sudo mount -t nfs 10.0.0.4:/home/leonardo/Documentos/fotos /home/silvi/fotos
entiendo que con este comando estoy montando mi carpeta fotos en la carpeta fotos (previamente creada) en la pc de mi esposa.

Pues bien, el comando me devuelve esto:mount 10.0.0.4:/home/leonardo/Documentos/fotos /home/silvi/fotos 
failed.reason given by server: permiso denegado

un compañero me dijo que edite el archivo exports y me fijara si figuraban las carpetas compartidas
```
# /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync) hostname2(ro,sync)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt)
# /srv/nfs4/homes  gss/krb5i(rw,sync)
#
/home/leonardo/Documentos/fotos silvi-desktop

```
aparentemente figura no?
entonces me dijeron que restartee el servidor nfs, que me tira esto:
```
  sudo /etc/init.d/nfs-kernel-server restart
 * Stopping NFS kernel daemon                                            [ OK ] 
 * Unexporting directories for NFS kernel daemon...                      [ OK ] 
 * Exporting directories for NFS kernel daemon...                               exportfs: No options for /home/leonardo/Documentos/fotos silvi-desktop: suggest silvi-desktop(sync) to avoid warning
exportfs: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export "silvi-desktop:/home/leonardo/Documentos/fotos".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x
exportfs: silvi-desktop has non-inet addr
exportfs: silvi-desktop has non-inet addr
                                                                         [ OK ]
 * Starting NFS kernel daemon                                            [ OK ] 



```
despues de esto intento otra vez y sigue tirando el mismo error acceso denegado, alguien me podra dar una mano y decirme que cuerno estoy haciendo mal?

Mi pc tiene Unbuntu 7.10 y la de mi esposa la version 7.04 ambas con ip fija 10.0.0.4/5 y acceso a internet sin problemas atravez de un modem router con ip 10.0.0.2

Gracias de antemano por la ayuda.

---

### Post by Hei Ku on 2008-02-22
es porque te falta definir que permisos tiene para el share. Te muestro un ejemplo de como los tengo yo.

/home 192.168.1.100(rw,no_root_squash,async)

por otro lado, tenes que estar seguro que si le pones el nombre de host, lo tengas agregado en tu lista de hosts. Si no, no puede resolver la direccion y tampoco te va a dejar acceder. O sea, te conviene usar una ip, mas q el nombre de host, salvo q tengas un servidor dns local.

---

### Post by spg76 on 2008-02-22
Tenes que darle permisos en el archivo /etc/exports a la carpeta que quieras compartir.
Pone, por ejemplo:
```
/home/leonardo/Documentos/fotos(rw,no_root_squash,async)
```
Creo que con eso debería funcionar.

EDIT: Hei Ku me madrugaste, cuando pude publicar ya habías respondido. Perdón.

---

### Post by lega on 2008-02-22
Gracias a ambos por la respuesta, ahi funciono :) una consulta mas, puedo hacer que las carpetas se monten automaticamente al iniciar la pc? como lo hago?

Muchisimas gracias otra vez por la ayuda.

---

### Post by Hei Ku on 2008-02-22
Si, tenes que agregarlas al /etc/fstab como cualquier otro sistema de archivos que montas

Esta es la linea q corresponde con el ejemplo anterior, en el fstab del cliente.

192.168.1.50:/ftp /mnt/ftp nfs rsize=8192,wsize=8192,timeo=14,intr,user,auto

---

### Post by lega on 2008-02-23
Muchisimas gracias por la ayuda, ya pude hacerlo :)

Saludos, Gracias

---

### Post by Hei Ku on 2008-02-23
Buenisimo. Entonces marcalo como Solved en las Thread Tools

---

