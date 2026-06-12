---
title: "Problema con plugin de flash en ubuntu 7.10"
date: 2007-12-11
forum: Argentina Team
---

### Post by jotix on 2007-12-11
Buenas tengo instalada la version 7.10 64 bits, ya con varias instalaciones encima en el termino de 3 semanas.

Ayer reinstale el SO nuevamente pero al momento de instalar el plugin del flash para el firefox, no lo termina de instalar bien.

Trate de buscar la solución por todos lados y encontre varias formas bastante complicadas de instalar el plugin, pero aclaro que hasta ayer tambien tenia instalada la misma version 7.10 64bits de ubuntu, y para instalar dicho plugin que ahora me da problemas, una semana antes no tuve mas que hacer click en "descargar plugin" y me funcionaba perfecto.

Lo que no entiendo es como antes me funciono sin ningun problema y ahora no, aclaro ya de antemano que estoy totalmente seguro de haber usado el mismo CD con la misma versión de ubuntu para instalar.

Desde ya muchas gracias...

este es el mensaje que me da el synaptic

"Se han aplicado todos los cambios con exito. Puede cerrar la ventana ahora"

pero mirando en la ventanita de detalles me sale esto al final:

.......
.......
download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed

---

### Post by joseluis on 2007-12-11
te recomiendo instalar la vesión que no es la de 64. Ocurre que esta versión de 64 necesita que una gran cantidad de soft y de hard estén funcionando a 64 y no siempre es  asi. Buen...es un consejo, proba eso ya que vas  a instalar de nuevo.
Suerte, y conta como fue.

---

### Post by jotix on 2007-12-11
lo que me hace estallar la cabeza es que este mismo plugin hace unos dias me funcionaba ok, quisiera poder solucionarlo sin tener que poner la version 32 bits ya que por ahora con la de 64 vengo super bien solo tengo este pequenio problema, aclaro que tampoco fuedo hacer funcionar el flash con el swiftfox.

En otro foro lei que ese error se debe a que adobe cambio el paquete...entonces por eso antes funcionaba y ahora no...con mis pocos conocimientos esto me suena logico mirando el error que detallo arriba, lo que quisiera es tener una opinion un poco mas cualificada y de paso ver si se puede solucionar de alguna manera.

---

### Post by jotix on 2007-12-11
bueno tras muchas horas de busqueda incesante, aqui esta la solucion a dicho problema, que se debe a que adobe actualizo el paquete del plugin dejandole la misma version, y es asi como el chequeo del archivo tira error...

La solucion fue la siguiente

1. sudo apt-get install flashplugin-nonfree
2. sudo nano /var/lib/dpkg/info/flashplugin-nonfree.postinst
3. Editar:

```

# verify MD5 checksum of (copied or downloaded) tarball
rm -rf install_flash_player_9_linux/
echo "821cc72359a937caef85bb4cc74ef5cd install_flash_player_9_linux.tar.gz"| md5sum -c > /dev/null 2>&1 \
|| fp_exit_with_error "md5sum mismatch install_flash_player_9_linux.tar.gz"

# unpacking and checking the plugin
tar xzf install_flash_player_9_linux.tar.gz || fp_exit_with_error "cannot unpack plugin"
echo "be5a2f9032f8fc8bccbbf5d96c5028f9 install_flash_player_9_linux/libflashplayer.so"| md5sum -c > /dev/null 2>&1 \
|| fp_exit_with_error "plugin changed, not trusted"
echo "a81fd3b03b8c6d6e5a14298110718d3f install_flash_player_9_linux/flashplayer.xpt"| md5sum -c > /dev/null 2>&1 \
|| fp_exit_with_error "plugin changed, not trusted"
```

a lo siguiente:

```

 # verify MD5 checksum of (copied or downloaded) tarball
rm -rf install_flash_player_9_linux/
echo "93b7c48eaa492237b807a3ae1de65cf9  install_flash_player_9_linux.tar.gz"| md5sum -c > /dev/null 2>&1 \
|| fp_exit_with_error "md5sum mismatch install_flash_player_9_linux.tar.gz"

# unpacking and checking the plugin
tar xzf install_flash_player_9_linux.tar.gz || fp_exit_with_error "cannot unpack plugin"
#echo "a81fd3b03b8c6d6e5a14298110718d3f  install_flash_player_9_linux/flashplayer.xpt"| md5sum -c > /dev/$
#echo "13ce705df5d47422a9192b29827544e8  install_flash_player_9_linux/libflashplayer.so"| md5sum -c > /de$
#|| fp_exit_with_error "plugin changed, not trusted"
```

4. sudo dpkg-reconfigure flashplugin-nonfree

Y YA ESTA FUNCIONA OK....

Bueno me respondo la solucion a mi mismo por si alguien necesita ayuda con este tema...

---

### Post by santiagoward2000 on 2007-12-12
Gracias jotix! Anduvo!!!! :KS

---

### Post by elpitagorico on 2008-01-01
Graciass!!!!!!!!!!!!!!!!!!

Es la solución perfecta a un extraño problema.

Propongo un nuevo código, ya que el MD5SUM de install_flash_player_9_linux, suele cambiar, lo cual hace temporal la solución.

Paso por paso:

1. sudo apt-get install flashplugin-nonfree
2. gksudo gedit /var/lib/dpkg/info/flashplugin-nonfree.postinst
3. Realizar las siguientes modificaciones:

Sustituir:
```
# verify MD5 checksum of (copied or downloaded) tarball
rm -rf install_flash_player_9_linux/
echo "821cc72359a937caef85bb4cc74ef5cd install_flash_player_9_linux.tar.gz"| md5sum -c > /dev/null 2>&1 \
|| fp_exit_with_error "md5sum mismatch install_flash_player_9_linux.tar.gz"

# unpacking and checking the plugin
tar xzf install_flash_player_9_linux.tar.gz || fp_exit_with_error "cannot unpack plugin"
echo "be5a2f9032f8fc8bccbbf5d96c5028f9 install_flash_player_9_linux/libflashplayer.so"| md5sum -c > /dev/null 2>&1 \
|| fp_exit_with_error "plugin changed, not trusted"
echo "a81fd3b03b8c6d6e5a14298110718d3f install_flash_player_9_linux/flashplayer.xpt"| md5sum -c > /dev/null 2>&1 \
|| fp_exit_with_error "plugin changed, not trusted"
```

Con:
```
# verify MD5 checksum of (copied or downloaded) tarball
#rm -rf install_flash_player_9_linux/
#echo "93b7c48eaa492237b807a3ae1de65cf9 install_flash_player_9_linux.tar.gz"| md5sum -c > /dev/null 2>&1 \
#|| fp_exit_with_error "md5sum mismatch install_flash_player_9_linux.tar.gz"

# unpacking and checking the plugin
tar xzf install_flash_player_9_linux.tar.gz || fp_exit_with_error "cannot unpack plugin"
#echo "a81fd3b03b8c6d6e5a14298110718d3f install_flash_player_9_linux/flashplayer.xpt"| md5sum -c > /dev/$
#echo "13ce705df5d47422a9192b29827544e8 install_flash_player_9_linux/libflashplayer.so"| md5sum -c > /de$
#|| fp_exit_with_error "plugin changed, not trusted"
```

4. sudo dpkg-reconfigure flashplugin-nonfree

---

### Post by Zenerek on 2008-01-09
Muchas gracias por la ayuda mis amigos, ignoren mi espanol si no es muy perfecto, es que ingles se ah echo my lengua mayor,ahora at ver si trabaja

---

