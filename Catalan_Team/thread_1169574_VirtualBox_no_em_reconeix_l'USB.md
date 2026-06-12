---
title: "VirtualBox no em reconeix l'USB"
date: 2009-05-25
forum: Catalan Team
---

### Post by prostata on 2009-05-25
Avui per fi he instal·lat virtualbox ja puc veure wxp en el meu Jaunty...tot va de perles en la maquina virtual wxp, excepte que encara que veig tot el wxp, aquest no em reconeix l'USB.

Dins de VirtualBox he mirat l'apartat configuració USB i tinc activat Habilitar controlador USB però no funciona, he habilitat també enable USB 2.0 (EHCI) controller i tampoc ho reconeix en sessió wxp de virtualbox.

Em temo que em deixo alguna cosa que se m'escapa...què pot ser...??

Per cert l'unitat CD-DVD tanpoc la reconeix

Gràcies

---

### Post by PatrickVogeli on 2009-05-25
afegeix això a l'arxiu /etc/fstab:

```

none 		/proc/bus/usb 	usbfs 	devgid=123,devmode=664 		0 	0
```

i afegeix això a l'arxiu /etc/init.d/mountdevsubfs.sh, despres de la línia que diu domount devpts "" /dev/pts devpts -onoexec,nosuid,gid=$TTYGRP,mode=$TTYMODE (és la linia numero 41):

```

	mkdir -p /dev/bus/usb/.usbfs
	domount usbfs &#8220;&#8221; /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	mount &#8211;rbind /dev/bus/usb /proc/bus/usb
```

Reinicia i em sembla que ja hauria de funcionar.

salut

---

### Post by prostata on 2009-05-25
He fet el que em dius, però no va, et paso el contingut dels dos arxius que he tocat, primer el fstab:


# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=211df460-f955-488a-8763-9b2d5248ec9d /               ext4    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
none 		/proc/bus/usb 	usbfs 	devgid=123,devmode=664 		0 	0

-------------------------------------------------------------------
i ara init:

#! /bin/sh
### BEGIN INIT INFO
# Provides:          mountdevsubfs
# Required-Start:    mountkernfs
# Required-Stop:
# Should-Start:      udev
# Default-Start:     S
# Default-Stop:
# Short-Description: Mount special file systems under /dev.
# Description:       Mount the virtual filesystems the kernel provides
#                    that ordinarily live under the /dev filesystem.
### END INIT INFO
#
# This script gets called multiple times during boot
#

PATH=/lib/init:/sbin:/bin
TTYGRP=5
TTYMODE=620
[ -f /etc/default/devpts ] && . /etc/default/devpts

TMPFS_SIZE=
[ -f /etc/default/tmpfs ] && . /etc/default/tmpfs

KERNEL="$(uname -s)"

. /lib/lsb/init-functions
. /lib/init/mount-functions.sh

do_start () {
	#
	# Mount a tmpfs on /dev/shm
	#
	SHM_OPT=
	[ "${SHM_SIZE:=$TMPFS_SIZE}" ] && SHM_OPT=",size=$SHM_SIZE"
	domount tmpfs shmfs /dev/shm tmpfs -onosuid,nodev$SHM_OPT

	#
	# Mount /dev/pts. Master ptmx node is already created by udev.
	#
        domount devpts "" /dev/pts devpts -onoexec,nosuid,gid=$TTYGRP,mode=$TTYMODE
mkdir -p /dev/bus/usb/.usbfs
	domount usbfs “” /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	mount –rbind /dev/bus/usb /proc/bus/usb
}

case "$1" in
  "")
	echo "Warning: mountdevsubfs should be called with the 'start' argument." >&2
	do_start
	;;
  start)
	do_start
	;;
  restart|reload|force-reload)
	echo "Error: argument '$1' not supported" >&2
	exit 3
	;;
  stop)
	# No-op
	;;
  *)
	echo "Usage: mountdevsubfs [start|stop]" >&2
	exit 3
	;;
esac

No vec on pot estar l'error de manera que pot ser tu si ho veus..

per cert la versió que tinc de virtualbox e:SunVirtualBox 2.2.2.

---

### Post by prostata on 2009-05-25
Ja veig l'unitat CDrom i la disketera, no els havia montat en fer la configuració del VB, però encara no puc veure el pendrive...

gràcies

---

### Post by PatrickVogeli on 2009-05-25
Pot ser que no hagis seleccionat el pendrive per a que agafi el control el sistema operatiu virtual?

El virtualbox, encara que tingui l'usb activat i aixo, no ho fa automaticament... li has de dir tu. Comprova tambe que tinguis la funcionalitat usb activa a la configuracio.

salut

---

### Post by uidb4056 on 2009-05-25
> **prostata said:**
> Avui per fi he instal·lat virtualbox ja puc veure wxp en el meu Jaunty...tot va de perles en la maquina virtual wxp, excepte que encara que veig tot el wxp, aquest no em reconeix l'USB.

Dins de VirtualBox he mirat l'apartat configuració USB i tinc activat Habilitar controlador USB però no funciona, he habilitat també enable USB 2.0 (EHCI) controller i tampoc ho reconeix en sessió wxp de virtualbox.

Em temo que em deixo alguna cosa que se m'escapa...què pot ser...??

Per cert l'unitat CD-DVD tanpoc la reconeix

Gràcies

El teu usuari te que ser membre del grup vboxusers, a més el gid=123 te que ser el del grup vboxusers

---

### Post by jerec on 2009-05-25
Dedueixo que has instal·lat la VirtualBox-OSE (Open Source Edition)

Hauràs de posar la No OpenSource (Si per exemple tens dual monitor, necessites aquesta) i per suposat instal·lar les "Guest Additions"

Aquí tens el que fa de mes a mes:


Closed-source feature

The following list shows the enterprise features that are only present in the closed-source edition. Note that this list may change over time as some of these features will eventually be made available with the open-source version as well.

    * Remote Display Protocol (RDP) Server 

    This component implements a complete RDP server on top of the virtual hardware and allows users to connect to a virtual machine remotely using any RDP compatible client.

    * USB support 

    VirtualBox implements a virtual USB controller and supports passing through USB 1.1 and USB 2.0 devices to virtual machines.

    * USB over RDP 

    This is a combination of the RDP server and USB support allowing users to make USB devices available to virtual machines running remotely.

    * Serial ATA controller 

    Like a real SATA controller, VirtualBox&#8217;s virtual SATA controller operates faster and also consumes less CPU resources than the virtual IDE controller. Also, this allows you to connect more than three virtual hard disks to the machine.


[EDITO]:Tenim el fil doblat, ara ho he vist:
[http://ubuntuforums.org/showthread.php?t=1167726]("http://ubuntuforums.org/showthread.php?t=1167726")

---

### Post by prostata on 2009-05-26
ja ho tinc arreglat, aquesta es la sol-lució que he trobat per internet, està en castellá però la idea és el que val...gracies per les vostres aportacions i espero que pugui ser ùtil per algú altre...

Salutacions

------------------------------------------------------------------

En el Menu de Gnome>Sistema>Administracion>Usuarios y grupos, le damos a desbloquear y metemos la contraseña de root.  Clikamos en Gestionar grupos y buscamos “vboxusers“, le damos a propiedades y añadimos nuestro usuario tildando la opción.

---

### Post by SiscoGarcia on 2009-05-26
> **prostata said:**
> ja ho tinc arreglat, aquesta es la sol-lució que he trobat per internet,..

Que és el que t'havia explicat uidb4056 al comentari #6 d'aquest fil, no?

---

