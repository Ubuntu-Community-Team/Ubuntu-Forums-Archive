---
title: "Grub2 y Boot"
date: 2015-07-11
forum: Argentina Team
---

### Post by Vero1 on 2015-07-11
Despues de la ùltima actualizaciòn para Ubuntu 12.04, al reiniciar el día siguiente, me encuentro con que sale pantalla negra.

Como ya me había pasado en una ocasiòn y utilicé Boot-repair(quedó solucionado) volví a usar esta herramienta, en base a instrucciones de AskUbuntu.

Cuando estaba terminando, sale una advertencia: apt error detectado y que corriera desde Terminal: sudo chroot "mnt/boot-sav/sda2" apt- get -f

Despues de hacer muchas operaciones me pone: E- internal error, no file name for liblzma5 y no se termina el boot-repair.

Hace 3 días que vengo luchando con este problema, probando sugerencias encontradas en Internet.

En estos momentos, cuando prendo la máquina me sale en pantalla negra una leyenda y al pie el promt de Grub> con cursor titilante, como esperando alguna orden.

Con el TAB salen muchas órdenes pero no sé cuál usar para poder arrancar el sistema.

Agradeceré su ayuda. 

:-)

---

### Post by gmunioz on 2015-07-11
Para el caso de que se trate del  prompt de la consola de rescate del Grub.
Prueba  acceder a la lista de particiones disponibles ejecutando el comando:
> ls
Este comando podría mostrar las particiones disponibles, algo asi como:
> (hd0) (hd0,1) (hd1) (hd1,1) (hd1,5) (hd2) (hd2,1) (hd3) (hd3,1)
Si es así, hace falta descubrir qué partición contiene la carpeta /boot/grub, basta con ir haciendo un ls para cada una de las particiones:
> ls (hd0,1)/
Una vez descubierta la partición en la que se encuentra la carpeta boot, se añade el prefijo correspondiente para que el Grub sepa dónde se encuentra:
> set prefix=(hd0,1)/boot/grub
Queda ejecutar el siguiente comando:
> insmod (hd0,1)/boot/grub/linux.mod
Configurar la partición root mediante el comando:
> set root=(hd0,1)
Cargar la imagen del kernel Linux, que se descubre ejecutando el comando &#8220;ls&#8221; en el directorio boot:
> linux /boot/vmlinuz-2.6.32-23-generic root=/dev/sdb1
El punto de montaje sda1, se establece conforme al nombre de la partición: (hd0,1) es sda1, mientras que (hd0,2) sería: sda2.
A continuación se carga el kernel:
> initrd /initrd.img
Y se inicia el sistema:
> boot
Si el sistema inició, reinstala el Grub
> grub-install /dev/sda

Si esto no funciona, es necesario contar con live-dvd/usb.
Inicia con la distribución live.
Terminada la carga abre una terminal.
Ejecuta en ella:
> sudo -i
fdisk -l
Fdisk te informará como se denominan tus discos y particiones
Supongamos, siguiendo el ejemplo anterior, que tu disco es /dev/sda
Y que tu partición root, / es /dev/sda1, continua ejecutando en la terminal:
> umount /dev/sda1
fsck -y /dev/sda1
mount /dev/sda1 /mnt
mount --bind /dev /mnt/dev 
mount --bind /dev/pts /mnt/dev/pts
mount --bind /proc /mnt/proc
mount --bind /sys /mnt/sys
chroot /mnt
A partir de este momento te encuentras ejecutando en la terminal
el sistema instalado en el disco rígido, queda repararlo, actualizarlo y
reinstalar el Grub mediante los comandos:
> dpkg --configure -a
apt-get -f install
apt-get -m install
apt-get update
apt-get dist-upgrade
apt-get install --reinstall ubuntu-desktop
grub-mkconfig -o /boot/grub/grub.cfg
grub-install --root-directory=/mnt /dev/sda
grub-install --recheck /dev/sda
apt-get clean
apt-get autoremove
umount /mnt
reboot


---

### Post by Vero1 on 2015-07-12
Hola Gabriel, muchas gracias por contestar. Usé los comandos de Terminal. Cuando llego a apt-get -f install, me sale:
root@ubuntu:/# dpkg --configure -a
dpkg: problemas de dependencias impiden la configuración de libdbus-1-3:
 libdbus-1-3 depende de libc6 (>= 2.17); sin embargo:
  La versión de `libc6' en el sistema es 2.15-0ubuntu10.12.
dpkg: error al procesar libdbus-1-3 (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de compiz:
 compiz depende de compiz-core (>= 1:0.9.12.1+15.04.20150410.1-0ubuntu1); sin embargo:
  La versión de `compiz-core' en el sistema es 1:0.9.7.12-0ubuntu4.
 compiz depende de compiz-plugins-default (>= 1:0.9.12.1+15.04.20150410.1-0ubuntu1); sin embargo:
  La versión de `compiz-plugins-default' en el sistema es 1:0.9.7.12-0ubuntu4.
dpkg: error al procesar compiz (--configure):
 problemas de dependencias - se deja sin configurar
Configurando libjson-c2 (0.11-4ubuntu2) ...
dpkg: problemas de dependencias impiden la configuración de libcgmanager0:
 libcgmanager0 depende de libdbus-1-3 (>= 1.0.2); sin embargo:
 El paquete `libdbus-1-3' no está configurado todavía.
dpkg: error al procesar libcgmanager0 (--configure):
 problemas de dependencias - se deja sin configurar
Configurando liblzma5 (5.1.1alpha+20120614-2ubuntu2) ...
Configurando libnih1 (1.0.3-4ubuntu27) ...
Configurando gconf2 (3.2.5-0ubuntu2) ...
gconftool-2: /lib/i386-linux-gnu/libc.so.6: version `GLIBC_2.17' not found (required by /lib/i386-linux-gnu/libdbus-1.so.3)
dpkg: error al procesar gconf2 (--configure):
 el subproceso instalado el script post-installation devolvió el código de salida de error 1
dpkg: problemas de dependencias impiden la configuración de libnih-dbus1:
 libnih-dbus1 depende de libdbus-1-3 (>= 1.2.16); sin embargo:
 El paquete `libdbus-1-3' no está configurado todavía.
dpkg: error al procesar libnih-dbus1 (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de compiz-gnome:
 compiz-gnome depende de libdecoration0 (>= 1:0.9.8.2); sin embargo:
  La versión de `libdecoration0' en el sistema es 1:0.9.7.12-0ubuntu4.
 compiz-gnome depende de libglib2.0-0 (>= 2.37.3); sin embargo:
  La versión de `libglib2.0-0' en el sistema es 2.32.4-0ubuntu1.
 compiz-gnome depende de libmetacity-private2 (>= 3.12.0); sin embargo:
  El paquete `libmetacity-private2' no está instalado.
 compiz-gnome depende de libpango-1.0-0 (>= 1.14.0); sin embargo:
  El paquete `libpango-1.0-0' no está instalado.
 compiz-gnome depende de libpangocairo-1.0-0 (>= 1.14.0); sin embargo:
  El paquete `libpangocairo-1.0-0' no está instalado.
 compiz-gnome depende de gconf2 (>= 2.28.1-2); sin embargo:
 El paquete `gconf2' no está configurado todavía.
 compiz-gnome depende de session-migration; sin embargo:
  El paquete `session-migration' no está instalado.
 compiz-gnome depende de compiz-plugins-default (= 1:0.9.12.1+15.04.20150410.1-0ubuntu1); sin embargo:
  La versión de `compiz-plugins-default' en el sistema es 1:0.9.7.12-0ubuntu4.
 compiz-gnome depende de gnome-settings-daemon-schemas (>= 3.4.2-0ubuntu9); sin embargo:
  El paquete `gnome-settings-daemon-schemas' no está instalado.
 compiz-gnome depende de python3-gi; sin embargo:
  El paquete `python3-gi' no está instalado.
dpkg: error al procesar compiz-gnome (--configure):
 problemas de dependencias - se deja sin configurar
Procesando disparadores para libc-bin ...
ldconfig deferred processing now taking place
Se encontraron errores al procesar:
 libdbus-1-3
 compiz
 libcgmanager0
 gconf2
 libnih-dbus1
 compiz-gnome
root@ubuntu:/# apt-get -f install
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Corrigiendo dependencias... falló.
Los siguientes paquetes tienen dependencias incumplidas:
 compiz : Depende: compiz-core (>= 1:0.9.12.1+15.04.20150410.1-0ubuntu1) pero 1:0.9.7.12-0ubuntu4 está instalado
          Depende: compiz-plugins-default (>= 1:0.9.12.1+15.04.20150410.1-0ubuntu1) pero 1:0.9.7.12-0ubuntu4 está instalado
 compiz-gnome : Depende: libdecoration0 (>= 1:0.9.8.2) pero 1:0.9.7.12-0ubuntu4 está instalado
                Depende: libglib2.0-0 (>= 2.37.3) pero 2.32.4-0ubuntu1 está instalado
                Depende: libmetacity-private2 (>= 3.12.0) pero no es instalable
                Depende: libpango-1.0-0 (>= 1.14.0) pero no es instalable
                Depende: libpangocairo-1.0-0 (>= 1.14.0) pero no es instalable
                Depende: session-migration pero no es instalable
                Depende: compiz-plugins-default (= 1:0.9.12.1+15.04.20150410.1-0ubuntu1) pero 1:0.9.7.12-0ubuntu4 está instalado
                Depende: gnome-settings-daemon-schemas (>= 3.4.2-0ubuntu9) pero no es instalable
                Depende: python3-gi pero no está instalado
 libdbus-1-3 : Depende: libc6 (>= 2.17) pero 2.15-0ubuntu10.12 está instalado
E: Error, pkgProblemResolver::Resolve generó cortes, esto puede haber sido causado por paquetes retenidos.
E: No se puede corregir las dependencias
root@ubuntu:/# 
Qué tengo que hacer?
Saludos

---

### Post by gmunioz on 2015-07-12
Antes de ejecutar:
> dpkg --configure -a

Ejecuta:
> nano /etc/apt/sources.list

En el archivo que se abre, verifica que el contenido sea este:
> deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
Control + U, pega. Control + O, guarda. Control + X, cierra nano.
Luego continua ejecutando:
> apt-get update
dpkg --configure -a
apt-get -f install
apt-get -m install
apt-get dist-upgrade
apt-get install --reinstall ubuntu-desktop
grub-mkconfig -o /boot/grub/grub.cfg
grub-install --root-directory=/mnt /dev/sda
grub-install --recheck /dev/sda
apt-get clean
apt-get autoremove
umount /mnt
reboot 

---

### Post by Vero1 on 2015-07-12
Me parece que voy muy mal.

Ésto es lo que sale:

  GNU nano 2.2.6                              Archivo: /etc/apt/sources.list                                                                    

# /etc/apt/sources.list

deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates main restricted































^G Ver ayuda            ^O Guardar              ^R Leer Fich            ^Y RePág.               ^K Cortar Texto         ^C Pos actual
^X Salir                ^J Justificar           ^W Buscar               ^V Pág. Sig.            ^U PegarTxt             ^T Ortografía

---

### Post by enriquek2 on 2015-07-12
Puede ser que esto se deba a falta de espacio en /boot y/o en / por la acumulación de kernels que se instalaron  a lo largo del tiempo
muestra la salida de 
df -h
y
df -hi

---

### Post by Vero1 on 2015-07-13
Hola EnriqueK, gracias por responder.

ubuntu@ubuntu:~$ df -h
S.ficheros     Tamaño Usado  Disp Uso% Montado en
/cow            1003M   82M  921M   9% /
udev             995M  4,0K  995M   1% /dev
tmpfs            401M  788K  401M   1% /run
/dev/sr0         702M  702M     0 100% /cdrom
/dev/loop0       673M  673M     0 100% /rofs
tmpfs           1003M  8,0K 1003M   1% /tmp
none             5,0M  4,0K  5,0M   1% /run/lock
none            1003M   76K 1003M   1% /run/shm
ubuntu@ubuntu:~$ df -hi
S.ficheros     Nodos-i NUsados NLibres NUso% Montado en
/cow              215K     864    214K    1% /
udev              211K     503    211K    1% /dev
tmpfs             215K     420    214K    1% /run
/dev/sr0             0       0       0     - /cdrom
/dev/loop0        156K    156K       0  100% /rofs
tmpfs             215K      19    215K    1% /tmp
none              215K       4    215K    1% /run/lock
none              215K       4    215K    1% /run/shm
ubuntu@ubuntu:~$

---

### Post by gmunioz on 2015-07-13
Pues simplemente copia y pega en el archivo el contenido requerido.
Sin los repositorios activos jamás podrás actualizar.
Elimina el cdrom del archivo.

---

### Post by Vero1 on 2015-07-13
Dos cosas Gabriel:

Dice que no tiene permisos de escritura, por lo tanto no pude guardar.

No pude eliminar cdrom. Seguramente debido a que no tengo permisos de escritura tambien.

saludos

Acabo de darme cuenta que no había puesto sudo. Copié y pegué con sudo y pude guardar. 
Lo que no pude hacer fue eliminar el cdrom.

Ahora pruebo seguir adelante con tus instrucciones. 

Volveré.

---

### Post by Vero1 on 2015-07-13
Ya es la segunda vez que me sale ésto:
E: Algunos archivos de índice fallaron al descargar. Se han ignorado, o se han utilizado unos antiguos en su lugar
ubuntu@ubuntu:~$ sudo apt-get -m install
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
0 actualizados, 0 se instalarán, 0 para eliminar y 745 no actualizados.
W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/restricted i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_restricted_binary-i386_Packages)
W: Tal vez quiera ejecutar «apt-get update» para corregir estos problemas
(ya hice apt-get update 2 veces)

---

### Post by enriquek2 on 2015-07-13
El comando df te muestra los valores de temaño, uso y disponibilidad de las particiones montadas , los valores que muestras al ejecutar df -h y df -hi  evta indicando que no tienes montadas las particiones y los valores que indican se refieren al livecd , sugiero que reinicies la sesión livecd , entra a una carpeta cualquiera y en el menú lateral selecciona las particiones /boot / y /home  esto hará que se monten y seguidamente pone las salidas de df -h  y  df -hi

---

### Post by Vero1 on 2015-07-13
Acá está lo que me pedis EnriqueK:

ubuntu@ubuntu:~$ df -h
S.ficheros     Tamaño Usado  Disp Uso% Montado en
/cow            1003M   81M  922M   9% /
udev             995M  4,0K  995M   1% /dev
tmpfs            401M  780K  401M   1% /run
/dev/sr0         702M  702M     0 100% /cdrom
/dev/loop0       673M  673M     0 100% /rofs
tmpfs           1003M  8,0K 1003M   1% /tmp
none             5,0M  4,0K  5,0M   1% /run/lock
none            1003M  148K 1003M   1% /run/shm
/dev/sda3        298G   82G  201G  29% /media/0d3d14d7-1c60-4039-9777-090ce4ed09ba
/dev/sda1        7,4G  493M  6,6G   7% /media/300e7274-09d3-42b9-80d5-db78d1b9e6f9
/dev/sda2         81G   14G   64G  18% /media/e14ce3e7-9876-4dd4-80a9-c39fde2b6b27
/dev/sda4         80G   67M   80G   1% /media/53366E2064DFD306
ubuntu@ubuntu:~$ df -hi
S.ficheros     Nodos-i NUsados NLibres NUso% Montado en
/cow              215K     854    214K    1% /
udev              211K     493    211K    1% /dev
tmpfs             215K     411    214K    1% /run
/dev/sr0             0       0       0     - /cdrom
/dev/loop0        156K    156K       0  100% /rofs
tmpfs             215K      19    215K    1% /tmp
none              215K       4    215K    1% /run/lock
none              215K       5    215K    1% /run/shm
/dev/sda3          19M     39K     19M    1% /media/0d3d14d7-1c60-4039-9777-090ce4ed09ba
/dev/sda1         478K     351    477K    1% /media/300e7274-09d3-42b9-80d5-db78d1b9e6f9
/dev/sda2         5,1M    568K    4,6M   11% /media/e14ce3e7-9876-4dd4-80a9-c39fde2b6b27
/dev/sda4          80M      19     80M    1% /media/53366E2064DFD306
ubuntu@ubuntu:~$

---

### Post by gmunioz on 2015-07-13
1- Los repositorios duplicados, responden a que no pudiste sobre escribir los existentes, salvo el mensaje no afectan para nada el sistema.
una vez logrado que el sistema funcione, con paciencia verificas en el archivo sources.list las líneas duplicadas y las comentas con # al inicio.

2- Si algunos archivos indices fallaron, continua con los otros comandos igual, para tratar de actualizar correctamente el sistema.

---

### Post by Vero1 on 2015-07-13
antes de reboot, te paso el resultado de todas las òrdenes, donde falla el asunto Grub. Ya verás.

ubuntu@ubuntu:~$ sudo apt-get dist-upgrade
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Calculando la actualización... Listo
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.
ubuntu@ubuntu:~$ apt-get install --reinstall ubuntu-desktop
E: No se pudo abrir el fichero de bloqueo «/var/lib/dpkg/lock» - open (13: Permiso denegado)
E: No se encontró un archivo de réplica «/var/lib/dpkg/»
ubuntu@ubuntu:~$ sudo apt-get install --reinstall ubuntu-desktop
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
0 actualizados, 0 se instalarán, 1 reinstalados, 0 para eliminar y 0 no actualizados.
Necesito descargar 3.932 B de archivos.
Se utilizarán 0 B de espacio de disco adicional después de esta operación.
Des:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main ubuntu-desktop i386 1.267 [3.932 B]
Descargados 3.932 B en 0seg. (11,4 kB/s)    
(Leyendo la base de datos ... 150248 ficheros o directorios instalados actualmente.)
Preparando para reemplazar ubuntu-desktop 1.267 (usando .../ubuntu-desktop_1.267_i386.deb) ...
Desempaquetando el reemplazo de ubuntu-desktop ...
Configurando ubuntu-desktop (1.267) ...
ubuntu@ubuntu:~$ sudo grub-mkconfig -o /boot/grub/grub.cfg
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
ubuntu@ubuntu:~$ sudo grub-mkconfig -o /boot/grub/grub.cfg
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
ubuntu@ubuntu:~$ sudo grub-mkconfig -o /boot/grub/grub.cfg
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
/usr/sbin/grub-probe: error: cannot find a device for /mnt/boot/grub (is /dev mounted?).
ubuntu@ubuntu:~$ sudo grub-install --recheck /dev/sda
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
ubuntu@ubuntu:~$ sudo apt-get clean
ubuntu@ubuntu:~$ sudo apt-get autoremove
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.
ubuntu@ubuntu:~$ sudo umount /mnt
umount: /mnt: no montado
ubuntu@ubuntu:~$

---

### Post by Vero1 on 2015-07-13
> **Vero1 said:**
> antes de reboot, te paso el resultado de todas las òrdenes, donde falla el asunto Grub. Ya verás.

ubuntu@ubuntu:~$ sudo apt-get dist-upgrade
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Calculando la actualización... Listo
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.
ubuntu@ubuntu:~$ apt-get install --reinstall ubuntu-desktop
E: No se pudo abrir el fichero de bloqueo «/var/lib/dpkg/lock» - open (13: Permiso denegado)
E: No se encontró un archivo de réplica «/var/lib/dpkg/»
ubuntu@ubuntu:~$ sudo apt-get install --reinstall ubuntu-desktop
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
0 actualizados, 0 se instalarán, 1 reinstalados, 0 para eliminar y 0 no actualizados.
Necesito descargar 3.932 B de archivos.
Se utilizarán 0 B de espacio de disco adicional después de esta operación.
Des:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main ubuntu-desktop i386 1.267 [3.932 B]
Descargados 3.932 B en 0seg. (11,4 kB/s)    
(Leyendo la base de datos ... 150248 ficheros o directorios instalados actualmente.)
Preparando para reemplazar ubuntu-desktop 1.267 (usando .../ubuntu-desktop_1.267_i386.deb) ...
Desempaquetando el reemplazo de ubuntu-desktop ...
Configurando ubuntu-desktop (1.267) ...
ubuntu@ubuntu:~$ sudo grub-mkconfig -o /boot/grub/grub.cfg
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
ubuntu@ubuntu:~$ sudo grub-mkconfig -o /boot/grub/grub.cfg
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
ubuntu@ubuntu:~$ sudo grub-mkconfig -o /boot/grub/grub.cfg
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
/usr/sbin/grub-probe: error: cannot find a device for /mnt/boot/grub (is /dev mounted?).
ubuntu@ubuntu:~$ sudo grub-install --recheck /dev/sda
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
ubuntu@ubuntu:~$ sudo apt-get clean
ubuntu@ubuntu:~$ sudo apt-get autoremove
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.
ubuntu@ubuntu:~$ sudo umount /mnt
umount: /mnt: no montado
ubuntu@ubuntu:~$

Lamentablemente al reboot sigue saliendo el Prompt Grub> , supongo debido a los fallos que informa el comando.

---

### Post by enriquek2 on 2015-07-13
Tienes espacio de sobra.
Prueba arrancar el sistema con el Super Grub2 Disk
[https://forja.cenatic.es/frs/download.php/file/1844/super_grub2_disk_hybrid_2.02s3.iso](https://forja.cenatic.es/frs/download.php/file/1844/super_grub2_disk_hybrid_2.02s3.iso)
Si arranca ejecuta este comando
sudo grub-mkconfig && sudo grub-install /dev/sda && sudo update-grub

---

### Post by Vero1 on 2015-07-13
EnriqueK, lamentablemente no pude grabar el SuperGrub2Disk porque el Backend no lo soporta(informa error).
De todas formas tengo como 4 de estos discos  y jamás me funcionò ni uno.

Además, como podrás ver en los posts con Gabriel Munioz, mi mayor problema es el Grub justamente y tu comando hace mención del Grub.

Bueno, vos dirás si hay algo mas que hacer.

Gracias

---

### Post by gmunioz on 2015-07-13
Te reitero los pasos que no has cumplido en su totalidad:


Inicia con la distribución live.
Terminada la carga abre una terminal.
Ejecuta en ella:
> ubuntu@ubuntu:~$ sudo -i
# fdisk -l
Fdisk te informará como se denominan tus discos y particiones
Supongamos, que tu disco es /dev/sda
Y que tu partición root, / es /dev/sda1, continua ejecutando en la terminal:
**Cambia /dev/sda1 por lo que corresponde a /, root**
> # umount /dev/sda1
# fsck  -y  /dev/sda1
# mount  /dev/sda1  /mnt
# mount --bind  /dev  /mnt/dev
#mount --bind  /dev/pts  /mnt/dev/pts
# mount --bind  /proc  /mnt/proc
# mount --bind  /sys  /mnt/sys
# chroot /mnt
A partir de este momento te encuentras ejecutando **en esta terminal**
donde el prompt será **#** y nunca el que muestras **ubuntu@ubuntu:~$**
el sistema instalado en el disco rígido, para repararlo, actualizarlo y
reinstalar el Grub ejecuta estos comandos **dentro de la terminal con el prompt # **:
> # nano  /etc/apt/sources.list 

Borra su contenido totalmente y pega este:
> deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
> Control + U, pega. Control + O, guarda. Control + X, cierra nano.

Continua ejecutando **dentro de la terminal con el prompt # **:
> # rm -Rf  /var/lib/dpkg/lock
# rm -Rf  /var/cache/apt/archives/lock
# apt-get update
# dpkg --configure -a
# apt-get -f install
# apt-get -m install
# apt-get dist-upgrade
# apt-get install --reinstall ubuntu-desktop
# grub-mkconfig -o /boot/grub/grub.cfg
# grub-install --root-directory=/mnt /dev/sda
# grub-install --recheck /dev/sda
# apt-get clean
# apt-get autoremove
# umount /mnt
# reboot


---

### Post by Vero1 on 2015-07-13
ubuntu@ubuntu:~$ sudo -i
bash: /usr/bin/python: Error de entrada/salida
ubuntu@ubuntu:~$ 


sigo con el resto?

---

### Post by gmunioz on 2015-07-13
No.
Prueba con:
> sudo su
> sudo -s
O a cada uno de los comandos le antepones > sudo

---

### Post by Vero1 on 2015-07-13
ok pero despues de sudo su, sigo a partir de donde?

pienso que desde lo que informa fdisk -l.

Otra cosa. Mi primera particion es sda1 - boot
                     segunda                 sda2 - raiz (es lo que vos llamás root?)
                     tercera                   sda3 - home
                     cuarta                    sda4 - lugar para Windows

Ahora, podrías decirme cómo se "borra" lo del sources list? Porque no pude borrar el cdrom. Simplemente voy con el cursor y elimino con el retroceso y despues "guardo" ? Porque opción no hay solamente "cortar" una línea.

Pregunto todo ésto para no meter las de andar.

Gracias

Gabriel, no pude esperar tu respuesta. Soy Co-Administradora de una Fan-page y necesito arreglar este problema cuanto antes. Por lo tanto, corrí el riesgo de seguir las instrucciones. Todo bien hasta donde indica lo que copié:

dpkg: problemas de dependencias impiden la configuración de compiz:
 compiz depende de compiz-core (>= 1:0.9.12.1+15.04.20150410.1-0ubuntu1); sin embargo:
  La versión de `compiz-core' en el sistema es 1:0.9.7.12-0ubuntu4.
 compiz depende de compiz-plugins-default (>= 1:0.9.12.1+15.04.20150410.1-0ubuntu1); sin embargo:
  La versión de `compiz-plugins-default' en el sistema es 1:0.9.7.12-0ubuntu4.

dpkg: error al procesar el paquete compiz (--configure):
 problemas de dependencias - se deja sin configurar
Configurando gconf2 (3.2.5-0ubuntu2) ...
Configurando ureadahead (0.100.0-19) ...
Configurando ttf-dejavu-core (2.34-1ubuntu1) ...
dpkg: problemas de dependencias impiden la configuración de install-info:
dpkg (1.17.25ubuntu1) rompe install-info (<< 5.1.dfsg.1-3~) y es instalado.
  La versión de `install-info' que se desconfigurará es 4.13a.dfsg.1-8ubuntu2.

dpkg: error al procesar el paquete install-info (--configure):
 problemas de dependencias - se deja sin configurar
Configurando cups-daemon (2.0.2-1ubuntu3) ...
update-rc.d: warning: cups stop runlevel arguments (0 1 6) do not match LSB Default-Stop values (1)
/usr/sbin/invoke-rc.d: 1: /usr/sbin/invoke-rc.d: /sbin/runlevel: not found
start: Job failed to start
invoke-rc.d: initscript cups, action "start" failed.
dpkg: error al procesar el paquete cups-daemon (--configure):
 el subproceso instalado el script post-installation devolvió el código de salida de error 1
dpkg: problemas de dependencias impiden la configuración de initramfs-tools:
 initramfs-tools depende de initramfs-tools-bin (>= 0.103ubuntu15); sin embargo:
  La versión de `initramfs-tools-bin' en el sistema es 0.99ubuntu13.5.
 initramfs-tools depende de klibc-utils (>= 2.0-1~); sin embargo:
  La versión de `klibc-utils' en el sistema es 1.5.25-1ubuntu2.

dpkg: error al procesar el paquete initramfs-tools (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de cups-core-drivers:
 cups-core-drivers depende de cups-daemon (>= 2.0.2-1ubuntu3); sin embargo:
 El paquete `cups-daemon' no está configurado todavía.

dpkg: error al procesar el paquete cups-core-drivers (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de mono-gac:
 mono-gac depende de mono-4.0-gac (= 3.2.8+dfsg-4ubuntu4); sin embargo:
  La versión de `mono-4.0-gac' en el sistema es 2.10.8.1-1ubuntu2.3.

dpkg: error al procesar el paquete mono-gac (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de perl:
 perl depende de perl-modules (>= 5.20.2-2); sin embargo:
  La versión de `perl-modules' en el sistema es 5.14.2-6ubuntu2.4.
 perl depende de libdb5.3; sin embargo:
  El paquete `libdb5.3' no está instalado.

dpkg: error al procesar el paquete perl (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de upstart:
 upstart depende de libjson0 (>= 0.10-1.1ubuntu1); sin embargo:
  La versión de `libjson0:i386' en el sistema es 0.9-1ubuntu1.1.

dpkg: error al procesar el paquete upstart (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de man-db:
dpkg (1.17.25ubuntu1) rompe man-db (<< 2.6.3-6~) y es instalado.
  La versión de `man-db' que se desconfigurará es 2.6.1-2ubuntu2.

dpkg: error al procesar el paquete man-db (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de compiz-gnome:
 compiz-gnome depende de libdecoration0 (>= 1:0.9.8.2); sin embargo:
  La versión de `libdecoration0' en el sistema es 1:0.9.7.12-0ubuntu4.
 compiz-gnome depende de libglib2.0-0 (>= 2.37.3); sin embargo:
  La versión de `libglib2.0-0:i386' en el sistema es 2.32.4-0ubuntu1.
 compiz-gnome depende de libmetacity-private2 (>= 3.12.0); sin embargo:
  El paquete `libmetacity-private2' no está instalado.
 compiz-gnome depende de libpango-1.0-0 (>= 1.14.0); sin embargo:
  El paquete `libpango-1.0-0' no está instalado.
 compiz-gnome depende de libpangocairo-1.0-0 (>= 1.14.0); sin embargo:
  El paquete `libpangocairo-1.0-0' no está instalado.
 compiz-gnome depende de session-migration; sin embargo:
  El paquete `session-migration' no está instalado.
 compiz-gnome depende de compiz-plugins-default (= 1:0.9.12.1+15.04.20150410.1-0ubuntu1); sin embargo:
  La versión de `compiz-plugins-default' en el sistema es 1:0.9.7.12-0ubuntu4.
 compiz-gnome d
dpkg: error al procesar el paquete compiz-gnome (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de fontconfig:
dpkg (1.17.25ubuntu1) rompe fontconfig (<< 2.11.1-0ubuntu5~) y es instalado.
  La versión de `fontconfig' que se desconfigurará es 2.8.0-3ubuntu9.1.

dpkg: error al procesar el paquete fontconfig (--configure):
 problemas de dependencias - se deja sin configurar
Configurando libnih-dbus1:i386 (1.0.3-4ubuntu27) ...
Configurando libcgmanager0:i386 (0.36-2ubuntu5) ...
dpkg: problemas de dependencias impiden la configuración de cups:
 cups depende de cups-core-drivers (>= 2.0.2-1ubuntu3); sin embargo:
 El paquete `cups-core-drivers' no está configurado todavía.
 cups depende de cups-daemon (>= 2.0.2-1ubuntu3); sin embargo:
 El paquete `cups-daemon' no está configurado todavía.

dpkg: error al procesar el paquete cups (--configure):
 problemas de dependencias - se deja sin configurar
Procesando disparadores para libc-bin (2.15-0ubuntu10.12) ...
ldconfig deferred processing now taking place
Se encontraron errores al procesar:
 compiz
 install-info
 cups-daemon
 initramfs-tools
 cups-core-drivers
 mono-gac
 perl
 upstart
 man-db
 compiz-gnome
 fontconfig
 cups
root@ubuntu:/# 


Gracias de antemano por tus comentarios.

---

### Post by enriquek2 on 2015-07-13
Creo recordar que en un post anterior indicaba que sda1 es partición /boot , aqul se le está dando instrucciones asumiendo que sda1 es  partición root / y sin tomar en cuenta que  además se debe montar sda1 en /boot , cuando en realidad es la sda2 la partición root y tal vez  sea este el factor por el cual las soluciones propuestas no llegan a puerto. Opino que este punto debe ser aclarado y también soy de la opinión de mover el contenido de /boot dentro del directorio root /

---

### Post by gmunioz on 2015-07-13
Reiteración conforme lo ultimo informado:
Inicia con la distribución live.
Terminada la carga abre una terminal.
En esta terminal te debes loguear como administrador, esto lo haces con el comando sudo
Ejecutas en la terminal:
> sudo -i
o
sudo su
ó
sudo -s
El que te funcione, luego de que el comando funcione el prompt
cambiará de 
> $ 
a
#
Si ningun sudo trabaja, deberás anteponer a cada comando que sigue el comando sudo.
Como has informado tu sistema en el disco rígido esta instalado en /boot = /dev/sda1
/ = /dev/sda2 y /home = /dev/sda3, no hace falta entonces ejecutar fdisk, pues ya sabemos 
como se llaman tus particiones.
Para reparar la instalación es necesario trabajar como administrador en el disco rígido, esto 
se hace mediante chroot, para hacer chroot es necesario montar las particiones del disco
rigido esto se hace dentro de la terminal donde estas como administrador, prompt # o anteponiendo
a cada comando el comando sudo, primero revisamos las particiones por si tiene errores, se
desmontan por las dudas y se revisan con fsck:
> umount /dev/sda1
fsck -y /dev/sda1
umount /dev/sda2
fsck -y /dev/sda2
umount /dev/sda3
fsck -y /dev/sda3
Si el prompt de la terminal no cambió a #, antepone sudo a cada comando.
Una vez revisados los sistemas de archivos es necesario montarlos, esto lo
haces con estos comandos:
> mount /dev/sda2 /mnt
mount /dev/sda1 /mnt/boot
mount /devsda3 /mnt/home
mount --bind /dev /mnt/dev
mount --bind /dev/pts /mnt/dev/pts
mount --bind /proc /mnt/proc
mount --bind /sys /mnt/sys

Si el prompt de la terminal no cambió a #, antepone sudo a cada comando.
A partir de este momento tienes montado el sistema del disco rígido y
hace falta hacerse dueño de el mediante chroot:
> chroot /mnt
Si el prompt de la terminal no cambió a #, antepone sudo al comando.
Ahora en esta terminal y solo en esta terminal donde el prompt será # y nunca ubuntu@ubuntu:~$
estas trabajando con el sistema instalado en el disco rígido, que es el que quieres reparar.

Primero corrige el archivo /etc/apt/sources.list del disco rígido, ejecutando en la terminal 
> nano /etc/apt/sources.list
Borra todo su contenido totalmente y pega este:
> deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

Con las teclas Control + U, pegas en nano. Control + O, guardas el archivo. 
Control + X, cierras nano y sigues trabajando en la terminal con el sistema del disco.
Continua ejecutando dentro de la terminal con el prompt #, para borrar el archivo lock
que aparentemente te bloquea y para actualizar, reparar y reinstalar el Grub :
>  rm -Rf /var/lib/dpkg/lock
 rm -Rf /var/cache/apt/archives/lock
 apt-get update
 dpkg --configure -a
 apt-get -f install
 apt-get -m install
 apt-get dist-upgrade
 apt-get install --reinstall ubuntu-desktop
 grub-mkconfig -o /boot/grub/grub.cfg
 grub-install --root-directory=/mnt /dev/sda
 grub-install --recheck /dev/sda
 apt-get clean
 apt-get autoremove
 umount /mnt
 reboot


---

### Post by Vero1 on 2015-07-14
EnriqueK, tal vez se le pasó por alto ésto que escribio gmunioz:

"Fdisk te informará como se denominan tus discos y particiones
Supongamos, que tu disco es /dev/sda
Y que tu partición root, / es /dev/sda1, continua ejecutando en la terminal:
Cambia /dev/sda1 por lo que corresponde a /, root"

En el último renglón hace mención a la necesidad de cambiar /dev/sda1, por lo que corresponda. Sí, recordó bien. Mi partición raíz es sda2.

Cuando instalé, separé la partición para Boot a sda1. 
Recuerdo haber usado en una ocasión Boot-repair y marcado todas las particiones para Boot. No sé si éso está vigente todavía con todo lo que pasó despues.

Gracias.

---

### Post by enriquek2 on 2015-07-14
No entiendo que problemas tienes con el Super Grub2 Disk , si no puedes grabar la iso en tu pc por estar ocupado el cdron al estar en sesión livecd, lo grabas en otro equipo , por ejemplo si se trata de uno con Xp que tiene a Nero , click secundario sobre la iso ---> abrir con --> Nero    y el mismo proceso si lo haces desde un linux, por ejemplo .....abrir con --> k3b  o brasero
Para mi lo mejor que puedes hacer es mover el contenido de /boot a la raiz , es simple de haer, para ello reinicia la sesión livecd
ejecuta en terminal 
sudo mkdir /mnt/111
sudo mkdir /mnt/222
sudo mount /dev/sda1 /mnt/111
sudo mount /dev/sda2 /mnt/222
sudo cp -ax /mnt/111/. /mnt/222/boot

luego ejecuta
sudo nano /mnt/222/etc/fstab
comentas la linea  (poniendo # al comienzo de la misma) que hace referencia al punto de montaje /boot
Guardas los cambios con Ctrl +O pulsa Enter 
sales de nano con Ctrl +X
reinicias sistema con 
sudo init 6

---

### Post by Vero1 on 2015-07-14
Con el SuperGrubDisk2(tengo 3 o 4 CDs) ninguno funciona ahora ni nunca funcionaron.

Estoy esperando que me conteste gmunioz porque quedé en la mitad de sus intrucciones y no sé si pueda ahora seguir sus indicaciones EnriqueK. Tengo miedo de hacer algún zafarrancho.

Ud. puede decirme, de acuerdo a lo que dice gmunioz con respecto a los comandos a ejecutar, la mayoría de los cuales ya ejecuté como root, si puedo intentar ahora lo que Ud. me indica?

Gracias

---

### Post by gmunioz on 2015-07-14
Mira más arriba en el post. Ya te contesté.

---

### Post by enriquek2 on 2015-07-14
Lo que te propone Gabriel debería funcionar, aunque nunca probé hacer con chroot por que prefiero usar el super grub2 por ser mucho mas simple intuitivo y rápido para estos casos .
Mi comentario anterior va mas que nada para cuando soluciones tu problema y decidas mover el contenido de  sda1 a /boot por que al menos yo no le veo sentido tener una partición boot separa , además de consumirte una partición primaria sin otorgar  beneficios.

---

### Post by Vero1 on 2015-07-14
Gabriel, Perdonáme pero creo que hay una confusión. Yo espero contestación sobre donde me quedé varada o sea en el comando # dpkg --configure -o.
Me sale todo ésto:

dpkg: problemas de dependencias impiden la configuración de compiz:
compiz depende de compiz-core (>= 1:0.9.12.1+15.04.20150410.1-0ubuntu1); sin embargo:
La versión de `compiz-core' en el sistema es 1:0.9.7.12-0ubuntu4.
compiz depende de compiz-plugins-default (>= 1:0.9.12.1+15.04.20150410.1-0ubuntu1); sin embargo:
La versión de `compiz-plugins-default' en el sistema es 1:0.9.7.12-0ubuntu4.

dpkg: error al procesar el paquete compiz (--configure):
problemas de dependencias - se deja sin configurar
Configurando gconf2 (3.2.5-0ubuntu2) ...
Configurando ureadahead (0.100.0-19) ...
Configurando ttf-dejavu-core (2.34-1ubuntu1) ...
dpkg: problemas de dependencias impiden la configuración de install-info:
dpkg (1.17.25ubuntu1) rompe install-info (<< 5.1.dfsg.1-3~) y es instalado.
La versión de `install-info' que se desconfigurará es 4.13a.dfsg.1-8ubuntu2.

dpkg: error al procesar el paquete install-info (--configure):
problemas de dependencias - se deja sin configurar
Configurando cups-daemon (2.0.2-1ubuntu3) ...
update-rc.d: warning: cups stop runlevel arguments (0 1 6) do not match LSB Default-Stop values (1)
/usr/sbin/invoke-rc.d: 1: /usr/sbin/invoke-rc.d: /sbin/runlevel: not found
start: Job failed to start
invoke-rc.d: initscript cups, action "start" failed.
dpkg: error al procesar el paquete cups-daemon (--configure):
el subproceso instalado el script post-installation devolvió el código de salida de error 1
dpkg: problemas de dependencias impiden la configuración de initramfs-tools:
initramfs-tools depende de initramfs-tools-bin (>= 0.103ubuntu15); sin embargo:
La versión de `initramfs-tools-bin' en el sistema es 0.99ubuntu13.5.
initramfs-tools depende de klibc-utils (>= 2.0-1~); sin embargo:
La versión de `klibc-utils' en el sistema es 1.5.25-1ubuntu2.

dpkg: error al procesar el paquete initramfs-tools (--configure):
problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de cups-core-drivers:
cups-core-drivers depende de cups-daemon (>= 2.0.2-1ubuntu3); sin embargo:
El paquete `cups-daemon' no está configurado todavía.

dpkg: error al procesar el paquete cups-core-drivers (--configure):
problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de mono-gac:
mono-gac depende de mono-4.0-gac (= 3.2.8+dfsg-4ubuntu4); sin embargo:
La versión de `mono-4.0-gac' en el sistema es 2.10.8.1-1ubuntu2.3.

dpkg: error al procesar el paquete mono-gac (--configure):
problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de perl:
perl depende de perl-modules (>= 5.20.2-2); sin embargo:
La versión de `perl-modules' en el sistema es 5.14.2-6ubuntu2.4.
perl depende de libdb5.3; sin embargo:
El paquete `libdb5.3' no está instalado.

dpkg: error al procesar el paquete perl (--configure):
problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de upstart:
upstart depende de libjson0 (>= 0.10-1.1ubuntu1); sin embargo:
La versión de `libjson0:i386' en el sistema es 0.9-1ubuntu1.1.

dpkg: error al procesar el paquete upstart (--configure):
problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de man-db:
dpkg (1.17.25ubuntu1) rompe man-db (<< 2.6.3-6~) y es instalado.
La versión de `man-db' que se desconfigurará es 2.6.1-2ubuntu2.

dpkg: error al procesar el paquete man-db (--configure):
problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de compiz-gnome:
compiz-gnome depende de libdecoration0 (>= 1:0.9.8.2); sin embargo:
La versión de `libdecoration0' en el sistema es 1:0.9.7.12-0ubuntu4.
compiz-gnome depende de libglib2.0-0 (>= 2.37.3); sin embargo:
La versión de `libglib2.0-0:i386' en el sistema es 2.32.4-0ubuntu1.
compiz-gnome depende de libmetacity-private2 (>= 3.12.0); sin embargo:
El paquete `libmetacity-private2' no está instalado.
compiz-gnome depende de libpango-1.0-0 (>= 1.14.0); sin embargo:
El paquete `libpango-1.0-0' no está instalado.
compiz-gnome depende de libpangocairo-1.0-0 (>= 1.14.0); sin embargo:
El paquete `libpangocairo-1.0-0' no está instalado.
compiz-gnome depende de session-migration; sin embargo:
El paquete `session-migration' no está instalado.
compiz-gnome depende de compiz-plugins-default (= 1:0.9.12.1+15.04.20150410.1-0ubuntu1); sin embargo:
La versión de `compiz-plugins-default' en el sistema es 1:0.9.7.12-0ubuntu4.
compiz-gnome d
dpkg: error al procesar el paquete compiz-gnome (--configure):
problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de fontconfig:
dpkg (1.17.25ubuntu1) rompe fontconfig (<< 2.11.1-0ubuntu5~) y es instalado.
La versión de `fontconfig' que se desconfigurará es 2.8.0-3ubuntu9.1.

dpkg: error al procesar el paquete fontconfig (--configure):
problemas de dependencias - se deja sin configurar
Configurando libnih-dbus1:i386 (1.0.3-4ubuntu27) ...
Configurando libcgmanager0:i386 (0.36-2ubuntu5) ...
dpkg: problemas de dependencias impiden la configuración de cups:
cups depende de cups-core-drivers (>= 2.0.2-1ubuntu3); sin embargo:
El paquete `cups-core-drivers' no está configurado todavía.
cups depende de cups-daemon (>= 2.0.2-1ubuntu3); sin embargo:
El paquete `cups-daemon' no está configurado todavía.

dpkg: error al procesar el paquete cups (--configure):
problemas de dependencias - se deja sin configurar
Procesando disparadores para libc-bin (2.15-0ubuntu10.12) ...
ldconfig deferred processing now taking place
Se encontraron errores al procesar:
compiz
install-info
cups-daemon
initramfs-tools
cups-core-drivers
mono-gac
perl
upstart
man-db
compiz-gnome
fontconfig
cups
root@ubuntu:/#

---

### Post by Vero1 on 2015-07-14
Lo que me propone Gabriel no se pudo completar todavía. Si querés mirá el post que acabo de enviarle.
Cuando instalé, preguntó si quería el boot en una partición aparte y le dije que si, por éso está en sda1.
Repito que el SuperGrubDisk a mi no me ha servido nunca. No me arrancó ni me arranca con él.
Gracias por tu tiempo y veré, una vez recuperado mi Grub y funcionando el sistema como debe, si muevo el boot a sda2.

Saludos

---

### Post by gmunioz on 2015-07-14
Repite el procedimiento desde el inicio.
No tienes actualizados los repositorios.
Los errores de dpkg indican que no se han descargado
los archivos de los repositorios.
Reitera el comando apt-get update.
Verifica que la conexión a internet funciona.

---

### Post by Vero1 on 2015-07-14
Son las 0,45 hs.
Lamentablemente no ha funcionado.

Cerré y volví a abrir para comprobar que el contenido del sources.list ha quedado guardado pero no es así. Siguen saliendo las 4 líneas del principio.

Nano no tiene la opciòn de borrar o eliminar. Gedit sí. He probado Gedit y allí sí se puede eliminar o borrar y luego guardar.

Hay otra cosa. Cuando escribo la última orden de # reboot, no pasa nada. Lo acepta y va al siguiente renglón.

Apagué la máquina y la encendí a ver si booteba así pero no, sigue saliendo el Promt Grub>.

He pensado en reinstalar pero le tengo algo de miedo o bien instalar ubuntu 14.04 (se puede no perder nada he leído, puede ser?)  Lo malo es que traté 3 veces de grabar un DVD pero cuando llega al 90% me tira un informe de que no hay mas espacio en disco(cosa completamente imposible). Bueno ésto fué antes del trabajo que hice hoy.

Cuál es tu opinión sobre todo este lío?

Gracias por querer ayudarme.

Saludos

---

### Post by enriquek2 on 2015-07-15
Creo que el problema se debe a que para editar el sources. list de la instalación en DD debes hacerlo antes de ejecutar chroot /mnt
Ejecuta los primeros pasos que te indicó Gabriel
sudo su
mount /dev/sda2 /mnt
mount /dev/sda1 /mnt/boot
mount /devsda3 /mnt/home
mount --bind /dev /mnt/dev
mount --bind /dev/pts /mnt/dev/pts
mount --bind /proc /mnt/proc
mount --bind /sys /mnt/sys

edita el sources.list
gedit /mnt/etc/apt/sources.list
guardas los cambios
ejecuta en ese mismoterminal de root
chroot /mnt
continúa con los pasos indicados por Gabriel

Otra cosa o no haces los pasos correctos para grabar la iso de instalación de Ubuntu o tu grabadora de cd no está bien, tal vez por eso es que tienes problemas con el Super Grub2 Disk y de paso te digo que no es lo mismo que el Super Grub Disk el cual es para usar con el grub 1 por lo que no sirve en una instalación con grub2

---

### Post by gmunioz on 2015-07-15
Antes de reinstalar lleva al técnico la computadora, para que la revise y la limpie especialmente a nivel memorias y ventiladores.
Esa máquina tiene demasidos problemas (boot, boot del dvd, grabación del dvd.) que impresionana como que algo no está correcto.
Luego para reinstalar, simplemente elige particionamiento manual y monta /dev/sda1 como /boot, /dev/sda2 como / y /dev/sda3
como /home usando el mismo nombre de usuario y la misma contraseña y mantendrás tus archivos y las configuraciones que se
mantengan vigentes..

---

### Post by Vero1 on 2015-07-15
ok EnriqueK, intentaré lo tuyo.

Antes que nada probaré grabar nuevamente el SuperGrub2Disk porque esos DVDs son anteriores a un cambio de lectora que hice el año pasado.

Pero, no sé si leiste el intercambio de posts con Gabriel, que hay problemas de dependencias que no se pueden resolver(según lo que se informa).

Bueno, despues te diré qué resultados obtuve.

Gracias

---

### Post by Vero1 on 2015-07-15
Antes de resolver qué hacer, probaré lo que me indica EnriqueK.

Comentaré los resultados.

Gracias.

---

### Post by Vero1 on 2015-07-15
Despues de haber hecho el apt-get dist-upgrade me dice : dpkg: error fatal irrecuperable, abortando:
 no se puede efectuar `flush' /var/lib/dpkg/updates/tmp.i tras el relleno: No queda espacio en el dispositivo
E: Sub-process /usr/bin/dpkg returned an error code (2)
root@ubuntu:/home/ubuntu# apt-get install --reinstall ubuntu-desktop
E: se interrumpió la ejecución de dpkg, debe ejecutar manualmente «sudo dpkg --configure -a» para corregir el problema
root@ubuntu:/home/ubuntu# exit
exit
ubuntu@ubuntu:~$ sudo dpkg --configure -a
dpkg: error: fallo al escribir el registro de base de datos status sobre `apparmor' a `/var/lib/dpkg/status': No queda espacio en el dispositivo
ubuntu@ubuntu:~$ 

No es posible. La partición /home tenia 320 Gb...

---

### Post by gmunioz on 2015-07-15
Has revisar el equipo antes de reinstalar, algo esta fallando que da tantos errores.

---

### Post by Vero1 on 2015-07-16
Tengo una consulta.

Cuando reinstale, qué va a pasar con mis Marcadores de Firefox y con el correo Thunderbird, lo que hay en Rhytmbox, Shotwell, en fin, con los programas instalados?
En las condiciones actuales no puedo hacer ningún respaldo.

Nunca reinstalé un Sistema Operativo desde hace más de 20 años que uso la computadora, así que es como si fuera novata.

Estuve buscando Tutoriales sobre re-instalación pero no encuentro nada preciso. Lo único que ví que me puede servir es NO formatear la partición Home y poner los mismos nombres que puse cuando instalé originalmente Precise.

Realmente estoy preocupada porque no quisiera perder nada de lo que hay actualmente en la máquina.

Algun comentario?

Gracias

---

### Post by gmunioz on 2015-07-16
Existe una opción que es actualizar el sistema instalado, asi no se pierde nada, 
pero no es aconsejable en razón de que tu sistema tiene errores importantes y
podrían persistir.

---

### Post by Vero1 on 2015-07-17
Ayer, despues de toda una tarde de trabajo, quedó re-instalado el sistema.
Dejé sin formatear /home. El Grub en sda2 -
Despues que terminó la instalación re-inicié esperando ansiosamente ver el Grub pero salió pantalla negra. Opté por pasarle el Boot-Repair- opción recomendada, pero no se arregló, entonces pasé la opción avanzada, pero al tildar nomodset la resoluciòn era muy baja porque me detectaba Portátil. 
Ya me había pasado lo mismo tiempo atrás. Menos mal que guardé las instrucciones de como revertir ésto. Lo hice y POR FIN tengo todo bien o casi porque cuando particionè, hice una partición para Windows y ocupé el cuarto lugar primario, así que no tengo Swap. Tenía un swap-file pero eso se borró. En fin. Veré qué hacer.

A vos, te agradezco tu buena voluntad y el tiempo invertido en ayudarme.

Saludos
p.d.
me encanta: Me creen indeciso-No estoy seguro de ello :p

---

### Post by gmunioz on 2015-07-17
Puedes crear un archivo que te sirva de partición de intercambio.
Crear un archivo para swap de 2,5 Gigas:

> sudo -i
dd if=/dev/zero of=/media/swapfile bs=1M count=2560
mkswap /media/swapfile
swapon /media/swapfile

Y para activarlo al inicio:

> sudo -i
nano /etc/fstab

Y añades en el archivo:

> /media/swapfile	swap	swap	defaults	0	0

Puedes crearlo donde más te guste, solo cambia el path.

---

### Post by Vero1 on 2015-07-18
Sos muy amable Gabriel, muchas gracias.
Lo voy a poner en práctica.
Ahora, yo tengo 2 GB de RAM. Tengo entendido que Swap debe tener la mitad de la RAM o es que siendo un archivo puedo darle lo que crea conveniente?

Saludos

---

### Post by gmunioz on 2015-07-18
Para uso común, basta con 2 gigas, sería 2048, para hibernar y/o suspender son necesarios el 
triple de la ram, en este caso serian 6144.

---

### Post by Vero1 on 2015-07-18
Bueno como no voy a hibernar ni a suspender, le pondré 2 Gb.

Gracias de nuevo :-)

saludos

---

### Post by enriquek2 on 2015-07-21
Hubieras aprovechado de no destinar partición separada para boot y destinar esa primaria para tener allí a la swap

---

### Post by Vero1 on 2015-07-22
Sí tenés razón EnriqueK pero no quise tener mas problemas.

Pero ya está. Gracias.

Saludos

---

