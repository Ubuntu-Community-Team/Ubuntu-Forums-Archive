---
title: "Recuperar Grub2- Ubuntu 12.04"
date: 2015-12-25
forum: Argentina Team
---

### Post by Vero1 on 2015-12-25
Hola,

Con la última actualización he perdido el Grub.

Reinstalé pero sigo igual.

Corrí como 4 veces el Boot-Repair pero no puede terminar por dependencias incumplidas y paquetes rotos.Tambien informa que no se puede corregir las dependencias.

No tengo idea de cómo se puede arreglar ésto.

Estoy usando un LiveCD por lo que no puedo ir a Synaptic para corregir los paquetes rotos.

Apreciaría si alguien me ayuda con este problema que ya se viene arrastrando desde hace varios días.

Desde ya muchas gracias.

---

### Post by Portaro on 2015-12-25
Ya intentaste el metodo manual?

[http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd)

---

### Post by Vero1 on 2015-12-25
Hola Portaro, gracias por contestar.
He probado todo lo que he encontrado en Internet y en Blogs.
Creo haber hecho tambien lo de tu Link, pero mañana probaré de nuevo porque ya hice tantas cosas que estoy mareada.
Luego te informo del resultado.

Saludos

Hola de nuevo,

Acabo de probar el Link que me pasaste.
Lamentablemente el resultado es el mismo. Dependencias incumplidas y paquetes rotos.
Hasta tanto alguien no me indique la manera de resolver estos dos errores, no puedo usar los programas de recuperaciòn.
Agradezco tu intención de ayudarme.

Saludos

---

### Post by Portaro on 2015-12-27
Pues necesitas a mi ver que tu Grub se configure hacia el disco pero no con el update.

O sea :
update-grub

ese comando es el que te da problemas de depndencia?

Si es asi habria que buscar una manera de indicar configurar el grub de forma manual en el mismo file of grub.

Si pudieras decir que dependencias te esta dando como (Broken) podria ayudar, puede que purgando eses pacotes el grub se pueda recuperar con el método que te di en el link.

---

### Post by Vero1 on 2015-12-27
Hola Portaro,

Justamente acabo de imprimir, despues de haber intentado nuevamente el Boot-Repair, el fallo.
Acá está lo que informa Terminal:

Corrigiendo dependencias... falló.
Los siguientes paquetes tienen dependencias incumplidas:
 dpkg : Rompe: fontconfig (< 2.11.1-0ubuntu5~) pero 2.8.0-3ubuntu9 está instalado
        Rompe: install-info (< 5.1.dfsg.1-3~) pero 4.13a.dfsg.1-8ubuntu2 está instalado
        Rompe: man-db (< 2.6.3-6~) pero 2.6.1-2 está instalado
 foomatic-db-engine : Depende: foomatic-filters (>= 4.0)
 initramfs-tools : Depende: initramfs-tools-bin (>= 0.103ubuntu15) pero 0.99ubuntu13 está instalado
                   Depende: klibc-utils (>= 2.0-1~) pero 1.5.25-1ubuntu2 está instalado
 libc-dev-bin : Depende: libc6 (< 2.16) pero 2.21-0ubuntu4 está instalado
 libc6-dev : Depende: libc6 (= 2.15-0ubuntu10) pero 2.21-0ubuntu4 está instalado
 libcairo-perl : Depende: perlapi-5.14.2
 libglib-perl : Depende: perlapi-5.14.2
 libgtk2-perl : Depende: perlapi-5.14.2
 liblocale-gettext-perl : PreDepende: perlapi-5.14.2
 libpango-perl : Depende: perlapi-5.14.2
 libperl5.14 : Depende: perl-base (= 5.14.2-6ubuntu2) pero 5.20.2-2 está instalado
 libpurple0 : Depende: perlapi-5.14.2
 libtext-charwidth-perl : Depende: perlapi-5.14.2
 libtext-iconv-perl : Depende: perlapi-5.14.2
 libuuid-perl : Depende: perlapi-5.14.2
 perl : Depende: perl-modules (>= 5.20.2-2) pero 5.14.2-6ubuntu2 está instalado
        Depende: libdb5.3 pero no es instalable
        Recomienda: rename pero no es instalable
 printer-driver-pxljr : Depende: foomatic-filters (>= 4.0.0~bzr156)
 upstart : Depende: libjson0 (>= 0.10-1.1ubuntu1) pero 0.9-1ubuntu1 está instalado
E: Error, pkgProblemResolver::Resolve generó cortes, esto puede haber sido causado por paquetes retenidos.
E: No se puede corregir las dependencias

He leido por ahí que habría que eliminar los paquetes que dan problemas.

Qué opinas del informe?

Gracias

---

### Post by enriquek2 on 2015-12-27
Estoy notando que este tipo de problems se ve mas seguido, creo que se debe a que se van acumulando kernels antiguos y esto se debe a que el usuario novato no se percata por que durante el arranque los diferentes kernels quedan enmascarados en "opciones avanzadas" y como las acualizaciones del kernel son casi semanale con un peso de 250 Mb, mas temprano que tarde te vas a quedar sin espacio en la partición root , a menos que hagas limpeza periódica de kernel viejos
muestra la salida al ejecutar
df -h
y
df -hi

---

### Post by Vero1 on 2015-12-27
Hola EnriqueK2, las salidas son éstas:
ubuntu@ubuntu:~$ df -h
S.ficheros     Tamaño Usado  Disp Uso% Montado en
/cow            1003M  219M  785M  22% /
udev             995M   12K  995M   1% /dev
tmpfs            401M  780K  401M   1% /run
/dev/sr0         702M  702M     0 100% /cdrom
/dev/loop0       673M  673M     0 100% /rofs
tmpfs           1003M  8,0K 1003M   1% /tmp
none             5,0M  4,0K  5,0M   1% /run/lock
none            1003M   80K 1003M   1% /run/shm

ubuntu@ubuntu:~$ df -hi 
S.ficheros     Nodos-i NUsados NLibres NUso% Montado en
/cow              215K    1,9K    213K    1% /
udev              211K     495    211K    1% /dev
tmpfs             215K     411    214K    1% /run
/dev/sr0             0       0       0     - /cdrom
/dev/loop0        156K    156K       0  100% /rofs
tmpfs             215K      19    215K    1% /tmp
none              215K       5    215K    1% /run/lock
none              215K       5    215K    1% /run/shm


Tiene ésto algo que ver con dependencias incumplidas y paquetes rotos?

Saludos

---

### Post by enriquek2 on 2015-12-27
Parece que a df lo estás ejecutando desde un live cd, primero debes montar las particiones boot / y home  y luego ejecuta los comandos indicados.
el comando df muestra el espacio linre y ocupado de las particiones  montadas.

---

### Post by Vero1 on 2015-12-28
Al no tener arranque, desde el principio que todo lo hago desde el Live CD.

Acá están las salidas.
ubuntu@ubuntu:~$ sudo mount /dev/sda2 /mnt
ubuntu@ubuntu:~$ sudo df -h
S.ficheros     Tamaño Usado  Disp Uso% Montado en
/cow            1003M   90M  914M   9% /
udev             995M  4,0K  995M   1% /dev
tmpfs            401M  780K  401M   1% /run
/dev/sr0         702M  702M     0 100% /cdrom
/dev/loop0       673M  673M     0 100% /rofs
tmpfs           1003M  8,0K 1003M   1% /tmp
none             5,0M  4,0K  5,0M   1% /run/lock
none            1003M  176K 1003M   1% /run/shm
/dev/sda2         81G  3,5G   74G   5% /mnt
/dev/sda3         81G  3,5G   74G   5% /mnt
/dev/sda2         81G  3,5G   74G   5% /mnt

ubuntu@ubuntu:~$ sudo mount /dev/sda3 /mnt
ubuntu@ubuntu:~$ sudo df -hi
S.ficheros     Nodos-i NUsados NLibres NUso% Montado en
/cow              215K     911    214K    1% /
udev              211K     493    211K    1% /dev
tmpfs             215K     411    214K    1% /run
/dev/sr0             0       0       0     - /cdrom
/dev/loop0        156K    156K       0  100% /rofs
tmpfs             215K      21    215K    1% /tmp
none              215K       4    215K    1% /run/lock
none              215K       5    215K    1% /run/shm
/dev/sda2          19M     49K     19M    1% /mnt
/dev/sda3          19M     49K     19M    1% /mnt
/dev/sda2          19M     49K     19M    1% /mnt
/dev/sda3          19M     49K     19M    1% /mnt
ubuntu@ubuntu:~$

---

### Post by enriquek2 on 2015-12-28
No se aprecia partición saturada
Lo que recomiendo es reinstalar, pero antes elimina la partición sda1 y la sda2 formateas todo ese espacio  para tener allí la / kn asli boot quedará dentro de la raiz y no  en partición separada que fancamente no tiene sentido y lo único que consigues es sacrificar una priimaria que puedes destinarlas para otros fines
esta instalación la haces sin internet para que resulte mas rápido, después , si todosale bien , ejecuta
Alt+F2
en el cuadro pones a ejecutar
sudo update-manager -d
con eso terminás instalñando la versión  14.04

---

### Post by Vero1 on 2015-12-28
Gracias por tu respuesta.

Lo que me ineteresa en estos momentos es cómo arreglar las dependencias incumplidas y los paquetes rotos.

No quiero perder nada de lo que tengo en el Escritorio (fotos, películas, etc) 

Tamb ien necesito poder bootear normalmente, cosa que no logro por las dependencias y paquetes rotos.

DESPUES de haber resuelto éso, pensaré en upgrade a 14.04.

Si me podés ayudar en lo que necesito te voy a agradecer.

Saludos

---

### Post by enriquek2 on 2015-12-28
Para arrncar el sistema usaría el Super Grub2 Disk
duando arranque , ejecutá en terminal
sudo grub-mkconfig && sudo grub-install /dev/sdba && sudo update-grub
Para el tema de paquetes rotos, ejecutá
sudo apt-get install --fix-broken

---

### Post by Vero1 on 2015-12-28
Gracias Enrique,

Debo ir a un Cyber a grabar el SuperGrub2Disk, ya que los que tengo(son 3) no sirven.

Despues volveré contigo.

saludos

Lamentablemente  no pude grabar el SuperGrub2Disk.
Tendré que esperar a que alguien me indique qué hacer con los paquetes rotos y las dependencias.
Gracias.

Saludos

Hice la prueba de grabar en un Pendrive Grub2.
Despues de bootear con él, me sale Grub Rescue.
Yo tengo los comandos que hay que usar pero cuando llega a "insmod" empiezan los problemas. No reconoce el comando y de ahí en adelante no se puede seguir.
Veo que no hay forma de hacer nada sin arreglar las benditas dependencias y los paquetes rotos.
Lástima que nadie parece conocer la respuesta que, seguramente, existe.

Gracias

---

### Post by enriquek2 on 2015-12-28
Prueba con chroot, imprime los siguientes comandos que debes ejecutar luego de arrancar con el livecd
Asumiendo que sda2 es la partición root y que sda1 es la /boot , arranca con el livecd y ejecuta estos comandos
sudo su
mount /dev/sda2 /mnt
mount --bind /dev/sda1 /mnt/boot 
mount --bind /dev /mnt/dev 
mount --bind /dev/pts /mnt/dev/pts
mount --bind /proc /mnt/proc
mount --bind /sys /mnt/sys
chroot /mnt

apt-get update
apt-get -f install
apt-get install --reinstall ubuntu-desktop
apt-get dist-upgrade
apt-get clean
apt-get autoremove
grub-mkconfig -o /boot/grub/grub.cfg
grub-install --root-directory=/mnt /dev/sda
grub-install --recheck /dev/sda

init 6

---

### Post by Vero1 on 2015-12-28
Mirá Enrique.
Antes que nada. Le saqué el boot a sda1 y ahora lo tiene sda2, así que voy a cambiar la orden por sda2.
Hasta aqui llegué:
ubuntu@ubuntu:~$ sudo su
root@ubuntu:/home/ubuntu# mount /dev/sda2 /mnt
root@ubuntu:/home/ubuntu# mount --bind /dev/sda2 /mnt/boot 
mount: No es un directorio

---

### Post by enriquek2 on 2015-12-28
Entrá a gparted en el livecd y poné cual es la partición root , sospecho que es sda3 
aclará cual es la partición sda1

---

### Post by Vero1 on 2015-12-28
Sospechás mal. sda3 es /home  y sda2 es Raíz.

sda1 originalmente era /boot ( le saqué el boot)
sda2 / Raiz donde está el boot ahora
sda3 /home
sda4 /lugar para Windows

no me acuerdo con qué programa enviaba un screenshot por eso no te lo mando.

Ahora que lo pienso, no será que algo quedó en sda1 que está interfiriendo?

---

### Post by enriquek2 on 2015-12-28
Creo que es lo mas probable, el proceso correcto requiere de varios pasos , tratá de indicar los pasos que empleaste.
Por esto es que te recomiendo reinstalar  sin /boot separada uniendo ambas particiones y de paso dispondrás de una primaria para usarla con otros fines.

---

### Post by Vero1 on 2015-12-29
Reinstalé el sistema 2 veces, formateando sda1 y sda2 (ex-boot y Raiz). Ahora, viendo Gparted dice que sda1 tiene usados 263 Mib. Cómo es posible si se formateó 2 veces?

 O sea: primero format sda1 para eliminar los Mib que aún tiene. Despues extender sda2 hacia la izquierda para integrar sda1. Despues poner /boot en sda2. 
Ésto con qué comando? y al final, sacándole unos Gib a sda2(raiz) ocuparlos con Swap( 1 Gb?) porque tengo 2Gb de RAM y tiene que ser la mitad de la Memoria Ram no?

Quedaría sin sda1, eso no importa? o sea sería sda2 como Raiz(cómo indico que Boot va en Raiz?), sda3 como Home, sda4(actualmente lugar para Win) y sda5 como Swap. Podría ser así? Se puede hacer?

Bueno, no sé si entenderás todo lo que puse.

Si estás de acuerdo haré los cambios enseguida.

---

### Post by enriquek2 on 2015-12-29
Te estás haciendo un lío barbaro , la cosa es mucho mas simple
1- Arranca con el livecd, abre gparted y borra las particiones sda1 y sda2, esto hará que se cree un espacio no asignado que será la suma de esas dos particiones
2- particiona y formatea ese espacio no asignado destlnanado los espacios para  la nueva root y la swap
3- Definidas las nuevas particiones procedes a instalar el sistema
4- llegado el momento, te pedirá respecto al particonado, eliges manual y te va a mostrar un cuadro de diálogo podrliaser por ejemplo
partición    punto de montaje  sistema de archivos    formatear
sda1           /                               ext4                                tildss el casillero
sda2          swap                        swap                              tildss el casillero
sda3          /hume                       ext4                               este casillero lo dejas sin tildar o marcar


Sigue con la instalación

---

### Post by Vero1 on 2015-12-29
Pero  hablas de la nueva root y la swap pero y el boot?

---

### Post by enriquek2 on 2015-12-29
boot quedará instalado dentro de la nueva root, o sea ya no estará en partición separada

---

### Post by Vero1 on 2015-12-29
ok ya eliminé las dos particiones y queda un espacio sin asignar de 88 Gib.
Lo que no me queda claro es que no se indica nada sobre el Boot. 
Vos decís que quedará en la nueva Root pero no se indica en ningun lado?

---

### Post by enriquek2 on 2015-12-29
boot es uno de lo tantos directorios del sistema que puede estar dentro de la raiz o en partición separada, lo mismo puede pasar por ejemplo con /usr /tmp y hasta /home , todo dependerá de una decisión de conveniencia, por ejemplo si tienes poco espacio para instalar el sistema, podrías definir a /usr en partición separada, lo mismo se aplica con boot que se instalará con el sistema ya sea dentro de la raiz o en partición separada.

Si tienes dudas respecto a la instalación manual, sugiero buscar en la redn que está plagado de turoriales y hasta de videos

---

### Post by Vero1 on 2015-12-29
Hurra!!!!
Particioné, reinstalé y tengo todo tal cual estaba, cosa que me alegra infinitamente.
Lo único que la pantalla de bienvenida es como visitante pero al reiniciar me sale mi escritorio.

Te quedo muy agradecida por tu ayuda y el tiempo invertido.

(despues de la instalación tuve que actualizar 900 archivos...)

Bueno EnriqueK2, ojalá algún dia pueda devolverte el favor.

Muchos saludos y Feliz Año Nuevo!!!

---

