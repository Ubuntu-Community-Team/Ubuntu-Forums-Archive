---
title: "HOWTO: Soporte de lectura y escritura en NTFS usando ntfs-3g"
date: 2006-12-03
forum: Argentina Team
---

### Post by QUASAR_FREAK on 2006-12-03
[FONT=Arial][SIZE=3]Este driver esta en modo testeo, si bien a mi y a muchos otros nos anduvo bien puede ser que tenga bugs y que te cause alguna perdida de datos, si instalas el driver y éste ocasiona perdida de datos mata a tu gato le pega a tu vieja no vengas a llorar y a echar culpas, ya estas avisado :p

[COLOR=black]_** 1. Configurando los repositorios**_[/COLOR]
[COLOR=black]
** Para Dapper**[/COLOR] 

No existe el driver ntfs-3g en los repos de Dapper por lo que vamos a tener que agregar unos

En una terminal ponemos:
[/SIZE][/FONT][FONT=Arial][SIZE=3]```

gksu gedit /etc/apt/sources.list

```[/SIZE][/FONT][FONT=Arial][SIZE=3]Al final de esa lista pongamos los nuevos repositorios:
[/SIZE][/FONT]```

[FONT=Arial][SIZE=3]deb http://givre.cabspace.com/ubuntu/ dapper main main-all
deb http://ntfs-3g.sitesweetsite.info/ubuntu/ dapper main main-all
deb http://flomertens.keo.in/ubuntu/ dapper main main-all[/SIZE][/FONT]

```[FONT=Arial][SIZE=3]

El canal "main" tiene la version oficial de ntfs-3g.
El canal "main-all" tiene una versión no oficial y modificada de ntfs-3g que mejora la integración de ntfs-3g con el escritorio. Si no querés esos paquetes solo saca "main-all"

[COLOR=black]** Para Edgy:**[/COLOR]

El driver ntfs-3g se encuentra en los repositorios universe de edgy, por lo que solo tenemos que habilitarlos si queremos el driver oficial.

Si deseamos usar la ultima versión del driver oficial, ya ke el de los repos no esta updateado agregamos:

[/SIZE][/FONT]```
[FONT=Arial][SIZE=3]deb http://givre.cabspace.com/ubuntu/ edgy main
deb http://ntfs-3g.sitesweetsite.info/ubuntu/ edgy main
deb http://flomertens.keo.in/ubuntu/ edgy main[/SIZE][/FONT]
```[FONT=Arial][SIZE=3]

Si queremos usar la versión parcheada y no oficial:
[/SIZE][/FONT]```
[FONT=Arial][SIZE=3]deb http://givre.cabspace.com/ubuntu/ edgy main-all
deb http://ntfs-3g.sitesweetsite.info/ubuntu/ edgy main-all
deb http://flomertens.keo.in/ubuntu/ edgy main-all[/SIZE][/FONT]
```[FONT=Arial][SIZE=3]

_[COLOR=black]** 2. Instalación:**[/COLOR]_

Agregamos las keys necesarias escribiendo en una terminal:
[/SIZE][/FONT]```
[FONT=Arial][SIZE=3]wget http://flomertens.keo.in/ubuntu/givre_key.asc -O- | sudo apt-key add -
wget http://givre.cabspace.com/ubuntu/givre_key.asc -O- | sudo apt-key add -[/SIZE][/FONT]
```[FONT=Arial][SIZE=3]

Y ahora a instalar:
[/SIZE][/FONT]```
[FONT=Arial][SIZE=3]sudo apt-get update
sudo apt-get upgrade
sudo apt-get install ntfs-3g[/SIZE][/FONT]
```[FONT=Arial][SIZE=3]

[COLOR=black]_** 3. Configuración:**_[/COLOR]

Si la instalación salio bien, debemos configurar los dispositivos locales que tengamos en ntfs, digo locales porque los removibles los configura solo.

Si no sabemos cuales son ejecutemos en una terminal:
[/SIZE][/FONT]```
[FONT=Arial][SIZE=3]sudo fdisk -l | grep NTFS[/SIZE][/FONT]
```[FONT=Arial][SIZE=3]

Eso debería mostrar una o varias lineas con las particiones que tenemos como ntfs, ahora hay que configurarlas dentro de /etc/ftsab.

Hacemos un backup:
[/SIZE][/FONT][FONT=Arial][SIZE=3]```
sudo cp /etc/fstab /etc/fstab.bak
```Editamos el archivo:
```

gksu gedit /etc/fstab
```[/SIZE][/FONT][FONT=Arial][SIZE=3]

Busca la linea de tu partición ntfs (si es que ya hay una sino creala) y editala para que quede:
[/SIZE][/FONT]```
[FONT=Arial][SIZE=3]/dev/<tu partición>     /media/<punto de montaje>     ntfs-3g     defaults,locale=es_ES.utf8   0    0[/SIZE][/FONT]
```[FONT=Arial][SIZE=3]

(obviamente reemplaza <tu partición> y <punto de montaje> por los que correspondan en tu caso.)

Si en tu caso no tenias la linea en fstab y tuviste que crearla, vas a tener que crear también el punto de montaje, para eso hace:
[/SIZE][/FONT]```
[FONT=Arial][SIZE=3]sudo mkdir /media/<punto de montaje>[/SIZE][/FONT]
```[FONT=Arial][SIZE=3]

Si keres saber mas sobre el driver usa:
```

man ntfs-3g

```Esta guía es una traducción de [HOWTO: NTFS with read/write support using ntfs-3g (easy method)]("http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g")

Aun no esta completa ya que faltan los repos de 64 bit y algunas cosas mas importantes que se encuentran en la guía original, no la termine porque tengo sueño, si alguien la continua posteenlo y lo agrego, sino lo hago yo cuando tenga tiempo, saludos! [/SIZE][/FONT]

---

### Post by beuno on 2006-12-03
Yo lo use bastante este driver en breezy/dapper/edgy y no tuve ningun problema.

---

### Post by kalel on 2006-12-04
me funciona a la perfeccion hace rato, no duden en instalarlo =P

---

### Post by javier.der on 2006-12-04
opa

buenisimo, mil gracias!

---

### Post by baalthazar on 2006-12-06
bah.. no me furula... ](*,) algo debe tener mi pc que siempre q intento algo, o me funciona a medias o no me funciona.

cuando intento esto me sale esto 
```
(gedit:6287): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

```

y esto es el fstab 

antes lo habia montado de otra forma, pero presumo q de esa forma no podia editar la particion ntfs, por eso quise intentar este howto... espero q me ayuden a solucionar mi problema.
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1 /intento1 ntfs-3g defaults,locale=es_ES.utf8   0    0
/dev/sda5 /intento2 ntfs-3g defaults,locale=es_ES.utf8   0    0
/dev/sda6 /intento3 ntfs-3g defaults,locale=es_ES.utf8   0    0
# /dev/sda3 -- converted during upgrade to edgy
UUID=5af82fd7-da25-46b2-8901-a1f5e64d74de / ext3 defaults,errors=remount-ro 0 1
# /dev/sda1 -- converted during upgrade to edgy
UUID=1238C32138C302A9 /windows ntfs nls=utf8,umask=0222 0 0
# /dev/sda5 -- converted during upgrade to edgy
UUID=28F4C322F4C2F0DC /D ntfs nls=utf8,umask=0222 0 0
# /dev/sda6 -- converted during upgrade to edgy
UUID=E29C0CEB9C0CBBD3 /e_drive ntfs nls=utf8,umask=0222 0 0
# /dev/sda7 -- converted during upgrade to edgy
UUID=29db8962-4fc4-44e1-95f5-3a5d39e2e4bd none swap sw 0 0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

---

### Post by QUASAR_FREAK on 2006-12-06
proba de kambiar en el fstab para que kede asi:
```

/dev/sda1 /intento1 ntfs-3g silent,umask=0,locale=es_AR.utf8 0 0
/dev/sda5 /intento2 ntfs-3g silent,umask=0,locale=es_AR.utf8 0 0
/dev/sda6 /intento3 ntfs-3g silent,umask=0,locale=es_AR.utf8 0 0

```
sino monta copianos el error que da el comando:
```
 sudo mount /intento1
```

---

### Post by pump on 2006-12-06
Gracias por el howto. 
Es una cosa que tengo pendiente.

---

### Post by baalthazar on 2006-12-06
lo q pasa es q ya las particiones estan montadas pero con [[COLOR="RoyalBlue"][SIZE="2"]este howto[/SIZE][/COLOR]]("http://www.psychocats.net/ubuntu/mountwindows") que no soporta la escritura.. entocnes hasta donde ntiendo tengo que bajar las particiones, y volverlas a montar pero con este driver...

---

### Post by Nemesis Teufel on 2006-12-15
Y que es mas "recomendable" usar Samba o esto? Con samba se puede leer y escribir ntfs?

---

### Post by beuno on 2006-12-15
> **Nemesis Teufel said:**
> Y que es mas "recomendable" usar Samba o esto? Con samba se puede leer y escribir ntfs?

Para usar samba tiene que estar "compartido", y es finalmente algo mucho mas lento, asi que solo lo usaria para acceder a cosas en otras PCs.

Para acceder a particiones en tu misma PC con NTFS yo usaria esto.

---

### Post by Nemesis Teufel on 2006-12-15
Preguntas seguramente de boludo:

1º: cuando hago gksu gedit /etc/fstab me aparece esto:
> 
(gedit:5165): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


Sera por eso que no funciona?

2º: En caso de no ser la 1º, xq baalthazar tiene de otra forma? es asi como se hace.. tiene el fstab y directamente le manda el /intento1 sin el /media/; y bueno este es mi fstab:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1 /media/hda1 ntfs-3g defaults,locale=es_ES.utf8   0    0
/dev/hdb5 /media/hdb5 ntfs-3g defaults,locale=es_ES.utf8   0    0
# /dev/hdb6
UUID=94e9a067-ebd2-476f-a4d8-b82e85a5c8e1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1   
UUID=FC7CF8087CF7BC08 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb5   
UUID=2A7C1ECE7C1E94A3 /media/hdb5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb7
UUID=8f9828ed-1b0e-46a2-897b-ba261c3f4017 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


3º: El punto de montaje es ese? voy a media y ahi tengo los discos..
igualmente los monto con sudo mkdir /media/<punto de montaje> y me dice que no se puede crear el fichero xq ya existe. Eso quiere decir que ya lo tengo montado?

---

### Post by beuno on 2006-12-15
> **Nemesis Teufel said:**
> Preguntas seguramente de boludo:

1º: cuando hago gksu gedit /etc/fstab me aparece esto:


Proba:
```
sudo gedit /etc/fstab
```

---

### Post by Nemesis Teufel on 2006-12-15
Hago sudo gedit /etc/fstab y aparece:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1 /media/hda1 ntfs-3g defaults,locale=es_ES.utf8   0    0
/dev/hdb5 /media/hdb5 ntfs-3g defaults,locale=es_ES.utf8   0    0
# /dev/hdb6
UUID=94e9a067-ebd2-476f-a4d8-b82e85a5c8e1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1   
UUID=FC7CF8087CF7BC08 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb5   
UUID=2A7C1ECE7C1E94A3 /media/hdb5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb7
UUID=8f9828ed-1b0e-46a2-897b-ba261c3f4017 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

Tengo que cambiarle algo?
Para darme cuenta que funciona y verificar que puedo escribir/leer los discos.. tengo que reiniciar, ctrl+alt+backspace o ya puedo hacerlo directamente??

---

### Post by QUASAR_FREAK on 2006-12-15
comenta las lineas 
# /dev/hda1   
#UUID=FC7CF8087CF7BC08 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb5   
#UUID=2A7C1ECE7C1E94A3 /media/hdb5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1

Para darte cuenta que funciona o remontas los discos o reinicia y trata de crear una carpeta en alguno de los discos de wintendo.

---

### Post by Nemesis Teufel on 2006-12-15
wiii de maravilla!!
Tanto lio x no comentar algo.. me cache en diez.

---

### Post by Nemesis Teufel on 2006-12-26
Sirve tmb para leer/escribir archivos de Linux _desde_ Windows?

O es otro tema ese y tengo que instalar otra cosa desde windows?

---

### Post by MeduZa on 2006-12-26
> **Nemesis Teufel said:**
> Y que es mas "recomendable" usar Samba o esto? Con samba se puede leer y escribir ntfs?

yo estoy usando esto y hasta ahora todo bien
lo unico q note es q las carpetas encriptadas o shareadas no se ven

---

### Post by QUASAR_FREAK on 2006-12-26
> **Nemesis Teufel said:**
> Sirve tmb para leer/escribir archivos de Linux _desde_ Windows?

O es otro tema ese y tengo que instalar otra cosa desde windows?

esto es un driver para linux, para ver diskos de linux desde windows necesitas un driver ext2 o ext3 para windows, hay varios.

---

### Post by beuno on 2006-12-27
Driver para windows: [http://www.kbglob.com/gnulinux/driver-de-ext2ext3-xfs-y-reiserfs-para-windows/](http://www.kbglob.com/gnulinux/driver-de-ext2ext3-xfs-y-reiserfs-para-windows/)

---

### Post by Nemesis Teufel on 2006-12-27
Gracias! cuando tenga que bootear en win lo hare!

---

