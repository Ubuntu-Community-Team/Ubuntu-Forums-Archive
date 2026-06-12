---
title: "APT inservirble después de actualización"
date: 2019-02-09
forum: Argentina Team
---

### Post by Gbl_13 on 2019-02-09
Buenas noches. Hace más o menos una semana quise actualizar la versión de Ubuntu a través del actualizador de paquetes. Resulta que cometí el error de irme de casa durante el proceso; cuando llegué tenía la pantalla en negro sin responder a ninguna acción. Reinicié y arrancaba normal, sin darme errores en la carga, pero cuando debía de aparecer la pantalla de autenticación vuelve la pantalla en negro.

Probé entrar en modo recovery y me da errores tanto en DPKG como cuando intento actualizar APT. Estuve viendo que hay varios post en diferentes sitios, pero no me han dado resultado. Intente forzar la instalación de archivos no instalados-instala-, de limpiar APT, generé una nueva sources.list entre otras pero el error sigue.

Paso a modo de ejemplo lo que sucede con apt update y apt-upgrade (si no me equivoco, el error de este último es el mismo que en DPKG). Ahora tengo montado el sistema desde un live usb.

Si alguien puede tirarme alguna idea, desde ya le estoy agradecido. Saludos.

```
root@xubuntu:/# sudo apt-get update
Err:1 http://ar.archive.ubuntu.com/ubuntu xenial InRelease
  No se pudo resolver «ar.archive.ubuntu.com»
Err:2 http://ar.archive.ubuntu.com/ubuntu xenial-security InRelease
  No se pudo resolver «ar.archive.ubuntu.com»
Err:3 http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu xenial InRelease
  No se pudo resolver «ppa.launchpad.net»
Err:4 http://ar.archive.ubuntu.com/ubuntu xenial-updates InRelease
  No se pudo resolver «ar.archive.ubuntu.com»
Leyendo lista de paquetes... Hecho
W: Fallo al obtener http://ar.archive.ubuntu.com/ubuntu/dists/xenial/InRelease  No se pudo resolver «ar.archive.ubuntu.com»
W: Fallo al obtener http://ar.archive.ubuntu.com/ubuntu/dists/xenial-security/InRelease  No se pudo resolver «ar.archive.ubuntu.com»
W: Fallo al obtener http://ar.archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease  No se pudo resolver «ar.archive.ubuntu.com»
W: Fallo al obtener http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/xenial/InRelease  No se pudo resolver «ppa.launchpad.net»
W: No se han podido descargar algunos archivos de índice, se han omitido, o se han utilizado unos antiguos en su lugar.
```


```
root@xubuntu:/# apt-get upgrade
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Calculando la actualización... Hecho
0 actualizados, 0 nuevos se instalarán, 0 para eliminar y 0 no actualizados.
108 no instalados del todo o eliminados.
Se utilizarán 0 B de espacio de disco adicional después de esta operación.
¿Desea continuar? [S/n] S
E: No se pudo escribir el informe (¿Está montado «/dev/pts»?) - posix_openpt (19: No existe el dispositivo)
Configurando python3 (3.6.7-1~18.04) ...
running python rtupdate hooks for python3.6...
dpkg-query: atención: falta el fichero de lista de ficheros del paquete `dh-python', se supondrá que el paquete no tiene ningún fichero actualmente instalado
dpkg-query: atención: falta el fichero de lista de ficheros del paquete `dh-python', se supondrá que el paquete no tiene ningún fichero actualmente instalado
dpkg-query: el paquete `gedit' no está instalado.
Utilice dpkg --info (= dpkg-deb --info) para examinar archivos,
y dpkg --contents (= dpkg-deb --contents) para listar su contenido.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of gedit
error running python rtupdate hook gedit
dpkg-query: atención: falta el fichero de lista de ficheros del paquete `hplip-data', se supondrá que el paquete no tiene ningún fichero actualmente instalado
dpkg-query: atención: falta el fichero de lista de ficheros del paquete `hplip-data', se supondrá que el paquete no tiene ningún fichero actualmente instalado
dpkg-query: el paquete `lsb-core' no está instalado.
Utilice dpkg --info (= dpkg-deb --info) para examinar archivos,
y dpkg --contents (= dpkg-deb --contents) para listar su contenido.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of lsb-core
error running python rtupdate hook lsb-core
dpkg-query: el paquete `python3-uno' no está instalado.
Utilice dpkg --info (= dpkg-deb --info) para examinar archivos,
y dpkg --contents (= dpkg-deb --contents) para listar su contenido.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of python3-uno
error running python rtupdate hook python3-uno
dpkg-query: atención: falta el fichero de lista de ficheros del paquete `ubuntu-drivers-common', se supondrá que el paquete no tiene ningún fichero actualmente instalado
dpkg-query: atención: falta el fichero de lista de ficheros del paquete `ubuntu-drivers-common', se supondrá que el paquete no tiene ningún fichero actualmente instalado
dpkg-query: el paquete `xfpanel-switch' no está instalado.
Utilice dpkg --info (= dpkg-deb --info) para examinar archivos,
y dpkg --contents (= dpkg-deb --contents) para listar su contenido.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of xfpanel-switch
error running python rtupdate hook xfpanel-switch
dpkg: error al procesar el paquete python3 (--configure):
 installed python3 package post-installation script subprocess returned error exit status 4
dpkg: problemas de dependencias impiden la configuración de update-notifier-common:
 update-notifier-common depende de python3:any; sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete update-notifier-common (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de printer-driver-escpr:
 printer-driver-escpr depende de python3; sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete printer-driver-escpr (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python3-lxml:amd64:
 python3-lxml:amd64 depende de python3 (<< 3.7); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-lxml:amd64 depende de python3 (>= 3.6~); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-lxml:amd64 depende de python3:any (>= 3.3.2-2~); sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete python3-lxml:amd64 (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de language-selector-common:
 language-selector-common depende de python3:any (>= 3.3.2-2~); sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete language-selector-common (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de printer-driver-foo2zjs-common:
 printer-driver-foo2zjs-common depende de python3; sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete printer-driver-foo2zjs-common (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python3-idna:
 python3-idna depende de python3:any (>= 3.3.2-2~); sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete python3-idna (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python3-update-manager:
 python3-update-manager depende de python3:any (>= 3.3.2-2~); sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete python3-update-manager (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python3-six:
 python3-six depende de python3:any (>= 3.4~); sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete python3-six (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de openprinting-ppds:
 openprinting-ppds depende de python3; sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete openprinting-ppds (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python3-certifi:
 python3-certifi depende de python3:any (>= 3.4~); sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete python3-certifi (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python3-gi-cairo:
 python3-gi-cairo depende de python3 (<< 3.7); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-gi-cairo depende de python3 (>= 3.6~); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-gi-cairo depende de python3:any (>= 3.3~); sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete python3-gi-cairo (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python3-pkg-resources:
 python3-pkg-resources depende de python3:any (>= 3.3.2-2~); sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete python3-pkg-resources (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de ubuntu-release-upgrader-core:
 ubuntu-release-upgrader-core depende de python3:any (>= 3.2~); sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete ubuntu-release-upgrader-core (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python3-gi:
 python3-gi depende de python3 (<< 3.7); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-gi depende de python3 (>= 3.6~); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-gi depende de python3:any (>= 3.3.2-2~); sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete python3-gi (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python3-psutil:
 python3-psutil depende de python3 (<< 3.7); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-psutil depende de python3 (>= 3.6~); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-psutil depende de python3:any (>= 3.3.2-2~); sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete python3-psutil (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de printer-driver-pxljr:
 printer-driver-pxljr depende de python3; sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete printer-driver-pxljr (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python3-debconf:
 python3-debconf depende de python3:any (>= 3.3.2-2~); sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete python3-debconf (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python3-chardet:
 python3-chardet depende de python3:any (>= 3.3.2-2~); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-chardet depende de python3-pkg-resources; sin embargo:
 El paquete `python3-pkg-resources' no está configurado todavía.

dpkg: error al procesar el paquete python3-chardet (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python3-systemd:
 python3-systemd depende de python3 (<< 3.7); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-systemd depende de python3 (>= 3.6~); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-systemd depende de python3:any (>= 3.3.2-2~); sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete python3-systemd (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python3-requests:
 python3-requests depende de python3-certifi; sin embargo:
 El paquete `python3-certifi' no está configurado todavía.
 python3-requests depende de python3-chardet (<< 3.1.0); sin embargo:
 El paquete `python3-chardet' no está configurado todavía.
 python3-requests depende de python3-idna; sin embargo:
 El paquete `python3-idna' no está configurado todavía.
 python3-requests depende de python3:any (>= 3.4~); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-requests depende de python3-chardet (>= 3.0.2); sin embargo:
 El paquete `python3-chardet' no está configurado todavía.

dpkg: error al procesar el paquete python3-requests (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de printer-driver-foo2zjs:
 printer-driver-foo2zjs depende de printer-driver-foo2zjs-common (>= 20170320dfsg0-4); sin embargo:
 El paquete `printer-driver-foo2zjs-common' no está configurado todavía.

dpkg: error al procesar el paquete printer-driver-foo2zjs (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python3-gdbm:amd64:
 python3-gdbm:amd64 depende de python3 (>= 3.6.6-1~); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-gdbm:amd64 depende de python3 (<< 3.8); sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete python3-gdbm:amd64 (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python3-software-properties:
 python3-software-properties depende de python3:any (>= 3.3.2-2~); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-software-properties depende de python3; sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-software-properties depende de python3-gi; sin embargo:
 El paquete `python3-gi' no está configurado todavía.

dpkg: error al procesar el paquete python3-software-properties (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python3-urllib3:
 python3-urllib3 depende de python3:any (>= 3.3.2-2~); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-urllib3 depende de python3-six; sin embargo:
 El paquete `python3-six' no está configurado todavía.

dpkg: error al procesar el paquete python3-urllib3 (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python3-reportlab-accel:amd64:
 python3-reportlab-accel:amd64 depende de python3 (<< 3.7); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-reportlab-accel:amd64 depende de python3 (>= 3.6~); sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete python3-reportlab-accel:amd64 (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python3-cairo:amd64:
 python3-cairo:amd64 depende de python3 (<< 3.7); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-cairo:amd64 depende de python3 (>= 3.6~); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-cairo:amd64 depende de python3:any (>= 3.3.2-2~); sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete python3-cairo:amd64 (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de gnome-menus:
 gnome-menus depende de python3:any (>= 3.1~); sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete gnome-menus (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python3-lib2to3:
 python3-lib2to3 depende de python3 (>= 3.6.6-1~); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-lib2to3 depende de python3 (<< 3.8); sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete python3-lib2to3 (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de dh-python:
 dh-python depende de python3:any (>= 3.3.2-2~); sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete dh-python (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python3-distutils:
 python3-distutils depende de python3 (>= 3.6.6-1~); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-distutils depende de python3 (<< 3.8); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-distutils depende de python3-lib2to3 (>= 3.6.4); sin embargo:
 El paquete `python3-lib2to3' no está configurado todavía.

dpkg: error al procesar el paquete python3-distutils (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python3-distupgrade:
 python3-distupgrade depende de python3:any (>= 3.3.2-2~); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-distupgrade depende de python3-update-manager (>= 1:18.04.11.9~); sin embargo:
 El paquete `python3-update-manager' no está configurado todavía.

dpkg: error al procesar el paquete python3-distupgrade (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python3-renderpm:amd64:
 python3-renderpm:amd64 depende de python3 (<< 3.7); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-renderpm:amd64 depende de python3 (>= 3.6~); sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete python3-renderpm:amd64 (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de foomatic-db-compressed-ppds:
 foomatic-db-compressed-ppds depende de python3; sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete foomatic-db-compressed-ppds (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de software-properties-common:
 software-properties-common depende de python3:any (>= 3.3.2-2~); sin embargo:
 El paquete `python3' no está configurado todavía.
 software-properties-common depende de python3; sin embargo:
 El paquete `python3' no está configurado todavía.
 software-properties-common depende de python3-gi; sin embargo:
 El paquete `python3-gi' no está configurado todavía.
 software-properties-common depende de python3-software-properties (= 0.96.24.32.7); sin embargo:
 El paquete `python3-software-properties' no está configurado todavía.

dpkg: error al procesar el paquete software-properties-common (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden procesar los disparadores de ufw:
 ufw depende de python3:any (>= 3.3.2-2~); sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete ufw (--configure):
 problemas de dependencias - no se procesarán los disparadores
dpkg: problemas de dependencias impiden la configuración de python3-distro-info:
 python3-distro-info depende de python3:any (>= 3.3.2-2~); sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete python3-distro-info (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python3-pycurl:
 python3-pycurl depende de python3 (<< 3.7); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-pycurl depende de python3 (>= 3.6~); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-pycurl depende de python3:any (>= 3.3.2-2~); sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete python3-pycurl (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python3-pil:amd64:
 python3-pil:amd64 depende de python3 (<< 3.7); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-pil:amd64 depende de python3 (>= 3.6~); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-pil:amd64 depende de python3:any (>= 3.3.2-2~); sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete python3-pil:amd64 (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python3-cups:
 python3-cups depende de python3 (<< 3.7); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-cups depende de python3 (>= 3.6~); sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete python3-cups (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de update-manager-core:
 update-manager-core depende de python3:any (>= 3.2~); sin embargo:
 El paquete `python3' no está configurado todavía.
 update-manager-core depende de python3-update-manager (= 1:18.04.11.9); sin embargo:
 El paquete `python3-update-manager' no está configurado todavía.
 update-manager-core depende de python3-distro-info; sin embargo:
 El paquete `python3-distro-info' no está configurado todavía.
 update-manager-core depende de ubuntu-release-upgrader-core (>= 1:18.04.9); sin embargo:
 El paquete `ubuntu-release-upgrader-core' no está configurado todavía.

dpkg: error al procesar el paquete update-manager-core (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden procesar los disparadores de gconf2:
 gconf2 depende de python3:any; sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete gconf2 (--configure):
 problemas de dependencias - no se procesarán los disparadores
dpkg: problemas de dependencias impiden la configuración de python3-apt:
 python3-apt depende de python3 (<< 3.7); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-apt depende de python3 (>= 3.6~); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-apt depende de python3:any (>= 3.3.2-2~); sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete python3-apt (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python3-dbus:
 python3-dbus depende de python3 (<< 3.7); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-dbus depende de python3 (>= 3.6~); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-dbus depende de python3:any (>= 3.4~); sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete python3-dbus (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden procesar los disparadores de gconf2:
 gconf2 depende de python3:any; sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete gconf2 (--configure):
 problemas de dependencias - no se procesarán los disparadores
dpkg: problemas de dependencias impiden procesar los disparadores de gconf2:
 gconf2 depende de python3:any; sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete gconf2 (--configure):
 problemas de dependencias - no se procesarán los disparadores
dpkg: problemas de dependencias impiden procesar los disparadores de gconf2:
 gconf2 depende de python3:any; sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete gconf2 (--configure):
 problemas de dependencias - no se procesarán los disparadores
dpkg: problemas de dependencias impiden procesar los disparadores de gconf2:
 gconf2 depende de python3:any; sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete gconf2 (--configure):
 problemas de dependencias - no se procesarán los disparadores
dpkg: problemas de dependencias impiden procesar los disparadores de gconf2:
 gconf2 depende de python3:any; sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete gconf2 (--configure):
 problemas de dependencias - no se procesarán los disparadores
dpkg: problemas de dependencias impiden procesar los disparadores de gconf2:
 gconf2 depende de python3:any; sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete gconf2 (--configure):
 problemas de dependencias - no se procesarán los disparadores
dpkg: problemas de dependencias impiden procesar los disparadores de gconf2:
 gconf2 depende de python3:any; sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete gconf2 (--configure):
 problemas de dependencias - no se procesarán los disparadores
dpkg: demasiados errores, parando
No se escribió un informe «apport» porque el mensaje de error indica que es un mensaje de error asociado a un fallo previo.
No se escribió un informe «apport» porque el mensaje de error indica que es un mensaje de error asociado a un fallo previo.
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
Se encontraron errores al procesar:
 python3
 update-notifier-common
 printer-driver-escpr
 python3-lxml:amd64
 language-selector-common
 printer-driver-foo2zjs-common
 python3-idna
 python3-update-manager
 python3-six
 openprinting-ppds
 python3-certifi
 python3-gi-cairo
 python3-pkg-resources
 ubuntu-release-upgrader-core
 python3-gi
 python3-psutil
 printer-driver-pxljr
 python3-debconf
 python3-chardet
 python3-systemd
 python3-requests
 printer-driver-foo2zjs
 python3-gdbm:amd64
 python3-software-properties
 python3-urllib3
 python3-reportlab-accel:amd64
 python3-cairo:amd64
 gnome-menus
 python3-lib2to3
 dh-python
 python3-distutils
 python3-distupgrade
 python3-renderpm:amd64
 foomatic-db-compressed-ppds
 software-properties-common
 ufw
 python3-distro-info
 python3-pycurl
 python3-pil:amd64
 python3-cups
 update-manager-core
 gconf2
 python3-apt
 python3-dbus
 gconf2
 gconf2
 gconf2
 gconf2
 gconf2
 gconf2
 gconf2
Proceso detenido por haber demasiados errores.
E: Sub-process /usr/bin/dpkg returned an error code (1) 
```

 ```
 [root@xubuntu:/# sudo apt install -f
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
0 actualizados, 0 nuevos se instalarán, 0 para eliminar y 0 no actualizados.
108 no instalados del todo o eliminados.
Se utilizarán 0 B de espacio de disco adicional después de esta operación.
E: No se pudo escribir el informe (¿Está montado «/dev/pts»?) - posix_openpt (19: No existe el dispositivo)
Configurando python3 (3.6.7-1~18.04) ...
running python rtupdate hooks for python3.6...
dpkg-query: atención: falta el fichero de lista de ficheros del paquete `dh-python', se supondrá que el paquete no tiene ningún fichero actualmente instalado
dpkg-query: atención: falta el fichero de lista de ficheros del paquete `dh-python', se supondrá que el paquete no tiene ningún fichero actualmente instalado
dpkg-query: el paquete `gedit' no está instalado.
Utilice dpkg --info (= dpkg-deb --info) para examinar archivos,
y dpkg --contents (= dpkg-deb --contents) para listar su contenido.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of gedit
error running python rtupdate hook gedit
dpkg-query: atención: falta el fichero de lista de ficheros del paquete `hplip-data', se supondrá que el paquete no tiene ningún fichero actualmente instalado
dpkg-query: atención: falta el fichero de lista de ficheros del paquete `hplip-data', se supondrá que el paquete no tiene ningún fichero actualmente instalado
dpkg-query: el paquete `lsb-core' no está instalado.
Utilice dpkg --info (= dpkg-deb --info) para examinar archivos,
y dpkg --contents (= dpkg-deb --contents) para listar su contenido.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of lsb-core
error running python rtupdate hook lsb-core
dpkg-query: el paquete `python3-uno' no está instalado.
Utilice dpkg --info (= dpkg-deb --info) para examinar archivos,
y dpkg --contents (= dpkg-deb --contents) para listar su contenido.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of python3-uno
error running python rtupdate hook python3-uno
dpkg-query: atención: falta el fichero de lista de ficheros del paquete `ubuntu-drivers-common', se supondrá que el paquete no tiene ningún fichero actualmente instalado
dpkg-query: atención: falta el fichero de lista de ficheros del paquete `ubuntu-drivers-common', se supondrá que el paquete no tiene ningún fichero actualmente instalado
dpkg-query: el paquete `xfpanel-switch' no está instalado.
Utilice dpkg --info (= dpkg-deb --info) para examinar archivos,
y dpkg --contents (= dpkg-deb --contents) para listar su contenido.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of xfpanel-switch
error running python rtupdate hook xfpanel-switch
dpkg: error al procesar el paquete python3 (--configure):
 installed python3 package post-installation script subprocess returned error exit status 4
dpkg: problemas de dependencias impiden la configuración de update-notifier-common:
 update-notifier-common depende de python3:any; sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete update-notifier-common (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de printer-driver-escpr:
 printer-driver-escpr depende de python3; sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete printer-driver-escpr (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python3-lxml:amd64:
 python3-lxml:amd64 depende de python3 (<< 3.7); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-lxml:amd64 depende de python3 (>= 3.6~); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-lxml:amd64 depende de python3:any (>= 3.3.2-2~); sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete python3-lxml:amd64 (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de language-selector-common:
 language-selector-common depende de python3:any (>= 3.3.2-2~); sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete language-selector-common (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de printer-driver-foo2zjs-common:
 printer-driver-foo2zjs-common depende de python3; sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete printer-driver-foo2zjs-common (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python3-idna:
 python3-idna depende de python3:any (>= 3.3.2-2~); sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete python3-idna (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python3-update-manager:
 python3-update-manager depende de python3:any (>= 3.3.2-2~); sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete python3-update-manager (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python3-six:
 python3-six depende de python3:any (>= 3.4~); sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete python3-six (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de openprinting-ppds:
 openprinting-ppds depende de python3; sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete openprinting-ppds (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python3-certifi:
 python3-certifi depende de python3:any (>= 3.4~); sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete python3-certifi (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python3-gi-cairo:
 python3-gi-cairo depende de python3 (<< 3.7); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-gi-cairo depende de python3 (>= 3.6~); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-gi-cairo depende de python3:any (>= 3.3~); sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete python3-gi-cairo (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python3-pkg-resources:
 python3-pkg-resources depende de python3:any (>= 3.3.2-2~); sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete python3-pkg-resources (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de ubuntu-release-upgrader-core:
 ubuntu-release-upgrader-core depende de python3:any (>= 3.2~); sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete ubuntu-release-upgrader-core (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python3-gi:
 python3-gi depende de python3 (<< 3.7); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-gi depende de python3 (>= 3.6~); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-gi depende de python3:any (>= 3.3.2-2~); sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete python3-gi (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python3-psutil:
 python3-psutil depende de python3 (<< 3.7); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-psutil depende de python3 (>= 3.6~); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-psutil depende de python3:any (>= 3.3.2-2~); sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete python3-psutil (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de printer-driver-pxljr:
 printer-driver-pxljr depende de python3; sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete printer-driver-pxljr (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python3-debconf:
 python3-debconf depende de python3:any (>= 3.3.2-2~); sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete python3-debconf (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python3-chardet:
 python3-chardet depende de python3:any (>= 3.3.2-2~); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-chardet depende de python3-pkg-resources; sin embargo:
 El paquete `python3-pkg-resources' no está configurado todavía.

dpkg: error al procesar el paquete python3-chardet (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python3-systemd:
 python3-systemd depende de python3 (<< 3.7); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-systemd depende de python3 (>= 3.6~); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-systemd depende de python3:any (>= 3.3.2-2~); sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete python3-systemd (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python3-requests:
 python3-requests depende de python3-certifi; sin embargo:
 El paquete `python3-certifi' no está configurado todavía.
 python3-requests depende de python3-chardet (<< 3.1.0); sin embargo:
 El paquete `python3-chardet' no está configurado todavía.
 python3-requests depende de python3-idna; sin embargo:
 El paquete `python3-idna' no está configurado todavía.
 python3-requests depende de python3:any (>= 3.4~); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-requests depende de python3-chardet (>= 3.0.2); sin embargo:
 El paquete `python3-chardet' no está configurado todavía.

dpkg: error al procesar el paquete python3-requests (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de printer-driver-foo2zjs:
 printer-driver-foo2zjs depende de printer-driver-foo2zjs-common (>= 20170320dfsg0-4); sin embargo:
 El paquete `printer-driver-foo2zjs-common' no está configurado todavía.

dpkg: error al procesar el paquete printer-driver-foo2zjs (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python3-gdbm:amd64:
 python3-gdbm:amd64 depende de python3 (>= 3.6.6-1~); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-gdbm:amd64 depende de python3 (<< 3.8); sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete python3-gdbm:amd64 (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python3-software-properties:
 python3-software-properties depende de python3:any (>= 3.3.2-2~); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-software-properties depende de python3; sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-software-properties depende de python3-gi; sin embargo:
 El paquete `python3-gi' no está configurado todavía.

dpkg: error al procesar el paquete python3-software-properties (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python3-urllib3:
 python3-urllib3 depende de python3:any (>= 3.3.2-2~); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-urllib3 depende de python3-six; sin embargo:
 El paquete `python3-six' no está configurado todavía.

dpkg: error al procesar el paquete python3-urllib3 (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python3-reportlab-accel:amd64:
 python3-reportlab-accel:amd64 depende de python3 (<< 3.7); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-reportlab-accel:amd64 depende de python3 (>= 3.6~); sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete python3-reportlab-accel:amd64 (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python3-cairo:amd64:
 python3-cairo:amd64 depende de python3 (<< 3.7); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-cairo:amd64 depende de python3 (>= 3.6~); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-cairo:amd64 depende de python3:any (>= 3.3.2-2~); sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete python3-cairo:amd64 (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de gnome-menus:
 gnome-menus depende de python3:any (>= 3.1~); sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete gnome-menus (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python3-lib2to3:
 python3-lib2to3 depende de python3 (>= 3.6.6-1~); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-lib2to3 depende de python3 (<< 3.8); sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete python3-lib2to3 (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de dh-python:
 dh-python depende de python3:any (>= 3.3.2-2~); sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete dh-python (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python3-distutils:
 python3-distutils depende de python3 (>= 3.6.6-1~); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-distutils depende de python3 (<< 3.8); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-distutils depende de python3-lib2to3 (>= 3.6.4); sin embargo:
 El paquete `python3-lib2to3' no está configurado todavía.

dpkg: error al procesar el paquete python3-distutils (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python3-distupgrade:
 python3-distupgrade depende de python3:any (>= 3.3.2-2~); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-distupgrade depende de python3-update-manager (>= 1:18.04.11.9~); sin embargo:
 El paquete `python3-update-manager' no está configurado todavía.

dpkg: error al procesar el paquete python3-distupgrade (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python3-renderpm:amd64:
 python3-renderpm:amd64 depende de python3 (<< 3.7); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-renderpm:amd64 depende de python3 (>= 3.6~); sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete python3-renderpm:amd64 (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de foomatic-db-compressed-ppds:
 foomatic-db-compressed-ppds depende de python3; sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete foomatic-db-compressed-ppds (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de software-properties-common:
 software-properties-common depende de python3:any (>= 3.3.2-2~); sin embargo:
 El paquete `python3' no está configurado todavía.
 software-properties-common depende de python3; sin embargo:
 El paquete `python3' no está configurado todavía.
 software-properties-common depende de python3-gi; sin embargo:
 El paquete `python3-gi' no está configurado todavía.
 software-properties-common depende de python3-software-properties (= 0.96.24.32.7); sin embargo:
 El paquete `python3-software-properties' no está configurado todavía.

dpkg: error al procesar el paquete software-properties-common (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden procesar los disparadores de ufw:
 ufw depende de python3:any (>= 3.3.2-2~); sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete ufw (--configure):
 problemas de dependencias - no se procesarán los disparadores
dpkg: problemas de dependencias impiden la configuración de python3-distro-info:
 python3-distro-info depende de python3:any (>= 3.3.2-2~); sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete python3-distro-info (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python3-pycurl:
 python3-pycurl depende de python3 (<< 3.7); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-pycurl depende de python3 (>= 3.6~); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-pycurl depende de python3:any (>= 3.3.2-2~); sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete python3-pycurl (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python3-pil:amd64:
 python3-pil:amd64 depende de python3 (<< 3.7); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-pil:amd64 depende de python3 (>= 3.6~); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-pil:amd64 depende de python3:any (>= 3.3.2-2~); sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete python3-pil:amd64 (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python3-cups:
 python3-cups depende de python3 (<< 3.7); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-cups depende de python3 (>= 3.6~); sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete python3-cups (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de update-manager-core:
 update-manager-core depende de python3:any (>= 3.2~); sin embargo:
 El paquete `python3' no está configurado todavía.
 update-manager-core depende de python3-update-manager (= 1:18.04.11.9); sin embargo:
 El paquete `python3-update-manager' no está configurado todavía.
 update-manager-core depende de python3-distro-info; sin embargo:
 El paquete `python3-distro-info' no está configurado todavía.
 update-manager-core depende de ubuntu-release-upgrader-core (>= 1:18.04.9); sin embargo:
 El paquete `ubuntu-release-upgrader-core' no está configurado todavía.

dpkg: error al procesar el paquete update-manager-core (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden procesar los disparadores de gconf2:
 gconf2 depende de python3:any; sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete gconf2 (--configure):
 problemas de dependencias - no se procesarán los disparadores
dpkg: problemas de dependencias impiden la configuración de python3-apt:
 python3-apt depende de python3 (<< 3.7); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-apt depende de python3 (>= 3.6~); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-apt depende de python3:any (>= 3.3.2-2~); sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete python3-apt (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de python3-dbus:
 python3-dbus depende de python3 (<< 3.7); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-dbus depende de python3 (>= 3.6~); sin embargo:
 El paquete `python3' no está configurado todavía.
 python3-dbus depende de python3:any (>= 3.4~); sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete python3-dbus (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden procesar los disparadores de gconf2:
 gconf2 depende de python3:any; sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete gconf2 (--configure):
 problemas de dependencias - no se procesarán los disparadores
dpkg: problemas de dependencias impiden procesar los disparadores de gconf2:
 gconf2 depende de python3:any; sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete gconf2 (--configure):
 problemas de dependencias - no se procesarán los disparadores
dpkg: problemas de dependencias impiden procesar los disparadores de gconf2:
 gconf2 depende de python3:any; sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete gconf2 (--configure):
 problemas de dependencias - no se procesarán los disparadores
dpkg: problemas de dependencias impiden procesar los disparadores de gconf2:
 gconf2 depende de python3:any; sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete gconf2 (--configure):
 problemas de dependencias - no se procesarán los disparadores
dpkg: problemas de dependencias impiden procesar los disparadores de gconf2:
 gconf2 depende de python3:any; sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete gconf2 (--configure):
 problemas de dependencias - no se procesarán los disparadores
dpkg: problemas de dependencias impiden procesar los disparadores de gconf2:
 gconf2 depende de python3:any; sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete gconf2 (--configure):
 problemas de dependencias - no se procesarán los disparadores
dpkg: problemas de dependencias impiden procesar los disparadores de gconf2:
 gconf2 depende de python3:any; sin embargo:
 El paquete `python3' no está configurado todavía.

dpkg: error al procesar el paquete gconf2 (--configure):
 problemas de dependencias - no se procesarán los disparadores
dpkg: demasiados errores, parando
No se escribió un informe «apport» porque el mensaje de error indica que es un mensaje de error asociado a un fallo previo.
No se escribió un informe «apport» porque el mensaje de error indica que es un mensaje de error asociado a un fallo previo.
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
No se escribió ningún informe «apport» porque ya se ha alcanzado el valor de «MaxReports»
Se encontraron errores al procesar:
 python3
 update-notifier-common
 printer-driver-escpr
 python3-lxml:amd64
 language-selector-common
 printer-driver-foo2zjs-common
 python3-idna
 python3-update-manager
 python3-six
 openprinting-ppds
 python3-certifi
 python3-gi-cairo
 python3-pkg-resources
 ubuntu-release-upgrader-core
 python3-gi
 python3-psutil
 printer-driver-pxljr
 python3-debconf
 python3-chardet
 python3-systemd
 python3-requests
 printer-driver-foo2zjs
 python3-gdbm:amd64
 python3-software-properties
 python3-urllib3
 python3-reportlab-accel:amd64
 python3-cairo:amd64
 gnome-menus
 python3-lib2to3
 dh-python
 python3-distutils
 python3-distupgrade
 python3-renderpm:amd64
 foomatic-db-compressed-ppds
 software-properties-common
 ufw
 python3-distro-info
 python3-pycurl
 python3-pil:amd64
 python3-cups
 update-manager-core
 gconf2
 python3-apt
 python3-dbus
 gconf2
 gconf2
 gconf2
 gconf2
 gconf2
 gconf2
 gconf2
Proceso detenido por haber demasiados errores.
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

